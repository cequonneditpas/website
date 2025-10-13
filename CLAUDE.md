# Ce qu'on ne dit pas - Project Documentation

## 📋 Project Overview

**Ce qu'on ne dit pas** is a single-page website for a French podcast focused on intimate stories of violence (committed and suffered). The site serves as a landing page to collect testimonies and share the podcast's mission.

- **Live Site**: https://cequonneditpas.fr/
- **Language**: French (fr-FR)
- **Type**: Single-page application (SPA)
- **Framework**: Vanilla HTML/CSS/JS (no framework)

## 🛠 Tech Stack

### Core Technologies
- **HTML5**: Semantic markup with accessibility features
- **Tailwind CSS 4.x**: Utility-first CSS framework
- **JavaScript (ES6+)**: Vanilla JS for interactions
- **Bun**: JavaScript runtime and package manager

### External Dependencies
- **Lucide Icons** (latest): Icon library via CDN
- **Google Fonts**: Playfair Display (display) + Inter (body)
- **Plausible Analytics**: Privacy-friendly analytics

### Build Tools
- **Tailwind CLI** (`@tailwindcss/cli`): CSS compilation
- **Bun**: Package management and development server

## 📁 Project Structure

```
cequonneditpas/
├── index.html          # Main HTML file (single-page app)
├── input.css           # Tailwind source CSS
├── output.css          # Compiled Tailwind CSS (generated)
├── robots.txt          # Search engine directives
├── sitemap.xml         # Site map for SEO
├── public/
│   ├── logo.png        # Main logo (512x512)
│   ├── favicon-*.png   # Favicons
│   └── social-banner.png # OG image for social sharing
├── package.json        # Dependencies and scripts
└── bun.lock           # Lockfile
```

## 🎨 Design System

### Typography
- **Display Font**: Playfair Display (serif) - Used for headings
- **Body Font**: Inter (sans-serif) - Used for body text
- **Font Classes**:
  - `.font-display` → Playfair Display
  - `.font-body` → Inter

### Color Palette
- **Primary**: Purple gradient (`from-purple-400/600 to-pink-400/600`)
- **Background**: Dark gradient (`from-gray-900 to-gray-800`)
- **Text**:
  - Primary: `text-gray-100`
  - Secondary: `text-gray-300`
  - Muted: `text-gray-400/500`
- **Accent**: Purple (`purple-400/600`) and Pink (`pink-400/600`)

### Spacing Scale
- Mobile-first responsive spacing using Tailwind's scale
- Sections: `py-12 sm:py-16 md:py-20`
- Containers: `max-w-4xl` or `max-w-5xl` or `max-w-7xl`

## 🧩 Key Components

### 1. Navigation
- **Type**: Fixed top navigation with backdrop blur
- **Features**:
  - Desktop horizontal menu
  - Mobile hamburger menu
  - Scroll spy (highlights active section)
  - Smooth scroll to sections
- **Location**: Lines 204-315

### 2. Hero Section
- **Features**:
  - Large logo with rounded corners
  - Gradient text heading
  - CTA button with smooth hover effect
- **Location**: Lines 318-350

### 3. Conviction Cards
- **Pattern**: 3-column grid with icons
- **Icons**: Lucide icons (sprout, headphones, handshake)
- **Hover**: Shadow lift effect
- **Location**: Lines 478-537

### 4. Testimonial Quotes
- **Pattern**: Stacked cards with author attribution
- **Styling**: Purple/pink accent colors per speaker
- **Location**: Lines 540-639

### 5. FAQ Section
- **Pattern**: Expandable question cards
- **Icons**: Lucide icons for each section
- **Location**: Lines 762-899

### 6. CTA Section
- **Pattern**: Gradient background card
- **Button**: White button with hover state
- **Location**: Lines 1047-1097

### 7. Footer
- **Pattern**: 2-column layout (logo + social links)
- **Features**: Social media icons, email link, copyright
- **Location**: Lines 1100-1238

## 🎯 Interactive Features

### Smooth Scrolling
- **File**: index.html (lines 1242-1276)
- **Behavior**: Smooth scroll to sections on nav click
- **Offset**: Accounts for 64px fixed navbar

### Scroll Spy
- **File**: index.html (lines 1278-1312)
- **Behavior**: Highlights active section in navigation
- **Trigger**: Updates on scroll with 100px offset

### Button Hover Effects
- **Pattern**: Layered gradient with opacity transition
- **Classes**:
  ```html
  <a class="group relative ... overflow-hidden">
    <span class="absolute inset-0 bg-gradient-to-r ... opacity-0 group-hover:opacity-100 transition-opacity duration-500"></span>
    <span class="relative">Button Text</span>
  </a>
  ```

### Mobile Menu Toggle
- **File**: index.html (line 259)
- **Behavior**: Toggle `.hidden` class on click
- **Auto-close**: Closes on navigation link click

## 🔍 SEO Optimization

### Structured Data (JSON-LD)
Three schema types implemented (lines 108-198):

1. **WebSite Schema**: Organization details, logo, contact info
2. **PodcastSeries Schema**: Podcast metadata
3. **FAQPage Schema**: FAQ section for rich snippets

### Meta Tags
- **Basic**: Title, description, keywords, author
- **Geo/Language**: `geo.region="FR"`, `hreflang="fr"`
- **Robots**: `index, follow` with rich media settings
- **Open Graph**: Full OG tags for social sharing
- **Twitter Cards**: Summary large image card

### Performance
- **Resource Hints**:
  - `preconnect` for Google Fonts
  - `dns-prefetch` for Plausible & Lucide
- **Image Optimization**:
  - Width/height attributes (prevents CLS)
  - `loading="lazy"` on footer logo
- **Canonical URL**: `https://cequonneditpas.fr/`

## 📱 Responsive Breakpoints

Tailwind's default breakpoints:
- **sm**: 640px (tablet portrait)
- **md**: 768px (tablet landscape)
- **lg**: 1024px (desktop)
- **xl**: 1280px (large desktop)

### Common Patterns
```html
<!-- Text sizing -->
text-xl sm:text-2xl md:text-3xl lg:text-4xl

<!-- Spacing -->
py-12 sm:py-16 md:py-20

<!-- Grid layouts -->
grid-cols-1 sm:grid-cols-2 lg:grid-cols-3
```

## 🚀 Development

### Setup
```bash
# Install dependencies
bun install

# Start Tailwind watcher
bun run build

# Serve locally (if needed)
bun run start
```

### Scripts
- `bun run build`: Compile Tailwind CSS with watch mode
- `bun run start`: Open index.html in browser

### CSS Compilation
- **Input**: `input.css` (Tailwind directives)
- **Output**: `output.css` (compiled CSS)
- **Command**: `bunx @tailwindcss/cli -i ./input.css -o ./output.css --watch --minify`

## 🎨 Custom Styles

### Gradient Text
```html
<h1 class="bg-gradient-to-r from-purple-400 to-pink-400 bg-clip-text text-transparent">
  Gradient Heading
</h1>
```

### Backdrop Blur
```html
<nav class="bg-gray-900 bg-opacity-95 backdrop-blur-md">
  <!-- Content -->
</nav>
```

### Custom Hover Effects
All buttons use the layered gradient pattern:
1. Base gradient background
2. Absolute overlay with darker gradient
3. Opacity transition on hover (0 → 100%)
4. Text wrapped in relative positioned span

## 🔧 Common Tasks

### Adding a New Section
1. Add section HTML with unique `id` attribute
2. Add navigation link with matching `href="#id"`
3. Add `data-section="id"` to nav link for scroll spy
4. Ensure section has `py-12 sm:py-16 md:py-20` spacing

### Updating Icons
Icons use Lucide with `data-lucide` attribute:
```html
<i data-lucide="icon-name" class="w-5 h-5"></i>
```
- Icons initialize on page load (line 1315)
- See [Lucide docs](https://lucide.dev) for available icons

### Modifying Colors
1. Update gradient colors in HTML classes
2. Common gradients:
   - Purple-Pink: `from-purple-600 to-pink-600`
   - Purple-Pink Light: `from-purple-400 to-pink-400`
   - Dark BG: `from-purple-900/10 to-pink-900/10`

### Adding Social Links
1. Add link in header social banner (line 361)
2. Add matching link in footer (line 1139)
3. Include SVG icon and label

## 📊 Analytics

**Plausible Analytics** is installed with custom event tracking:
- **Script**: Loaded in `<head>` (lines 99-103)
- **Domain**: Configured for `cequonneditpas.fr`
- **Privacy**: GDPR-compliant, no cookies

## ♿ Accessibility

### Features
- Semantic HTML5 elements (`<header>`, `<nav>`, `<section>`, `<footer>`)
- ARIA labels on interactive elements
- Proper heading hierarchy (h1 → h2 → h3)
- Alt text on all images
- Focus states on interactive elements
- Keyboard navigation support

### Testing Checklist
- [ ] Test with screen reader
- [ ] Verify keyboard navigation
- [ ] Check color contrast ratios
- [ ] Test with reduced motion preferences

## 🐛 Known Issues / Considerations

1. **Lucide Icons**: Using `@latest` - consider pinning to specific version for production
2. **Single HTML File**: All content in one file - consider splitting if site grows
3. **No Build Process**: No minification/bundling - consider adding for production
4. **Static Content**: All content hardcoded - consider CMS if frequent updates needed

## 📝 Git Workflow

### Commit Message Style
French language with conventional format:
```
[Type] Brief description

- Detailed change 1
- Detailed change 2

🤖 Generated with Claude Code
Co-Authored-By: Claude <noreply@anthropic.com>
```

### Common Types
- `Optimiser`: Performance/SEO improvements
- `Corriger`: Bug fixes
- `Ajouter`: New features
- `Améliorer`: Enhancements
- `Mettre à jour`: Updates

## 🌐 Deployment

### Requirements
- Static file hosting (Netlify, Vercel, GitHub Pages, etc.)
- No server-side rendering needed
- No build step required (CSS pre-compiled)

### Pre-Deployment Checklist
- [ ] Update Google Search Console verification code (line 26)
- [ ] Verify all URLs are production URLs
- [ ] Test on multiple devices/browsers
- [ ] Validate HTML/CSS
- [ ] Test structured data with Google Rich Results Test
- [ ] Verify analytics tracking

## 📚 Resources

- **Tailwind CSS**: https://tailwindcss.com/docs
- **Lucide Icons**: https://lucide.dev
- **Schema.org**: https://schema.org
- **Plausible Analytics**: https://plausible.io/docs
- **Google Search Console**: https://search.google.com/search-console

## 🤝 Contributing

When making changes:
1. Test locally before committing
2. Follow existing code style and patterns
3. Update this documentation if adding new patterns
4. Verify accessibility features remain intact
5. Test on mobile and desktop viewports

---

**Last Updated**: 2025-10-13
**Maintained by**: Tom (@thomasjeanneau)
