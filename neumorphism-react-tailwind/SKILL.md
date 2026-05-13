---
name: neumorphism-react-tailwind
description: >
  Apply neumorphism (soft UI) design effects to React + TypeScript components using
  TailwindCSS v4. Use this skill whenever the user mentions "neumorfismo", "neumorphism",
  "soft UI", "sombra suave", "efeito de relevo", "extruded UI", or asks to make
  components look "raised", "pressed", "inset", or "soft-shadow". Also trigger when
  the user asks to style cards, buttons, inputs, toggles, sliders, or dashboards with
  a soft/clay-like look, OR when they share a component and want it to look more tactile
  or 3D. Always trigger for any React + Tailwind v4 project that mentions neumorphism or
  soft UI, even if the user just says "quero deixar mais bonito com aquele efeito de
  relevo". This skill assumes Tailwind v4 (CSS-first, no tailwind.config file).
---

# Neumorphism for React + TypeScript + TailwindCSS v4

Neumorphism (soft UI) creates the illusion of extruded or inset elements via
dual `box-shadow` — one light (top-left), one dark (bottom-right) — on a surface
whose color exactly matches its container. This skill is fully compatible with
**Tailwind v4's CSS-first configuration** (`@theme`, `@utility`, `@custom-variant`)
— there is no `tailwind.config.js`.

---

## Core Concept

Three colors are required:
- **Base** — shared by container and element (they must match exactly)
- **Light shadow** — ~12–15% lighter (top-left highlight)
- **Dark shadow** — ~12–15% darker (bottom-right shadow)

If the element and its container have different backgrounds, the illusion breaks.

---

## 1. CSS Setup — `globals.css`

In Tailwind v4, all customization lives in CSS via `@theme` and `@utility`.
Add this to your main CSS file (e.g. `src/app/globals.css` or `src/index.css`):

```css
@import "tailwindcss";

/* ─── Neumorphism Design Tokens ─── */
@theme {
  /* Base palette — light theme */
  --color-neu-base:   #e0e5ec;
  --color-neu-light:  #ffffff;
  --color-neu-dark:   #a3b1c6;
  --color-neu-text:   #4a5568;
  --color-neu-accent: #6c63ff;

  /* Shadow tokens — referenced by @utility below */
  --shadow-neu-raised:  8px 8px 16px var(--color-neu-dark), -8px -8px 16px var(--color-neu-light);
  --shadow-neu-pressed: inset 6px 6px 12px var(--color-neu-dark), inset -6px -6px 12px var(--color-neu-light);
  --shadow-neu-flat:    4px 4px 8px var(--color-neu-dark), -4px -4px 8px var(--color-neu-light);
  --shadow-neu-convex:
    8px 8px 16px var(--color-neu-dark), -8px -8px 16px var(--color-neu-light),
    inset 1px 1px 2px var(--color-neu-light), inset -1px -1px 2px var(--color-neu-dark);
}

/* ─── Dark mode overrides ─── */
.dark {
  --color-neu-base:   #2d2d2d;
  --color-neu-light:  #3d3d3d;
  --color-neu-dark:   #1a1a1a;
  --color-neu-text:   #e2e8f0;
  --color-neu-accent: #818cf8;
}

/* ─── Utility classes via @utility ─── */
@utility neu-raised  { box-shadow: var(--shadow-neu-raised);  }
@utility neu-pressed { box-shadow: var(--shadow-neu-pressed); }
@utility neu-flat    { box-shadow: var(--shadow-neu-flat);    }
@utility neu-convex  { box-shadow: var(--shadow-neu-convex);  }

/* ─── Surface shorthand ─── */
@utility neu-surface {
  background-color: var(--color-neu-base);
  color: var(--color-neu-text);
}

/* ─── High-contrast fallback ─── */
@media (forced-colors: active) {
  .neu-raised, .neu-flat, .neu-convex { outline: 2px solid ButtonText; }
  .neu-pressed { outline: 2px inset ButtonText; }
}
```

> **How `@theme` works in v4:** variables declared inside `@theme` are automatically
> exposed as Tailwind utilities. `--color-neu-base` becomes `bg-neu-base`,
> `text-neu-base`, etc. Shadow tokens declared via `--shadow-*` inside `@theme` also
> become `shadow-neu-*` utilities automatically in v4.

---

## 2. TypeScript Types — `types/neu.ts`

```ts
// src/types/neu.ts

export type NeuVariant = 'raised' | 'pressed' | 'flat' | 'convex';

export const neuVariantClass: Record<NeuVariant, string> = {
  raised:  'neu-raised',
  pressed: 'neu-pressed',
  flat:    'neu-flat',
  convex:  'neu-convex',
} as const;
```

---

## 3. React Component Library

All components use:
- `bg-neu-base` — from the `@theme` `--color-neu-base` token
- `neu-raised` / `neu-pressed` / etc. — from the `@utility` definitions above
- `text-neu-text`, `text-neu-accent` — from `@theme` color tokens

### NeuCard

```tsx
// src/components/neu/NeuCard.tsx
import { cn } from '@/lib/utils';
import { neuVariantClass, type NeuVariant } from '@/types/neu';

interface NeuCardProps extends React.HTMLAttributes<HTMLDivElement> {
  variant?: NeuVariant;
  rounded?: string;
}

export function NeuCard({
  children,
  variant = 'raised',
  rounded = 'rounded-2xl',
  className,
  ...props
}: NeuCardProps) {
  return (
    <div
      className={cn('neu-surface p-6', rounded, neuVariantClass[variant], className)}
      {...props}
    >
      {children}
    </div>
  );
}
```

### NeuButton

```tsx
// src/components/neu/NeuButton.tsx
import { cn } from '@/lib/utils';
import { useState } from 'react';

type NeuButtonVariant = 'default' | 'icon';

interface NeuButtonProps extends React.ButtonHTMLAttributes<HTMLButtonElement> {
  variant?: NeuButtonVariant;
}

export function NeuButton({
  children,
  className,
  variant = 'default',
  disabled,
  ...props
}: NeuButtonProps) {
  const [pressed, setPressed] = useState(false);

  return (
    <button
      className={cn(
        'neu-surface select-none transition-shadow duration-150 font-medium cursor-pointer',
        'rounded-xl px-6 py-3',
        pressed || disabled ? 'neu-pressed' : 'neu-raised',
        'hover:brightness-105',
        'focus:outline-none focus-visible:ring-2 focus-visible:ring-neu-accent',
        'disabled:opacity-50 disabled:cursor-not-allowed',
        variant === 'icon' && 'p-4 rounded-2xl',
        className
      )}
      disabled={disabled}
      onMouseDown={() => setPressed(true)}
      onMouseUp={() => setPressed(false)}
      onMouseLeave={() => setPressed(false)}
      {...props}
    >
      {children}
    </button>
  );
}
```

### NeuInput

```tsx
// src/components/neu/NeuInput.tsx
import { cn } from '@/lib/utils';

interface NeuInputProps extends React.InputHTMLAttributes<HTMLInputElement> {
  label?: string;
  error?: string;
}

export function NeuInput({ label, error, className, id, ...props }: NeuInputProps) {
  return (
    <div className="flex flex-col gap-1.5">
      {label && (
        <label htmlFor={id} className="text-sm font-medium text-neu-text/70">
          {label}
        </label>
      )}
      <input
        id={id}
        aria-invalid={!!error}
        className={cn(
          'neu-surface neu-pressed rounded-xl px-4 py-3 w-full',
          'placeholder:text-neu-text/40 border-none outline-none',
          'focus:ring-2 focus:ring-neu-accent/40 transition-shadow',
          error && 'ring-2 ring-red-400',
          className
        )}
        {...props}
      />
      {error && (
        <p role="alert" className="text-xs text-red-500">{error}</p>
      )}
    </div>
  );
}
```

### NeuToggle

```tsx
// src/components/neu/NeuToggle.tsx
import { cn } from '@/lib/utils';
import { useState } from 'react';

interface NeuToggleProps {
  defaultChecked?: boolean;
  checked?: boolean;
  onChange?: (checked: boolean) => void;
  label?: string;
  id?: string;
}

export function NeuToggle({
  defaultChecked = false,
  checked,
  onChange,
  label,
  id,
}: NeuToggleProps) {
  const [internalOn, setInternalOn] = useState(defaultChecked);
  const isControlled = checked !== undefined;
  const on = isControlled ? checked : internalOn;

  const toggle = () => {
    if (!isControlled) setInternalOn((prev) => !prev);
    onChange?.(!on);
  };

  return (
    <div className="flex items-center gap-3">
      <button
        id={id}
        role="switch"
        aria-checked={on}
        onClick={toggle}
        className={cn(
          'relative w-14 h-7 rounded-full transition-all duration-300',
          'neu-surface neu-pressed',
          'focus:outline-none focus-visible:ring-2 focus-visible:ring-neu-accent'
        )}
      >
        <span
          className={cn(
            'absolute top-1 w-5 h-5 rounded-full transition-all duration-300 neu-raised',
            on ? 'left-8 bg-neu-accent' : 'left-1 bg-neu-base'
          )}
        />
      </button>
      {label && (
        <label htmlFor={id} className="text-sm text-neu-text cursor-pointer">
          {label}
        </label>
      )}
    </div>
  );
}
```

### NeuSlider

```tsx
// src/components/neu/NeuSlider.tsx
import { cn } from '@/lib/utils';

interface NeuSliderProps extends React.InputHTMLAttributes<HTMLInputElement> {
  label?: string;
}

export function NeuSlider({ label, className, id, ...props }: NeuSliderProps) {
  return (
    <div className="flex flex-col gap-2">
      {label && (
        <label htmlFor={id} className="text-sm font-medium text-neu-text/70">
          {label}
        </label>
      )}
      <div className="rounded-full neu-pressed neu-surface px-2 py-3">
        <input
          id={id}
          type="range"
          className={cn(
            'w-full appearance-none bg-transparent cursor-pointer',
            '[&::-webkit-slider-thumb]:appearance-none',
            '[&::-webkit-slider-thumb]:w-5 [&::-webkit-slider-thumb]:h-5',
            '[&::-webkit-slider-thumb]:rounded-full',
            '[&::-webkit-slider-thumb]:bg-neu-base',
            '[&::-webkit-slider-thumb]:[box-shadow:var(--shadow-neu-raised)]',
            '[&::-webkit-slider-runnable-track]:h-1',
            '[&::-webkit-slider-runnable-track]:rounded-full',
            '[&::-webkit-slider-runnable-track]:bg-neu-dark/20',
            className
          )}
          {...props}
        />
      </div>
    </div>
  );
}
```

---

## 4. Barrel Export — `components/neu/index.ts`

```ts
// src/components/neu/index.ts
export { NeuCard }   from './NeuCard';
export { NeuButton } from './NeuButton';
export { NeuInput }  from './NeuInput';
export { NeuToggle } from './NeuToggle';
export { NeuSlider } from './NeuSlider';
export type { NeuVariant } from '@/types/neu';
```

---

## 5. Applying to Existing Components

| Before (generic Tailwind v4)              | After (neumorphic)                         |
|-------------------------------------------|--------------------------------------------|
| `shadow-md bg-white`                      | `neu-raised bg-neu-base`                   |
| `shadow-inner bg-gray-100`                | `neu-pressed bg-neu-base`                  |
| `border border-gray-200 bg-white`         | `neu-flat bg-neu-base` (remove border)     |
| `rounded bg-gray-100`                     | `neu-flat bg-neu-base rounded-2xl`         |

**Container rule:** the parent wrapping neumorphic elements must also use `bg-neu-base`.
A `bg-white` or `bg-gray-100` parent will break the illusion.

---

## 6. Custom Color Palette — `utils/neuColors.ts`

Use this when the user provides a non-default base color:

```ts
// src/utils/neuColors.ts

function hexToHsl(hex: string): [number, number, number] {
  const r = parseInt(hex.slice(1, 3), 16) / 255;
  const g = parseInt(hex.slice(3, 5), 16) / 255;
  const b = parseInt(hex.slice(5, 7), 16) / 255;
  const max = Math.max(r, g, b), min = Math.min(r, g, b);
  const l = (max + min) / 2;
  let h = 0, s = 0;
  if (max !== min) {
    const d = max - min;
    s = l > 0.5 ? d / (2 - max - min) : d / (max + min);
    switch (max) {
      case r: h = ((g - b) / d + (g < b ? 6 : 0)) / 6; break;
      case g: h = ((b - r) / d + 2) / 6; break;
      case b: h = ((r - g) / d + 4) / 6; break;
    }
  }
  return [Math.round(h * 360), Math.round(s * 100), Math.round(l * 100)];
}

function hue2rgb(p: number, q: number, t: number): number {
  if (t < 0) t += 1;
  if (t > 1) t -= 1;
  if (t < 1 / 6) return p + (q - p) * 6 * t;
  if (t < 1 / 2) return q;
  if (t < 2 / 3) return p + (q - p) * (2 / 3 - t) * 6;
  return p;
}

function hslToHex(h: number, s: number, l: number): string {
  h /= 360; s /= 100; l /= 100;
  let r: number, g: number, b: number;
  if (s === 0) {
    r = g = b = l;
  } else {
    const q = l < 0.5 ? l * (1 + s) : l + s - l * s;
    const p = 2 * l - q;
    r = hue2rgb(p, q, h + 1 / 3);
    g = hue2rgb(p, q, h);
    b = hue2rgb(p, q, h - 1 / 3);
  }
  return '#' + [r, g, b]
    .map((x) => Math.round(x * 255).toString(16).padStart(2, '0'))
    .join('');
}

export interface NeuPalette {
  base: string;
  light: string;
  dark: string;
}

export function neuPalette(baseHex: string, offset = 12): NeuPalette {
  const [h, s, l] = hexToHsl(baseHex);
  return {
    base:  baseHex,
    light: hslToHex(h, Math.max(0, s - 5),  Math.min(100, l + offset)),
    dark:  hslToHex(h, Math.min(100, s + 5), Math.max(0,   l - offset)),
  };
}

/**
 * Generates the @theme snippet to paste into globals.css.
 * Usage: console.log(neuCssTokens('#d4e9ff'))
 */
export function neuCssTokens(baseHex: string, offset = 12): string {
  const { base, light, dark } = neuPalette(baseHex, offset);
  return [
    `--color-neu-base:  ${base};`,
    `--color-neu-light: ${light};`,
    `--color-neu-dark:  ${dark};`,
  ].join('\n  ');
}
```

When the user provides a custom color, run `neuCssTokens('#yourcolor')` and paste
the result into the `@theme` block in `globals.css` replacing the three color lines.

---

## 7. Accessibility Checklist

- [ ] Text contrast ≥ 4.5:1 (WCAG AA) — `text-neu-text` (#4a5568) on `bg-neu-base` (#e0e5ec) passes
- [ ] All interactive elements have `focus-visible:ring-2 focus-visible:ring-neu-accent`
- [ ] Don't use shadow alone for error/disabled states — pair with color or text cues
- [ ] `aria-checked` on toggles, `aria-invalid` on inputs with errors
- [ ] `forced-colors` fallback is included in `globals.css` (see Section 1)

---

## 8. Performance Notes

- Use `transition-shadow` not `transition-all` on interactive elements — cheaper repaint
- Use `neu-flat` (smaller offsets) for lists with 20+ items
- Avoid `box-shadow` on GPU-composited layers (`will-change: transform`)
- Add `will-change: box-shadow` only on buttons/toggles, not static cards

---

## Quick Reference

| Utility class | Effect   | Use case                        |
|---------------|----------|---------------------------------|
| `neu-raised`  | Extruded | Cards, panels, icon buttons     |
| `neu-pressed` | Inset    | Inputs, active state, track     |
| `neu-flat`    | Subtle   | List items, secondary surfaces  |
| `neu-convex`  | Bulging  | Knobs, badges, pill labels      |

All utilities defined in `globals.css` via `@utility` — no config file needed.

See `references/shadow-calculator.md` for color math and precomputed palettes.
See `references/patterns.md` for full patterns: login form, settings page, music player, dashboard.
