# Flash Game Library - Design Guidelines

## Design Approach

**Reference-Based Approach:** Drawing inspiration from classic Flash gaming portals (Newgrounds, Miniclip, Kongregate) from the early-to-mid 2000s era, modernized with contemporary web standards. The design should evoke nostalgia while maintaining clean, usable interfaces.

**Core Principle:** Celebrate the retro gaming aesthetic without sacrificing modern UX patterns. Think "pixel-perfect nostalgia meets 2024 web standards."

## Typography System

**Primary Font:** "Press Start 2P" or similar pixel/bitmap font for headings and game titles (via Google Fonts)
**Secondary Font:** System font stack (Inter, SF Pro, Segoe UI) for body text and UI elements to maintain readability

**Hierarchy:**
- Page title: Pixel font, large (text-4xl to text-5xl)
- Game titles: Pixel font, medium (text-lg to text-xl)
- Body/UI text: System font, standard sizes (text-sm to text-base)
- Metadata: System font, small (text-xs to text-sm)

## Layout System

**Spacing Units:** Consistently use Tailwind units of 2, 4, 6, and 8 for tight spacing; 12, 16, and 20 for generous spacing (p-4, gap-6, mb-8, py-16, etc.)

**Container Structure:**
- Main container: max-w-7xl mx-auto px-4
- Game grid: max-w-6xl mx-auto
- Player view: max-w-5xl mx-auto (when fullscreen not active)

## Component Library

### Game Library Grid
- Responsive grid: grid-cols-2 md:grid-cols-3 lg:grid-cols-4 xl:grid-cols-5
- Gap between cards: gap-4 md:gap-6
- Card design: Rounded corners (rounded-lg), subtle borders, hover lift effect
- Card content: Thumbnail (aspect-ratio-square or 4:3), game title below, file size indicator

### Game Card Elements
- Thumbnail container: Full-width image with aspect ratio container
- Fallback placeholder: Pixel art style icon for games without thumbnails
- Title: Pixel font, truncate with ellipsis (line-clamp-2)
- Metadata bar: Small system font showing file size, last modified
- Play overlay: Appears on hover with semi-transparent backdrop and play icon

### Player Interface
- Full-width container with centered game canvas
- Canvas wrapper: Maintains aspect ratio (aspect-video or 4:3 based on game)
- Control bar below canvas: Fullscreen toggle, back to library button, game info
- Spacing: Generous padding around player (py-8 to py-12)

### Header/Navigation
- Sticky header: h-16 to h-20
- Logo/title: Pixel font with retro gaming icon
- Right-aligned utilities: Game count indicator, view toggle (grid/list)
- Breadcrumb navigation when in player view

### Empty States
- Centered message: "No games found - Add .swf files to the games folder"
- Pixel art illustration or retro folder icon
- Helpful instructions in system font

## Icons

**Library:** Font Awesome (via CDN) for modern UI icons
- Play button: fa-play
- Fullscreen: fa-expand/fa-compress
- Back arrow: fa-arrow-left
- Grid view: fa-th
- List view: fa-list

**Custom retro elements:** Use pixel-art styled borders, decorative corners, and arcade-inspired visual accents

## Animations

**Minimal, purposeful animations:**
- Card hover: Subtle lift (translate-y-1) with shadow increase
- Loading spinner: Retro-styled rotating element while Ruffle initializes
- Page transitions: None or simple fade
- NO scroll-triggered animations, NO complex motion

## Accessibility

- All interactive elements have proper focus states with visible outlines
- Alt text for game thumbnails
- Keyboard navigation: Arrow keys for grid navigation, Enter to launch game, Escape to exit fullscreen
- Screen reader announcements for game launches and state changes

## Images

**Thumbnails:** Game preview images (user-provided or auto-generated from .swf metadata)
- Format: PNG or JPG
- Size: 320x240px or 400x300px
- Fallback: Generic retro game controller icon or pixel art placeholder

**No hero image** - Jump straight into the game grid. This is a utility-focused app, not a marketing page.

## Layout Patterns

**Library View:**
- Minimal header (h-16)
- Optional filters/search bar (h-12 to h-16)
- Game grid starts immediately with pt-6
- Footer with file management instructions

**Player View:**
- Header with back button and game title
- Centered game canvas with generous breathing room
- Control bar directly below canvas
- No sidebar clutter - focus on the game

**Vertical Rhythm:** Consistent section spacing of py-8 to py-12 throughout. Cards and components use p-4 to p-6 internally.

This design celebrates Flash gaming's golden era while delivering a clean, modern browsing and playing experience. The pixel fonts and retro visual elements provide nostalgia, while the grid layout and responsive design ensure excellent usability.