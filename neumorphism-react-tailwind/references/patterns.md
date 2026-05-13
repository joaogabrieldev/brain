# Neumorphism Patterns — Complete UI Templates

## Pattern 1: Login / Auth Form

```tsx
export function NeuLoginForm() {
  return (
    <div className="min-h-screen bg-neu-light-base flex items-center justify-center p-8">
      <NeuCard variant="raised" className="w-96 flex flex-col gap-6">
        {/* Logo area */}
        <NeuCard variant="convex" rounded="rounded-2xl" className="w-16 h-16 flex items-center justify-center mx-auto">
          <span className="text-2xl">🔐</span>
        </NeuCard>

        <div className="text-center">
          <h1 className="text-xl font-semibold text-neu-text">Welcome back</h1>
          <p className="text-sm text-neu-text/50 mt-1">Sign in to continue</p>
        </div>

        <NeuInput label="Email" type="email" placeholder="you@example.com" />
        <NeuInput label="Password" type="password" placeholder="••••••••" />

        <NeuButton className="w-full justify-center">
          Sign In
        </NeuButton>

        <p className="text-center text-sm text-neu-text/40">
          No account? <a href="#" className="text-neu-accent">Sign up</a>
        </p>
      </NeuCard>
    </div>
  );
}
```

## Pattern 2: Settings Panel

```tsx
export function NeuSettings() {
  return (
    <div className="bg-neu-light-base min-h-screen p-8">
      <NeuCard variant="raised" className="max-w-md mx-auto flex flex-col gap-4">
        <h2 className="text-lg font-semibold text-neu-text">Settings</h2>

        {['Notifications', 'Dark Mode', 'Auto-sync', 'Analytics'].map((label) => (
          <NeuCard key={label} variant="flat" rounded="rounded-xl" className="flex items-center justify-between py-3 px-4">
            <span className="text-sm text-neu-text">{label}</span>
            <NeuToggle />
          </NeuCard>
        ))}

        <NeuSlider label="Volume" min={0} max={100} defaultValue={70} />
        <NeuSlider label="Brightness" min={0} max={100} defaultValue={80} />
      </NeuCard>
    </div>
  );
}
```

## Pattern 3: Music Player Widget

```tsx
export function NeuMusicPlayer() {
  return (
    <div className="bg-neu-light-base flex items-center justify-center min-h-screen p-8">
      <NeuCard variant="raised" className="w-72 flex flex-col items-center gap-6">
        {/* Album art */}
        <NeuCard variant="convex" rounded="rounded-3xl" className="w-48 h-48 flex items-center justify-center">
          <span className="text-5xl">🎵</span>
        </NeuCard>

        <div className="text-center">
          <p className="font-semibold text-neu-text">Track Name</p>
          <p className="text-sm text-neu-text/50">Artist Name</p>
        </div>

        <NeuSlider className="w-full" min={0} max={100} defaultValue={40} />

        <div className="flex gap-4">
          <NeuButton variant="icon">⏮</NeuButton>
          <NeuButton variant="icon" className="text-neu-accent">▶</NeuButton>
          <NeuButton variant="icon">⏭</NeuButton>
        </div>
      </NeuCard>
    </div>
  );
}
```

## Pattern 4: Stat/Metric Cards

```tsx
function NeuStatCard({ label, value, delta }: { label: string; value: string; delta: string }) {
  return (
    <NeuCard variant="raised" className="flex flex-col gap-2">
      <NeuCard variant="pressed" rounded="rounded-xl" className="p-3">
        <p className="text-xs text-neu-text/50 uppercase tracking-wider">{label}</p>
        <p className="text-2xl font-bold text-neu-text">{value}</p>
      </NeuCard>
      <p className="text-sm text-green-500 px-1">{delta}</p>
    </NeuCard>
  );
}

export function NeuDashboard() {
  return (
    <div className="bg-neu-light-base min-h-screen p-8">
      <div className="grid grid-cols-2 md:grid-cols-4 gap-4 max-w-4xl mx-auto">
        <NeuStatCard label="Revenue"   value="$12.4k" delta="+8.2%" />
        <NeuStatCard label="Users"     value="3,210"  delta="+4.1%" />
        <NeuStatCard label="Sessions"  value="18,900" delta="+2.7%" />
        <NeuStatCard label="Bounce"    value="34.2%"  delta="-1.3%" />
      </div>
    </div>
  );
}
```

## Converting a Generic Tailwind Component

Before:
```tsx
<div className="bg-white shadow-md rounded-lg p-6 border border-gray-200">
  <input className="border border-gray-300 rounded px-3 py-2 w-full" />
  <button className="bg-blue-500 text-white px-4 py-2 rounded mt-4">Submit</button>
</div>
```

After:
```tsx
<div className="bg-neu-light-base shadow-neu-raised rounded-2xl p-6">
  <input className="bg-neu-light-base shadow-neu-pressed rounded-xl px-3 py-2 w-full text-neu-text border-none outline-none focus:ring-2 focus:ring-neu-accent/40" />
  <NeuButton className="mt-4 w-full justify-center">Submit</NeuButton>
</div>
```

Key changes:
1. Replace `bg-white` / `bg-gray-*` with `bg-neu-light-base`
2. Replace `shadow-md` with `shadow-neu-raised`
3. Replace `border border-gray-*` with nothing (no borders in neumorphism)
4. Replace `shadow-inner` / inset elements with `shadow-neu-pressed`
5. Remove all `border` classes from inputs
