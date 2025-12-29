# Overview

This is a Vietnamese-language promotional landing page for "Cen iOS Store," showcasing iOS applications including "FunTap PUBG" and "Cen Map AOV". The project is a clean, modern static website that displays app information, pricing tiers, download links, and includes a dark/light theme toggle with localStorage persistence. This single-page marketing site is optimized for mobile and desktop viewing.

# Recent Changes (November 23, 2025)

- Refactored HTML for cleaner structure and better organization
- Separated CSS into external stylesheet (styles.css) for better maintainability
- Fixed HTML validation errors (malformed strong tags)
- Enhanced responsive design with improved mobile layout
- Added localStorage theme persistence (remembers user's dark/light mode preference)
- Improved UX with better animations and visual feedback on buttons
- Added emoji icons for better visual appeal
- Removed unnecessary commented-out code
- Organized all assets in root directory for easier access
- **NEW: Countdown Timer System** - Free key timers (3h, 6h) with real-time countdown, auto-updates every second
- **NEW: Statistics Dashboard** - Shows total downloads and simulated online users (random 150-200, updates every 30s)
- **NEW: Review & Rating System** - Users can rate 1-5 stars and write reviews, stores in localStorage, displays 10 most recent
- **NEW: Notification Banner** - Auto-appears after 2 seconds on page load, dismissible, announces new apps/keys
- **SECURITY FIX: XSS Protection** - Implemented HTML escaping for all user-generated review content to prevent XSS attacks

# User Preferences

Preferred communication style: Simple, everyday language.

# System Architecture

## Frontend Architecture

**Technology Stack**
- Pure HTML5, CSS3, and vanilla JavaScript
- No frameworks or build tools required
- Static site architecture suitable for simple hosting

**Design Pattern**
- Single-page application (SPA) pattern without routing
- Component-based visual structure using semantic HTML
- CSS custom properties (CSS variables) for theming
- Event-driven JavaScript for interactivity (theme toggle, copy functionality)

**Theming System**
- CSS custom properties define color schemes in `:root` and `body.dark` selectors
- JavaScript-based theme toggling that likely persists user preference
- Supports both light and dark modes with smooth transitions

**File Organization**
- Separation of concerns: HTML (index.html), CSS (styles.css), and inline JavaScript
- All assets stored in root directory for easy access
- Images: banner.jpg, Aov.png, icon-120.png, icon-512.png, hd1.png, hd2.png, hd3.png
- Manifest files: app.plist, lienquanvu.plist, Kogiat.plist

**Responsive Design**
- Mobile-first viewport meta tag
- Max-width container pattern (800px) for content constraint
- CSS transitions for smooth visual feedback

## Data Architecture

**Static Content**
- No backend or database
- All content hardcoded in HTML
- Pricing information, app keys, and metadata stored directly in markup
- Code snippet for promotional key: `CeniOs-hour-ijEXMWqmg1qyTa1d`

## User Interaction Patterns

**Copy-to-Clipboard Functionality**
- Interactive code elements with `onclick` handlers
- Uses JavaScript Clipboard API for key copying
- User-friendly alert messages with success/failure feedback
- Graceful fallback for environments where clipboard API is unavailable

**Theme Persistence**
- Theme toggle button with dynamic emoji icons (🌙 for light mode, ☀️ for dark mode)
- localStorage-based persistence - remembers user preference across sessions
- Smooth transitions between light and dark modes

# External Dependencies

## Client-Side Technologies
- **Browser APIs**: Clipboard API (for copy functionality), localStorage (implied for theme persistence)
- **Fonts**: System font stack (`-apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto`) - no external font loading

## Hosting Requirements
- Static file hosting capable server
- No server-side processing required
- Can be deployed on: GitHub Pages, Netlify, Vercel, or any static hosting service

## Asset Dependencies
- `favicon.ico` - site favicon
- `banner.jpg` - application banner image
- `icon-120.png` - app icon (120px size suggests iOS app icon dimensions)
- These assets are referenced but not included in the visible repository files

## No External Service Integrations
- No analytics tracking visible
- No CDN dependencies
- No third-party API calls
- Self-contained application with no runtime external dependencies