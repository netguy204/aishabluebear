# Aisha Bluebear's Portfolio

The website for [aishabluebear.com](https://aishabluebear.com), migrated from
Squarespace to a [Jekyll](https://jekyllrb.com) static site hosted on **GitHub Pages**.

## Adding a new story / News post

Every story on the **News** page is one Markdown file in [`_posts/`](_posts/).
To add a new one, create a file named `YYYY-MM-DD-short-title.md` (the date controls
the order — newest shows first) with this shape:

```markdown
---
title: "My New Story"
date: 2026-04-01 12:00:00
image: /assets/images/my-new-story.webp
image_alt: "Short description of the picture"
caption: "A caption shown under the image."
link: "https://codespark.com/play/?a=story&p=XXXXXXXXX"
---
The teaser: a sentence or two describing the story. Shows above the image and
on the News cards.
```

The **teaser** (the body text below the `---`) and the **caption** (the `caption:`
field) are kept separate: the teaser appears above the image and on the News cards,
while the caption appears in italics directly under the image.

1. Put the picture in [`assets/images/`](assets/images/) and point `image:` at it.
2. `caption:` is optional — leave it out for a post with no image caption.
3. `link:` is the CodeSpark "Watch now" link (optional — leave it out for a post with
   no link). You can also link words inside the teaser with `[words](https://...)`.
4. Commit the file. GitHub rebuilds the site automatically in ~1 minute.

You can do all of this from GitHub's website (**Add file → Create new file**) — no
tools to install.

## Editing the "Soon" banner

The yellow scrolling banner text lives in [`_config.yml`](_config.yml) as `banner:`.
Set it to `""` to hide it. (Config changes need a fresh build, ~1 min.)

## Previewing locally (optional)

Requires Ruby. From the repo root:

```bash
bundle install
bundle exec jekyll serve --livereload
# open http://localhost:4000/aishabluebear/
```

## Going live on the custom domain

See the cutover steps in the migration notes. In short:

1. Set `baseurl: ""` in `_config.yml`.
2. Add a `CNAME` file at the repo root containing `aishabluebear.com`.
3. In **GitHub → Settings → Pages → Custom domain**, enter `aishabluebear.com`.
4. In the **Squarespace domain dashboard**, point DNS at GitHub Pages:
   - `A` records for the root `@`: `185.199.108.153`, `185.199.109.153`,
     `185.199.110.153`, `185.199.111.153`
   - `CNAME` record for `www` → `netguy204.github.io`
5. Enable **Enforce HTTPS** in GitHub Pages once the certificate is issued.
