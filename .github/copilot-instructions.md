<!-- .github/copilot-instructions.md -->
# HPP Law — Copilot / AI Agent Instructions

Purpose: give AI coding agents immediate, actionable context for working on this repository.

- **Project type**: Static marketing website (multi-page HTML/CSS/JS). No build step, server, or backend.
- **Primary files**: top-level HTML pages (`index.html`, `contact.html`, `our-story.html`, `layanan.html`, `partner.html`, `visi-misi.html`), styles in `css/style.css`, client JS in `js/script.js`.

Key architecture and intent
- The site is a small, static marketing site for HPP Law Office. Pages are standalone HTML files styled using Tailwind CDN in `index.html` plus project-specific CSS in `css/style.css`.
- Design choices: Tailwind utilities via CDN are used together with handcrafted CSS classes for brand colors and small animations (see `.gold-text`, `.gold-bg`, `.navy-bg`, `.service-card`, `.fade-in`, `.slide-up`, `.scale-in`). Preserve these names when adding/ changing styles.

Project-specific patterns and conventions
- Language: pages use `lang="id"` (Indonesian). Keep or update `lang` appropriately when adding content.
- Filenames / routes: pages live at repository root and link to each other using relative paths (`index.html`, `contact.html`, ...). Do not rename without updating links across the other HTML files.
- Brand classes: reuse `brand-font`, `gold-text`, `gold-bg`, `navy-bg` to maintain consistent typography and colors.
- Service cards: the `.service-card` pattern (in `index.html` and `css/style.css`) is used for hover/interaction — prefer this structure for new service-like UI blocks.
- JS hooks: `js/script.js` expects DOM elements with IDs `mobile-menu-button` and `mobile-menu` and uses `a[href^="#"]` for smooth scrolling. Keep these IDs and anchor structure when modifying navigation.

Examples (refer to these files when making edits)
- Mobile menu toggle: `js/script.js` — toggles `hidden` on `#mobile-menu`. If you change the mobile markup, update this script accordingly.
- Inline styles vs. `css/style.css`: `index.html` contains inline <style> blocks for animations used across pages; `css/style.css` holds repeated utility classes. When adding new global styles, prefer `css/style.css`.
- Components: many sections are copy-paste friendly (hero, services, blog teaser, footer). Use the same Tailwind + custom-class approach when creating new sections.

Developer workflows (how to run/test locally)
- Quick preview: open `index.html` in a browser (double-click or run PowerShell: `start index.html`).
- Local static server (recommended for testing relative requests):
  - Powershell: `python -m http.server 8000; start http://localhost:8000`
  - Or Node (if installed): `npx serve .`
- Debugging: use browser devtools. There are no automated tests or build scripts in the repo.

When editing UI or content
- Preserve relative links between HTML files. Update navigation menus across all pages when adding or renaming pages.
- Keep external CDNs (Tailwind, FontAwesome, Google Fonts) unless asked to vendor them.
- Use existing color classes (`.gold-text`, `.gold-bg`, `.navy-bg`) for brand consistency instead of arbitrary color hexes.
- For accessibility: ensure images have `alt` text and anchors that navigate within the page target existing `id` attributes.

When adding code or assets
- Add images and local assets under a new `assets/` directory (e.g., `assets/img/`), and reference them with relative paths.
- Avoid changing the top-level HTML structure radically—this is a small site where consistency matters more than large refactors.

Non-goals / things not present
- There is no backend, build pipeline, or test harness in this repo. Do not add complex build tooling unless the owner asks.

If you modify files
- Update only the files required for the change. Keep edits minimal and preserve page links.
- If you add JavaScript behavior that relies on new DOM elements, add matching IDs/classes and update `js/script.js` or add a new file in `js/` and include it in the affected HTML files.

Contact for clarification
- Ask the repository owner before introducing new infrastructure (CI, build systems), or renaming pages.

If this file already existed, merge guidance
- Preserve any custom instructions already present; supplement with the project-specific bullets above, ensuring references to `css/style.css` and `js/script.js` remain accurate.

-- end
