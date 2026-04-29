# Perfect Pixel Proxy — Portfolio Template

A sleek, AMOLED-dark personal portfolio built with **Vite + React + TypeScript + Tailwind CSS**. Features a live Discord presence card (via Lanyard API), animated constellation background, typewriter tagline, gradient buttons, and a custom glowing cursor.

---

## 🚀 Quick Start

```bash
npm install
npm run dev
```

Open the URL Vite prints (default: `http://localhost:8080`).

### Build for Production

```bash
npm run build     # outputs to dist/
npm run preview   # preview the production build locally
```

Deploy the `dist/` folder to any static host — Vercel, Netlify, Cloudflare Pages, GitHub Pages, etc.

---

## 📁 Project Structure

```
├── public/
│   ├── favicon.png                ← Site favicon (replace with your own)
│   └── robots.txt                 ← Search engine crawling rules
│
├── src/
│   ├── main.tsx                   ← App entry point (no edits needed)
│   ├── App.tsx                    ← React Router setup
│   ├── index.css                  ← All colors, gradients, animations, custom classes
│   │
│   ├── pages/
│   │   ├── Index.tsx              ← ⭐ Main page — all site content lives here
│   │   └── NotFound.tsx           ← 404 page
│   │
│   ├── components/
│   │   ├── Nav.tsx                ← Top navigation bar + brand name
│   │   ├── DiscordProfile.tsx     ← Live Discord avatar + status via Lanyard API
│   │   ├── Typewriter.tsx         ← Rotating tagline animation under hero name
│   │   ├── Constellation.tsx      ← Animated starfield background (canvas)
│   │   └── ui/
│   │       └── button.tsx         ← Reusable button component (shadcn/ui)
│   │
│   └── lib/
│       └── utils.ts               ← Tailwind `cn()` class merge utility
│
├── index.html                     ← Page title, meta tags, Google Fonts
├── tailwind.config.ts             ← Tailwind theme (colors, fonts, animations)
├── postcss.config.js              ← PostCSS plugins
├── vite.config.ts                 ← Vite dev server config
├── eslint.config.js               ← Linting rules
├── tsconfig.json                  ← TypeScript config
└── package.json                   ← Dependencies & scripts
```

---

## ✏️ Customization Guide

### 1. Site Metadata — `index.html`

| What to Change          | Where to Find It                                         |
| ----------------------- | -------------------------------------------------------- |
| **Browser tab title**   | `<title>Ayle - Portfolio</title>` (line 6)               |
| **SEO description**     | `<meta name="description" content="...">` (line 7)      |
| **Author name**         | `<meta name="author" content="Ayle">` (line 8)          |
| **Favicon**             | Replace `public/favicon.png` with your own image         |
| **Google Fonts**        | Edit the `<link href="https://fonts.googleapis.com/...">` URL (line 14) |

---

### 2. Brand Name — `src/components/Nav.tsx`

Change the brand text displayed in the floating navbar:

```tsx
// Line 15 — change "AYLE" to your name
<span className="tracking-widest">AYLE</span>
```

The **footer copyright** is at the bottom of `src/pages/Index.tsx`:

```tsx
// Line 278
<span>© {new Date().getFullYear()} AYLE · crafted in the dark</span>
```

---

### 3. Navigation Links — `src/components/Nav.tsx`

Edit the `links` array (line 4–9) to add, remove, or rename nav items:

```tsx
const links = [
  { href: "#about", label: "about" },
  { href: "#work", label: "work" },
  { href: "#stack", label: "stack" },
  { href: "#contact", label: "contact" },
];
```

The **availability badge** ("available" with green dot) is on line 26–32. Change the text or remove the `<div>` to hide it.

---

### 4. Hero Section — `src/pages/Index.tsx`

| What to Change                  | Where to Find It                                        |
| ------------------------------- | ------------------------------------------------------- |
| **Discord User ID**             | `const DISCORD_ID = "544047377540186114";` (line 18)    |
| **Big shimmering name**         | `<span className="text-shimmer">AYLE</span>` (line 83) |
| **Subtitle / description**      | `<p>` tag on lines 90–93                                |
| **CTA buttons**                 | "See selected work" & "Start a project" (lines 96–105) |

> **Note:** For the Discord avatar to load, the user with the configured ID must join the [Lanyard Discord server](https://discord.gg/lanyard). See Section 9 below.

---

### 5. Typewriter Tagline — `src/components/Typewriter.tsx`

Edit the `lines` array (line 3–7) to change the rotating phrases:

```tsx
const lines = [
  "I build websites, servers & resilient systems.",
  "I ship fast UIs and calm infrastructure.",
  "I design software that stays out of the way.",
];
```

Adjust typing speed on line 16: `del ? 30 : 55` (delete speed vs type speed in ms).  
Adjust pause between phrases on line 21: `1400` (ms before deleting starts).

---

### 6. About Section — `src/pages/Index.tsx`

**Bio text** — Edit the heading and paragraphs inside `id="about"` section (lines 124–137):

```tsx
<h2>Hey, I'm <span className="text-foreground">Alya</span>.</h2>
<p>I'm a graphic designer, web developer, and Discord bot builder...</p>
```

**Stats cards** — Edit the `stats` array (lines 53–58):

```tsx
const stats = [
  { value: "3.5+", label: "Years Exp." },
  { value: "20",   label: "Years Old" },
  { value: "10+",  label: "Projects" },
  { value: "30",   label: "Clients" },
];
```

---

### 7. Featured Work / Projects — `src/pages/Index.tsx`

Edit the `projects` array (lines 20–51). Each entry:

```tsx
{
  name: "inamusic",
  status: "live",              // "live" = green dot + accent border
  blurb: "Short description shown on the card.",
  stack: ["React", "Node", "Audio"],
  href: "https://inamusic.in", // link when clicked
  cta: "Visit Site",           // button label
  featured: true,              // true = highlighted accent border
}
```

Add, remove, or reorder entries freely — the responsive grid auto-updates.

---

### 8. Tech Stack — `src/pages/Index.tsx`

Edit the `stack` array (lines 60–67). Icons come from [lucide-react](https://lucide.dev/icons):

```tsx
import { Terminal, Boxes, Server, Cpu, Sparkles, Send } from "lucide-react";

const stack = [
  { icon: Terminal, label: "TypeScript", note: "daily driver" },
  { icon: Boxes,    label: "React / Next", note: "UI layer" },
  { icon: Server,   label: "Node · Go · Rust", note: "services" },
  { icon: Cpu,      label: "Postgres · Redis", note: "data" },
  { icon: Sparkles, label: "GLSL · Canvas", note: "motion" },
  { icon: Send,     label: "AWS · Fly · CF", note: "delivery" },
];
```

Browse all available icons at [lucide.dev/icons](https://lucide.dev/icons).

---

### 9. Contact Section — `src/pages/Index.tsx`

Inside the `id="contact"` section (lines 248–274):

| What to Change       | Where                                              |
| -------------------- | --------------------------------------------------- |
| **Headline**         | Lines 253–255                                       |
| **Description**      | Lines 256–260                                       |
| **Email address**    | `<a href="mailto:arcticayl@gmail.com">` (line 263)  |
| **GitHub link**      | `<a href="https://github.com/ayliee">` (line 268)  |

---

### 10. Discord Integration — `src/components/DiscordProfile.tsx`

This component fetches live Discord status via the **Lanyard API**.

**Setup:**
1. Join the [Lanyard Discord server](https://discord.gg/lanyard) with the account you want to track.
2. Set your Discord User ID in `src/pages/Index.tsx` line 18:
   ```tsx
   const DISCORD_ID = "YOUR_DISCORD_USER_ID";
   ```
3. The avatar, decoration, username, and online status will auto-populate.

**Polling interval:** Line 42 — `setInterval(load, 30_000)` refreshes every 30 seconds. Adjust as needed.

---

## 🎨 Theming & Colors

All visual tokens are **CSS custom properties** in `src/index.css` under `:root` (lines 6–52). Change them once and the entire site updates.

### Color Palette (HSL format)

```css
--background: 0 0% 0%;           /* AMOLED black */
--foreground: 270 20% 96%;       /* near-white text */
--card:       260 20% 4%;        /* card surfaces */
--accent:     260 85% 70%;       /* light purple — main accent */
--indigo:     240 80% 60%;       /* blue-ish accent */
--lilac:      275 90% 80%;       /* pink-ish accent */
--glow:       265 90% 72%;       /* glow/shadow tint */
--border:     260 25% 12%;       /* subtle borders */
--muted-foreground: 265 15% 65%; /* dimmed text */
```

### Gradients

| Variable             | Used For                                     |
| -------------------- | -------------------------------------------- |
| `--gradient-hero`    | Radial blobs behind the hero section         |
| `--gradient-text`    | White → lilac → indigo text gradient         |
| `--gradient-brand`   | Indigo → accent → lilac (brand gradient)     |
| `--shadow-glow`      | Purple glow shadow on elements               |
| `--shadow-card`      | Card drop shadow                             |

---

### Custom CSS Classes — `src/index.css`

| Class                  | Effect                                            |
| ---------------------- | ------------------------------------------------- |
| `.text-shimmer`        | White shimmer animation on the hero name          |
| `.text-gradient-brand` | Indigo → lilac gradient text                      |
| `.font-feminine`       | Italiana / Cormorant Garamond serif font          |
| `.btn-grad-border`     | Animated rainbow gradient border on buttons       |
| `.btn-glow`            | Hover glow effect for buttons                     |
| `.cursor-nav`          | Custom glowing-dot cursor on content sections     |
| `.terminal-chip`       | Monospace pill chip (used under hero)             |
| `.glass`               | Glassmorphism translucent surface                 |
| `.bg-hero`             | Applies the hero radial gradient background       |
| `.bg-brand`            | Applies the brand gradient as background          |
| `.scanline`            | Subtle CRT scanline overlay effect                |

---

### Fonts

Fonts are loaded from Google Fonts in `index.html` (line 14) and mapped in two places:

**`tailwind.config.ts`** (lines 11–14):
```ts
fontFamily: {
  sans: ['Inter', 'ui-sans-serif', 'system-ui'],           // body text
  mono: ['"JetBrains Mono"', 'ui-monospace', 'monospace'],  // code / labels
  display: ['"Space Grotesk"', 'Inter', 'sans-serif'],      // headings
}
```

**`src/index.css`** (line 88–92):
```css
.font-feminine {
  font-family: 'Italiana', 'Cormorant Garamond', serif;     /* hero name */
}
```

**To swap a font:**
1. Update the Google Fonts URL in `index.html`.
2. Update the corresponding `font-family` in `tailwind.config.ts` or `index.css`.

---

### Animations — `tailwind.config.ts`

Custom keyframes defined in the Tailwind config (lines 35–50):

| Animation        | Usage                                    |
| ---------------- | ---------------------------------------- |
| `fade-up`        | Hero section entrance                    |
| `pulse-glow`     | Green "available" dot, status indicators |
| `blink`          | Typewriter cursor                        |
| `float`          | Discord avatar floating up/down          |

Additional CSS animations in `src/index.css`:
- `shimmer` — name text shimmer sweep
- `grad-border` — animated gradient border rotation

---

## 🪐 Background & Cursor

### Constellation Background — `src/components/Constellation.tsx`

An animated canvas starfield with mouse-reactive particles.

| What to Tweak       | Where (line)     | Default                |
| -------------------- | --------------- | ---------------------- |
| Star density         | Line 32         | `width * height / 14000` |
| Min/Max star count   | Line 33         | `40` – `140`           |
| Drift speed          | Lines 36–37     | `0.25` max velocity    |
| Star size range      | Line 38         | `0.4` – `1.8` radius  |
| Star hue range       | Line 39         | `190` – `270` (cyan→purple) |
| Connection distance  | Line 85         | `130` pixels           |
| Mouse attraction radius | Line 68      | `150` pixels (22500 = 150²) |

### Custom Cursor — `src/index.css`

The `.cursor-nav` class (line 121–123) uses an inline SVG. To change colors, edit the URL-encoded gradient stops:
- `%23d8b4fe` → light purple
- `%23a78bfa` → medium purple  
- `%236366f1` → indigo

---

## ✅ Quick Customization Checklist

1. Replace `public/favicon.png` with your icon
2. Update `<title>` and `<meta description>` in `index.html`
3. Set your `DISCORD_ID` in `src/pages/Index.tsx` and [join Lanyard](https://discord.gg/lanyard)
4. Update your name in `src/components/Nav.tsx` and the footer in `src/pages/Index.tsx`
5. Edit the typewriter phrases in `src/components/Typewriter.tsx`
6. Update bio, `stats`, `projects`, `stack`, email, and GitHub link in `src/pages/Index.tsx`
7. Tweak colors in `:root` of `src/index.css`
8. Optionally swap fonts in `index.html` + `tailwind.config.ts`

---

## 📦 Tech Stack

- **[Vite](https://vitejs.dev/)** — Build tool & dev server
- **[React 18](https://react.dev/)** — UI framework
- **[TypeScript](https://www.typescriptlang.org/)** — Type safety
- **[Tailwind CSS 3](https://tailwindcss.com/)** — Utility-first styling
- **[React Router 6](https://reactrouter.com/)** — Client-side routing
- **[Lucide React](https://lucide.dev/)** — Icon library
- **[Lanyard API](https://github.com/Phineas/lanyard)** — Live Discord presence

---

Made with 💜
