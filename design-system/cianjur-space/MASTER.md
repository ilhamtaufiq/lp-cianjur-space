# Design System Master File

> **LOGIC:** When building a specific page, first check `design-system/pages/[page-name].md`.
> If that file exists, its rules **override** this Master file.
> If not, strictly follow the rules below.

---

**Project:** Cianjur Space
**Generated:** 2026-10-13 23:38:34
**Category:** SaaS (General)
**Design Dials:** Variance 4/10 (Balanced / Modern) | Motion 3/10 (Subtle) | Density 4/10 (Standard)

---

## Global Rules

### Color Palette

| Role | Hex | CSS Variable |
|------|-----|--------------|
| Background | `#0A0A0A` | `--color-background` |
| Surface | `#151515` | `--color-surface` |
| Muted (surface 2) | `#1C1C1C` | `--color-muted` |
| Foreground | `#F5F5F5` | `--color-foreground` |
| Muted Foreground | `#A3A3A3` | `--color-muted-foreground` |
| Border | `#262626` | `--color-border` |
| Border Strong | `#3A3A3A` | `--color-border-strong` |
| Primary (brand green) | `#00D40E` | `--color-primary` |
| Primary Strong (hover) | `#00B30C` | `--color-primary-strong` |
| On Primary | `#0A0A0A` | `--color-on-primary` |
| Secondary (green dark) | `#067A10` | `--color-secondary` |
| Accent / CTA | `#00D40E` | `--color-accent` |
| On Accent | `#0A0A0A` | `--color-on-accent` |
| Ink (headings) | `#F5F5F5` | `--color-ink` |
| Ring (focus) | `#00D40E` | `--color-ring` |
| Destructive | `#F87171` | `--color-destructive` |

**Color Notes:** Palet mengikuti brand Cendera (cendera.cianjur.space): tema gelap, `--brand-green: #00d40e`, `--brand-green-600: #00b30c`, `--brand-green-700: #067a10`, background `#0a0a0a`, surface `#151515`, border `#262626`, teks `#f5f5f5`, muted `#a3a3a3`. Kontras (WCAG): teks utama di background 18.2:1, teks muted 7.9:1, hijau di background 9.8:1, teks hitam di tombol hijau 9.8:1. Palet lama dari lambang kabupaten sudah tidak dipakai.

**Typography note:** palet ini tidak mengubah font. Judul dan body tetap Bricolage Grotesque dan Source Serif 4 (lihat bagian Typography).

### Typography

- **Heading Font:** Bricolage Grotesque (display, untuk judul, brand, dan tombol)
- **Body Font:** Source Serif 4 (serif, untuk teks panjang; line-height 1.7)
- **Mood:** editorial, lokal, jelas, tidak generik. Judul tegas, teks panjang mudah dibaca.
- **Catatan:** font dipilih sengaja, bukan default. Sebelumnya Plus Jakarta Sans dari rekomendasi awal; sudah diganti setelah review skill `frontend-design`.

**CSS Import:**
```css
@import url('https://fonts.googleapis.com/css2?family=Bricolage+Grotesque:opsz,wght@12..96,500..800&family=Source+Serif+4:opsz,wght@8..60,400..600&display=swap');
```

### Grid & Layout

- **Base unit:** 4px. Semua jarak memakai kelipatan 4 (lihat tabel spacing).
- **Grid:** 12 kolom untuk layout desktop. Lebar konten maksimum `1080px` (`--max-width`), padding horizontal `1.25rem`.
- **Breakpoint:** 860px untuk layout dua kolom ke satu kolom. Uji juga di 375px dan 1440px.
- **Gaya dasar:** dark-first, kontras tinggi, dan judul tegas. Dekorasi hanya jika membawa makna.
- **Referensi:** [v0-pixel-perfect](https://v0-pixel-perfect-seven.vercel.app/) dipakai sebagai acuan disiplin grid 4px, grid 12 kolom, dan dokumentasi token. Palet, sudut tajam, dan label huruf kapital dari referensi itu **tidak** dipakai karena palet resmi Cianjur Space mengikuti Cendera.

### Spacing Variables

*Density: 4/10 — Standard. Semua nilai kelipatan 4px.*

| Token | Value | Usage |
|-------|-------|-------|
| `--space-xs` | `4px` / `0.25rem` | Tight gaps |
| `--space-sm` | `8px` / `0.5rem` | Icon gaps, inline spacing |
| `--space-md` | `16px` / `1rem` | Standard padding |
| `--space-lg` | `24px` / `1.5rem` | Section padding |
| `--space-xl` | `32px` / `2rem` | Large gaps |
| `--space-2xl` | `48px` / `3rem` | Section margins |
| `--space-3xl` | `64px` / `4rem` | Hero padding |

### Shadow Depths

| Level | Value | Usage |
|-------|-------|-------|
| `--shadow-sm` | `0 1px 2px rgba(0,0,0,0.05)` | Subtle lift |
| `--shadow-md` | `0 4px 6px rgba(0,0,0,0.1)` | Cards, buttons |
| `--shadow-lg` | `0 10px 15px rgba(0,0,0,0.1)` | Modals, dropdowns |
| `--shadow-xl` | `0 20px 25px rgba(0,0,0,0.15)` | Hero images, featured cards |

---

## Component Specs

### Buttons

```css
/* Primary Button */
.btn-primary {
  background: #00D40E;
  color: #0A0A0A;
  padding: 12px 24px;
  border-radius: 8px;
  font-weight: 600;
  transition: all 200ms ease;
  cursor: pointer;
}

.btn-primary:hover {
  background: #00B30C;
}

/* Accent CTA (logo yellow, black outline) */
.btn-accent {
  background: #00D40E;
  color: #0A0A0A;
  border: 2px solid #00D40E;
  padding: 12px 24px;
  border-radius: 8px;
  font-weight: 700;
  transition: background-color 200ms ease;
  cursor: pointer;
}

.btn-accent:hover {
  background: #00B30C;
}

/* Secondary Button */
.btn-secondary {
  background: transparent;
  color: #00D40E;
  border: 2px solid #00D40E;
  padding: 12px 24px;
  border-radius: 8px;
  font-weight: 600;
  transition: all 200ms ease;
  cursor: pointer;
}
```

### Cards

```css
.card {
  background: #151515;
  border: 1px solid #262626;
  border-radius: 12px;
  padding: 24px;
  box-shadow: var(--shadow-md);
  transition: all 200ms ease;
  cursor: pointer;
}

.card:hover {
  box-shadow: var(--shadow-lg);
  transform: translateY(-2px);
}
```

### Inputs

```css
.input {
  padding: 12px 16px;
  border: 1px solid #262626;
  border-radius: 8px;
  font-size: 16px;
  transition: border-color 200ms ease;
}

.input:focus {
  border-color: #00D40E;
  outline: none;
  box-shadow: 0 0 0 3px #00D40E33;
}
```

### Modals

```css
.modal-overlay {
  background: rgba(0, 0, 0, 0.5);
  backdrop-filter: blur(4px);
}

.modal {
  background: white;
  border-radius: 16px;
  padding: 32px;
  box-shadow: var(--shadow-xl);
  max-width: 500px;
  width: 90%;
}
```

---

## Style Guidelines

**Style:** Glassmorphism

**Keywords:** Frosted glass, transparent, blurred background, layered, vibrant background, light source, depth, multi-layer

**Best For:** Modern SaaS, financial dashboards, high-end corporate, lifestyle apps, modal overlays, navigation

**Key Effects:** Backdrop blur (10-20px), subtle border (1px solid rgba white 0.2), light reflection, Z-depth

### Page Pattern

**Pattern Name:** Hero + Features + CTA

- **Conversion Strategy:** Deep CTA placement. For CTA label text, verify at least 4.5:1 against the button fill; use 7:1 only when the product explicitly targets AAA normal-text contrast. Keep focus and component boundaries independently visible. Disable hero parallax under reduced motion and render its static final state.
- **CTA Placement:** Hero (sticky) + Bottom
- **Section Order:** Hero with headline/image > Value prop > Key features (3-5) > CTA section > Footer

---

## Motion

**Scroll Reveal** (Subtle) — Trigger: scroll (viewport enter) | Duration: 300-400ms | Easing: `power1.out`

```js
gsap.from(el, { opacity: 0, y: 12, duration: 0.35, ease: 'power1.out', scrollTrigger: { trigger: el, start: 'top 90%', toggleActions: 'play none none reverse' } });
```

**Framework notes:** Requires the ScrollTrigger plugin registered once via gsap.registerPlugin(ScrollTrigger); Use matchMedia('(prefers-reduced-motion: reduce)') to skip non-essential motion and render the final state immediately

- ✅ Keep the y offset small (8-16px) so it reads as a fade, not a slide
- ❌ Don't reveal below-the-fold content needed for SEO/crawlers as invisible-by-default without a no-JS fallback
- ⚡ toggleActions 'play none none reverse' avoids re-triggering on every scroll direction change

---

## Anti-Patterns (Do NOT Use)

- ❌ Excessive animation
- ❌ Dark mode by default

### Additional Forbidden Patterns

- ❌ **Emojis as icons** — Use SVG icons (Heroicons, Lucide, Simple Icons)
- ❌ **Missing cursor:pointer** — All clickable elements must have cursor:pointer
- ❌ **Layout-shifting hovers** — Avoid scale transforms that shift layout
- ❌ **Low contrast text** — Maintain 4.5:1 minimum contrast ratio
- ❌ **Instant state changes** — Always use transitions (150-300ms)
- ❌ **Invisible focus states** — Focus states must be visible for a11y

---

## Pre-Delivery Checklist

Before delivering any UI code, verify:

- [ ] No emojis used as icons (use SVG instead)
- [ ] All icons from consistent icon set (Heroicons/Lucide)
- [ ] `cursor-pointer` on all clickable elements
- [ ] Hover states with smooth transitions (150-300ms)
- [ ] Light mode: text contrast 4.5:1 minimum
- [ ] Focus states visible for keyboard navigation
- [ ] `prefers-reduced-motion` respected
- [ ] Responsive: 375px, 768px, 1024px, 1440px
- [ ] No content hidden behind fixed navbars
- [ ] No horizontal scroll on mobile
