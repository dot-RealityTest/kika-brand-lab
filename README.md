# 🎨 KIKA Brand Lab

> **Real-time brand design system playground** — Create, customize, and export complete brand identities with live preview, WCAG accessibility checking, and one-click export.

[![Live Site](https://img.shields.io/badge/Live-Site-0c8ce9?style=for-the-badge&logo=vercel)](https://brand.akakika.com)
[![License](https://img.shields.io/badge/License-MIT-green?style=for-the-badge)](LICENSE)
![React](https://img.shields.io/badge/React-19-61dafb?style=for-the-badge&logo=react)
![TypeScript](https://img.shields.io/badge/TypeScript-5-3178c6?style=for-the-badge&logo=typescript)
![Vite](https://img.shields.io/badge/Vite-7-646cff?style=for-the-badge&logo=vite)
![Tailwind](https://img.shields.io/badge/Tailwind-v4-38bdf8?style=for-the-badge&logo=tailwind-css)

---

## 🌐 **Live Demo**

### 👉 [**https://brand.akakika.com**](https://brand.akakika.com)

Try it now! Press **⌘K** for the command palette.

---

## ✨ Features

### 🎨 Design Tools
- **Real-time Brand Preview** — See your brand applied across mockups instantly
- **Color Palette Manager** — Create, edit, and reorder colors with drag-and-drop
- **WCAG Contrast Checker** — Ensure accessibility compliance (AA & AAA)
- **Typography System** — Choose from Google Fonts for heading, body, and mono
- **Logo & Icon Upload** — Upload and resize with pixel-perfect controls
- **Image Palette Extraction** — Auto-extract colors from any image

### ⌨️ Workflow
- **Command Palette (⌘K)** — Keyboard-driven workflow for all actions
- **Undo/Redo History** — Full timeline with visual state management
- **Dark/Light Mode** — Toggle between themes instantly
- **Inline Editing (⌘E)** — Edit mockup text directly on the page
- **Preset System** — Start from curated brand templates

### 📤 Export
- **DESIGN.md** — 9-section brand specification document
- **brand.css** — CSS custom properties (design tokens)
- **brand.json** — Complete brand state as JSON
- **Brand Boards** — Light and dark mode screenshots
- **One-click ZIP Export** — Everything in a single download

### 🖼️ Mockup Templates
- **Landing Page** — Modern SaaS/product landing page
- **Dashboard** — Admin/analytics dashboard UI
- **Portfolio** — Creative portfolio layout

---

## 🚀 Quick Start

### Local Development

```bash
# Clone the repository
git clone https://github.com/dot-RealityTest/kika-brand-lab.git
cd kika-brand-lab

# Install dependencies
pnpm install

# Start development server (port 3002)
pnpm dev
```

Open [http://localhost:3002](http://localhost:3002) in your browser.

### Build for Production

```bash
# Build optimized production bundle
pnpm build

# Preview production build
pnpm preview
```

---

## ⌨️ Keyboard Shortcuts

| Shortcut | Action |
|----------|--------|
| `⌘K` | Open/close command palette |
| `⌘E` | Toggle mockup edit mode |
| `⌘1` | Landing page template |
| `⌘2` | Dashboard template |
| `⌘3` | Portfolio template |
| `⌘Z` | Undo |
| `⌘⇧Z` | Redo |
| `Esc` | Close panel / close palette |

---

## 🏗️ Architecture

```
client/src/
├── App.tsx                      # Root app (ThemeProvider, Router, TooltipProvider)
├── pages/
│   └── Home.tsx                 # Main layout (brand preview + command palette)
├── contexts/
│   ├── BrandContext.tsx         # Brand state (colors, fonts, logos, undo/redo)
│   ├── ThemeContext.tsx         # Global dark/light theme toggle
│   ├── MockupTemplateContext.tsx # Selected mockup template
│   └── MockupContentContext.tsx # Editable mockup text, localStorage persistence
├── hooks/
│   ├── useThemeColors.ts        # Maps brand palette → CSS custom properties
│   ├── useComposition.ts        # IME composition awareness for CJK input
│   ├── useMobile.tsx            # Responsive breakpoint detection
│   └── usePersistFn.ts          # Persistent function reference hook
├── components/
│   ├── CommandPalette.tsx       # Keyboard-driven command palette (⌘K)
│   ├── BrandPreview.tsx         # Live brand preview with resizable logo
│   ├── BrandMockup.tsx          # Mockup templates (landing, dashboard, portfolio)
│   ├── ColorPaletteManager.tsx  # Color palette CRUD with drag-to-reorder
│   ├── ContrastChecker.tsx      # WCAG contrast ratio checker
│   ├── ExportPanel.tsx          # Export brand as ZIP
│   ├── ImagePaletteExtractor.tsx # Extract palette from uploaded images
│   └── ui/                      # shadcn/ui primitives
└── index.css                    # Tailwind v4 + CSS custom properties
```

---

## 🎯 Brand State

```typescript
interface BrandState {
  colors: ColorSwatch[];      // { id, hex, name }
  headingFont: string;        // Google Font name
  bodyFont: string;           // Google Font name
  monoFont: string;           // Google Font name
  brandName: string;
  tagline: string;
  logoUrl?: string;
  iconUrl?: string;
  logoSize?: number;          // px — resizable in edit mode
  iconSize?: number;          // px — resizable in edit mode
}
```

---

## 🛠️ Tech Stack

- **React 19** + **TypeScript 5**
- **Vite 7** (dev server + build)
- **Tailwind CSS v4** with `@theme inline`
- **Framer Motion** for animations
- **cmdk** for command palette
- **Radix UI** primitives
- **Wouter** for routing
- **JSZip** for export
- **html2canvas** for screenshots
- **Google Fonts API**

---

## 📤 Export Format

Export produces a ZIP file containing:

1. **DESIGN.md** — 9-section brand specification
   - Brand overview
   - Color palette
   - Typography
   - Logo usage
   - Icon usage
   - Voice & tone
   - Imagery style
   - Components
   - Dos and don'ts

2. **brand.css** — CSS custom properties
   ```css
   :root {
     --brand-color-1: #D9D9D9;
     --brand-color-2: #BFBFBF;
     --brand-heading-font: "Arial Black", sans-serif;
     --brand-body-font: "Fira Sans", system-ui;
   }
   ```

3. **brand.json** — Full brand state
4. **brand-board-light.png** — Light mode brand board
5. **brand-board-dark.png** — Dark mode brand board

---

## 🎨 Theming System

The UI reflects the brand palette through dynamic CSS custom properties:

### Light Mode
- Brand accent → `--primary`
- Lightest mid-color → `--card`
- Borders from `mix(bg, accent, ratio)`

### Dark Mode
- Inverted — darkest colors become surfaces
- `mix()` used for subtle elevation
- Avoids blinding-white backgrounds

### Key CSS Variables
```css
--primary, --primary-foreground
--background, --foreground
--card, --card-foreground
--popover, --popover-foreground
--border, --input
--muted, --muted-foreground
--accent, --accent-foreground
--destructive, --destructive-foreground
--ring
```

---

## 📝 Design Decisions

- **Dialog overlays** use `bg-foreground/50` so the overlay respects the theme
- **Mockup text** is editable inline only when edit mode is toggled (⌘E)
- **Logo/icon resizing** is drag-based on the right edge with pixel size preview
- **Dark mode cards** use `mix(bg, midColor, ratio)` to avoid white backgrounds
- **Accent backgrounds** use `mix(bg, accent, 0.15)` for better Tailwind compatibility

---

## 🚀 Deployment

### Vercel (Production)

The app is deployed on Vercel with automatic deployments:

```bash
# Deploy to production
vercel --prod
```

**Live URL:** https://brand.akakika.com

### Custom Domain

Configured with:
- Domain: `brand.akakika.com`
- DNS: Cloudflare (proxied)
- SSL: Automatic via Vercel

---

## 📄 License

MIT — open source. See [LICENSE](LICENSE).

---

## 👨‍💻 Author

**KIKA** ([@Kika_Loren](https://twitter.com/Kika_Loren))

- **Website:** https://akakika.com
- **GitHub:** https://github.com/dot-RealityTest
- **Telegram:** @Kika_Loren

---

## 🙏 Acknowledgments

- [shadcn/ui](https://ui.shadcn.com) — Beautiful UI components
- [cmdk](https://cmdk.paco.me) — Command palette
- [Vercel](https://vercel.com) — Hosting & deployment
- [Google Fonts](https://fonts.google.com) — Typography

---

## 📞 Support

For questions or issues:
- **GitHub Issues:** https://github.com/dot-RealityTest/kika-brand-lab/issues
- **Twitter:** [@Kika_Loren](https://twitter.com/Kika_Loren)
- **Email:** via https://akakika.com

---

**Built with ❄️ by KIKA**  
**Last Updated:** May 2, 2026

---

## 📖 About

**KIKA Brand Lab** is a real-time brand design system built for designers and developers who need to create professional brand identities quickly. Whether you're a freelancer, agency, or startup, you can create, customize, and export complete brand guidelines in minutes.

### Why Use KIKA Brand Lab?

- ⚡ **Fast** — Create a complete brand identity in under 30 minutes
- ♿ **Accessible** — Built-in WCAG contrast checking ensures your colors work for everyone
- 📤 **Export-Ready** — Get CSS, JSON, and DESIGN.md files ready for developers
- 🎨 **Visual** — See your brand applied to real mockups instantly
- ⌨️ **Efficient** — Command palette (⌘K) for keyboard-driven workflow
- 💰 **Free** — No signup, no paywall, no limits

### Built By

**KIKA** — Digital craft and macOS systems

- **Main Site:** https://akakika.com
- **Brand Lab:** https://brand.akakika.com
- **GitHub:** https://github.com/dot-RealityTest
- **Twitter:** [@Kika_Loren](https://twitter.com/Kika_Loren)
- **Telegram:** @Kika_Loren
