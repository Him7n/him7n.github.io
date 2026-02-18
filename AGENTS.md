# AGENTS.md

Guidance for coding agents and contributors working in this repository.

## Project overview

- This is a static personal site built with plain HTML, CSS, and vanilla JavaScript.
- There is no build step, package manager, or framework in this repo.
- Main pages:
  - `index.html`: terminal-style home page with command parser.
  - `blog.html`: terminal-style blog index with command parser.
  - `posts/gitsense.html`: full blog post page.

## Working conventions

1. Keep changes simple and local.
   - Prefer direct edits to existing HTML/CSS/JS.
   - Avoid introducing new tooling unless explicitly requested.

2. Preserve the terminal UX.
   - Maintain keyboard behavior (`Enter`, arrow history, `Tab`, `Ctrl+L`).
   - Keep prompt visuals and command output style consistent.

3. Respect relative paths.
   - Root pages link to posts via `posts/<slug>.html`.
   - Post pages link back using `../index.html` and `../blog.html`.

4. Keep styling coherent across pages.
   - `index.html`, `blog.html`, and `posts/gitsense.html` each define their own CSS.
   - If changing shared theme tokens (`:root` colors, terminal frame styles), update all relevant pages for consistency.

## Adding or editing blog posts

When adding a new post page under `posts/`:

1. Add the post HTML file (copying existing post structure is preferred).
2. Update post metadata in `blog.html`:
   - Add a `<li class="post-item">` entry.
   - Add/update the `POSTS` JavaScript object for terminal commands.
3. Update post metadata in `index.html`:
   - Add/update the `BLOG_POSTS` JavaScript object so terminal commands can discover posts.
4. Verify terminal commands still work:
   - `ls`, `cd`, `cat`, and `help` on both `index.html` and `blog.html`.

## Quality checks

Before finishing:

- Open `index.html`, `blog.html`, and modified `posts/*.html` pages in a browser.
- Verify navigation links and command-driven navigation.
- Confirm no broken relative paths.
- Ensure console has no new JavaScript errors.

Optional local preview:

```bash
python3 -m http.server 8000
```

Then browse `http://localhost:8000/`.

## Scope and safety

- Do not rewrite unrelated content or restyle the whole site unless requested.
- Keep text/content edits intentional and minimal outside requested scope.
- If user instructions conflict with this file, follow user instructions.
