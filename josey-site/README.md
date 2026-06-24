# joseybarlow.com — Hugo site

This folder has your **content** and **config** fully set up for Josey Barlow's
portfolio + blog (engineering, baking, crochet) using the Starry Hugo theme.

It does **not** yet include the theme's actual template/CSS files — those live in a
separate repository and need to be pulled in once. This only takes 3 commands.

## One-time setup

You'll need [Hugo](https://gohugo.io/installation/) installed (extended version,
v0.154.0+ recommended), and Git.

```sh
cd joseybarlow.com          # this folder
git init                    # only if this folder isn't already a git repo
git clone https://github.com/meethigher/hugo-theme-starry.git themes/starry
hugo server
```

Then open the URL it prints (usually `http://localhost:1313/`) to preview the site.

## What's already done for you

- `hugo.toml` — site title, your name, navigation menu (About, Posts, Categories,
  Tags, Newsletter), and category/tag taxonomies are all configured.
- `content/about/index.md` — your About page, written for an EE senior with
  baking and crochet as side interests.
- `content/newsletter/index.md` — a newsletter signup page with a placeholder
  email-capture form (see "Newsletter setup" below).
- `content/archives/` — three starter posts, one each for Engineering, Baking,
  and Crochet, so you can see how categories and tags work.
- `archetypes/default.md` — a template Hugo uses whenever you create a new post,
  so new posts start with the right front matter automatically.

## How to write and publish a new article

This is the part that trips people up the first time, so here's the full picture:

1. **Create the file.** From the site's root folder, run:
   ```sh
   hugo new content archives/my-new-post-title/index.md
   ```
   This creates a new folder under `content/archives/` with an `index.md` file
   pre-filled from the archetype above. Using a folder (`my-new-post-title/index.md`)
   rather than a single `.md` file means you can drop images right next to it — see
   the existing posts for examples, e.g. `content/archives/post-1/index/`-style
   image folders in the original example content.

2. **Edit the front matter at the top of the file:**
   - `title` — the post title shown on the site
   - `categories` — pick ONE main bucket, e.g. `[Engineering]`, `[Baking]`, or `[Crochet]`
     (you can add more categories later, like `[Crochet, Gift Ideas]`)
   - `tags` — more specific keywords, e.g. `[sourdough, bread]` or `[granny-square, blanket]`
   - `draft` — set to `false` when you're ready to publish; while `true`, it won't
     show up on the live site
   - `date` — when it should be considered published; this also controls sort order

3. **Write the post** below the `<!--more-->` line in Markdown. Everything above
   `<!--more-->` is the short summary shown in post listings; everything below is
   the full article.

4. **Add images** by putting them in the same folder as your post's `index.md`
   (e.g. `content/archives/my-new-post-title/photo.jpg`) and referencing them
   in Markdown like `![Alt text](photo.jpg)`.

5. **Preview locally** with `hugo server` (if it's not already running) and check
   `localhost:1313` — drafts show up automatically in the dev server.

6. **Publish.** Once happy, run `hugo` (no arguments) to build the static site
   into the `public/` folder, then deploy that folder — or, if you're hosting on
   Netlify, Vercel, or GitHub Pages, just push your changes to your Git repo and
   the host will rebuild automatically. (Let me know where you're planning to
   host it and I can write the exact deploy steps for that service.)

## Newsletter setup

Hugo builds a static site, so it can't "receive" signups itself — you need a
free third-party email service to actually collect addresses. I've left a
placeholder form in `content/newsletter/index.md` for **Buttondown**, with
comments in that file explaining how to swap in Buttondown, Kit (ConvertKit),
or Mailchimp instead. Steps in short:

1. Create a free account with one of those services.
2. Find their "embed form" / "signup form" HTML snippet in their dashboard.
3. Paste that snippet over the placeholder `<form>...</form>` block in
   `content/newsletter/index.md`.

That's it — no backend or database needed, since the email service handles
storage and sending for you.

## Categories vs. tags, quickly

- **Categories** = the big sections (Engineering / Baking / Crochet). Keep this
  list short and stable.
- **Tags** = specific topics within a category (e.g. `sourdough`, `pcb-design`,
  `granny-square`). Use as many as are genuinely useful for searching later.

Both automatically get list pages (e.g. `/categories/baking/` and `/tags/sourdough/`)
once you build the site — no extra setup needed beyond adding them to a post's
front matter.
