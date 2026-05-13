# Shadow Calculator — Color Math for Neumorphism

## The Formula

Given a base hex color, derive light and dark shadows:

```
light_shadow: hue stays same, saturation -5%, lightness +12%
dark_shadow:  hue stays same, saturation +5%, lightness -12%
```

Adjust the `±12` offset for stronger/subtler effects:
- `±8`  → very subtle (good for dark themes, dense UIs)
- `±12` → standard
- `±18` → dramatic (good for hero elements, large cards)

## Precomputed Palettes

| Base Color | Base Hex  | Light Shadow | Dark Shadow  | Good For           |
|------------|-----------|--------------|--------------|---------------------|
| Cool Gray  | `#e0e5ec` | `#ffffff`    | `#a3b1c6`    | Default, most apps  |
| Warm Gray  | `#ece9e4` | `#ffffff`    | `#b5afa8`    | Warm/cozy UIs       |
| Blue Tint  | `#d6e4f0` | `#f0f8ff`    | `#9bb8d4`    | Finance, health     |
| Lavender   | `#e8e5f0` | `#ffffff`    | `#b0aac4`    | Wellness, beauty    |
| Dark Slate | `#2d2d2d` | `#3d3d3d`    | `#1a1a1a`    | Dark mode           |
| Dark Navy  | `#1e2a3a` | `#283850`    | `#121a24`    | Dark premium        |
| Dark Green | `#1a2820` | `#243830`    | `#0e1814`    | Dark nature         |

## Tailwind Shadow String Template

```
`${spread}px ${spread}px ${blur}px ${darkShadow}, -${spread}px -${spread}px ${blur}px ${lightShadow}`
```

Standard values:
- `spread`: 6–10px
- `blur`: `spread * 2`

For pressed/inset, add `inset` at the start of both parts.

## JavaScript Color Utility

```ts
export function hexToRgb(hex: string): [number, number, number] {
  const r = parseInt(hex.slice(1, 3), 16);
  const g = parseInt(hex.slice(3, 5), 16);
  const b = parseInt(hex.slice(5, 7), 16);
  return [r, g, b];
}

export function rgbToHsl(r: number, g: number, b: number): [number, number, number] {
  r /= 255; g /= 255; b /= 255;
  const max = Math.max(r, g, b), min = Math.min(r, g, b);
  let h = 0, s = 0;
  const l = (max + min) / 2;
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

function hue2rgb(p: number, q: number, t: number) {
  if (t < 0) t += 1;
  if (t > 1) t -= 1;
  if (t < 1/6) return p + (q - p) * 6 * t;
  if (t < 1/2) return q;
  if (t < 2/3) return p + (q - p) * (2/3 - t) * 6;
  return p;
}

export function hslToHex(h: number, s: number, l: number): string {
  h /= 360; s /= 100; l /= 100;
  let r, g, b;
  if (s === 0) {
    r = g = b = l;
  } else {
    const q = l < 0.5 ? l * (1 + s) : l + s - l * s;
    const p = 2 * l - q;
    r = hue2rgb(p, q, h + 1/3);
    g = hue2rgb(p, q, h);
    b = hue2rgb(p, q, h - 1/3);
  }
  return '#' + [r, g, b].map(x => Math.round(x * 255).toString(16).padStart(2, '0')).join('');
}

export function neuPalette(baseHex: string, offset = 12) {
  const [r, g, b] = hexToRgb(baseHex);
  const [h, s, l] = rgbToHsl(r, g, b);
  return {
    base:  baseHex,
    light: hslToHex(h, Math.max(0, s - 5),  Math.min(100, l + offset)),
    dark:  hslToHex(h, Math.min(100, s + 5), Math.max(0, l - offset)),
  };
}
```
