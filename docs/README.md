# Rhino Tools Wiki

A self-contained documentation site for the scripts in this repository, in the style of Rhino's own command reference: one page per tool with an ELI5 explanation, an animated demonstration, the exact command-line prompts, tips, known issues and cross-references.

**Open it:** double-click `docs/index.html`, or serve the `docs/` folder with any static file server.

**Host it:** in the repository settings, enable GitHub Pages from the default branch, folder `/docs`. The site will appear at `https://notkoosh.github.io/rhinotools/`.

## Layout

Everything is in `index.html`. There is no build step and no dependency except Google Fonts (the page falls back to system fonts without it).

- Each wiki page is an `<article class="page" id="page-NAME">`. The URL hash selects the page (`index.html#dogbone`), so links between pages are plain `href="#NAME"`.
- The left-hand tree is the `<nav class="sidenav">`. Each `<li>` carries `data-k="…"` keywords that the search box also matches against.
- Animations are inline SVG. Every animated element runs the same looping timeline (`--dur` on the `.anim` wrapper); keyframes named `vA-B` make an element visible from A % to B %. Elements that should remain in the final frame have `opacity="1"` as their static attribute, so the drawing still shows the finished state when the viewer prefers reduced motion.
- The 3D-looking scenes use an oblique projection: screen X = x + 0.45·y, screen Y = −z − 0.28·y. Faces carry classes `top`, `front`, `side` inside a group classed `ply`, `oak` or `maple` for the wood tones.
- Colours are CSS custom properties at the top of the stylesheet and switch with the system light/dark theme.

## Adding a tool page

1. Copy an existing tool `<article>` and change its `id`, `data-title`, breadcrumbs, heading and chips.
2. Add a `<li>` to the right group in the nav with `href="#NAME"` and keywords.
3. Add "See also" cards on related pages so the new page is reachable from more than the tree.
4. For an animation, draw an SVG with a `viewBox` of `0 0 440 250`, give animated elements `data-a=""` and `style="animation-name:…"`, and add the matching `@keyframes` to the stylesheet.
