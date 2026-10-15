# AGENTS.md

Static multi-page HTML site (Chinese web-design coursework). No build tooling, no package manager, no tests — open `index.html` directly in a browser; all pages work over `file://`.

## Structure

- `index.html` is the navigation hub; it links to every exercise page with `target="_blank"`. Keep it in sync when adding pages.
- Each exercise page (`1.html` … `10-3.html`, `biao.html`) is fully self-contained: inline `<style>` block in `<head>`, no shared stylesheet. Numbered base/variant pairs (e.g. `6.html` / `6-2.html`) are iterations of the same exercise.
- `css.css` exists but is empty — only `5.html` links it. Do not put page styles here.
- Images live in `img/` and are referenced with relative paths. Keep all HTML files in the repo root so relative links resolve.

## Conventions

- Chinese (`zh-CN`) content; match the existing charset (`UTF-8`) and font stack (`"Microsoft YaHei", "PingFang SC", "Segoe UI", sans-serif`) in new pages.
- Exercise pages follow the same card/gradient visual language as `index.html` — copy an existing page as a template rather than starting from scratch.
- All new CSS class names, ID names, and JS variables must start with `hjy` (e.g. `hjy-card`, `hjyTitle`, `hjyCount`). Existing pages predate this rule — do not mass-refactor them unless asked.
- Before executing any user request, append the prompt to `hjy_prompt.md` (never overwrite): timestamp `yyyy-MM-dd-HH:mm`, the model used, and the prompt text. Do this first, then carry out the task.
