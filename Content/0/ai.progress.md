# AI Progress Notes

## Session 1 - Login Template Redesign

### What was done:
- Redesigned `login.html` template to match the visual style of `welcome.html`
- Removed Bulma CSS dependency and Font Awesome - now uses pure custom CSS like the welcome page
- Adopted the welcome template's design system (Inter font, indigo/cyan palette, animated bg, glassmorphism cards, fadeInUp animations, Heroicons SVGs)
- Layout: CSS Grid with welcome text on left, login card on right
- Compiled LOGIN action successfully

### Session 2 - Made feature list generic

Updated the four feature bullet points on the login page from business-specific items to generic portal features:

| Before | After |
|--------|-------|
| View statements & invoices | Your personalized dashboard at a glance |
| Place orders online | Real-time data from Business Central |
| Track shipments & deliveries | Submit requests & interact online |
| Secure access to your account information | Secure access to your account information |

Also updated:
- Badge text from "Customer Portal" to "Self-Service Portal"
- Description text to be more generic: "...access your personalized portal powered by live Business Central data"
- New matching icons: grid/dashboard, database/cylinder, chat bubble, shield-check
- Compiled LOGIN action

### Session 3 - Extracted CSS into shared action

Created a centralized CSS action (`CSS`) so styles are no longer embedded inline in each page:

**New action created:**
- `CSS` (type: file) — uses template `portal.css`, serves shared stylesheet with `<?mimetype('text/css')?>` 

**Template `portal.css` contains all styles organized in sections:**
- Shared Foundation (reset, variables, body, animated background)
- Header (logo, badges)
- Buttons (primary, secondary)
- Hero badge / welcome badge (shared pulse dot badge, gradient text)
- Footer
- Animations (fadeInUp, spin, pulse)
- Welcome Page Styles (hero, features grid, feature cards, divider, steps)
- Login Page Styles (login grid, welcome section, feature list, login card, form fields, error message, contact info) — scoped under `body.login-page` for flex layout
- Responsive breakpoints

**Updated templates:**
- `welcome.html` — replaced `<style>` block with `<link rel="stylesheet" href="<?action('CSS')?>">`
- `login.html` — replaced `<style>` block with `<link rel="stylesheet" href="<?action('CSS')?>">`, added `class="login-page"` to `<body>` tag for page-specific flex layout

**Compiled all actions.**

### Session 4 - Added APDSCRIPT link to both pages

Added `<script src="<?action('APDSCRIPT')?>"></script>` to the `<head>` section of both templates:
- `welcome.html` — added after the CSS link
- `login.html` — added after the CSS link, before Company Information table tags

Compiled all actions.

### Existing Actions:
- `APDSCRIPT` - APD Script (type 0) - uses `apdscript.js` template
- `CSS` - Shared CSS Stylesheet (type file) - uses `portal.css` template
- `LOGIN` - Login (type 0) - uses `login.html` template
- `LOGINCHECK` - Login Check (type 3 / script)
- `WELCOME` - Welcome Landing Page (type 0) - uses `welcome.html` template

### Templates:
- `apdscript.js` - JavaScript library
- `login.html` - Login page (uses external CSS + APDSCRIPT)
- `portal.css` - Shared CSS stylesheet
- `welcome.html` - Welcome/landing page (uses external CSS + APDSCRIPT)