# Poa

A Poa is a small personal site made of Markdown files. Every Poa lists the other Poas its owner reads, and you find your way around by hopping from list to list. There is no central server, no signup and no algorithm.

## Make your own Poa

1. Go to [github.com/gearnoodle/poa-template](https://github.com/gearnoodle/poa-template) and press the green **Use this template** button, then **Create a new repository**. Name it `poa` and make it **Public**.
2. In the repository, go to **Settings → Pages**, choose **Deploy from a branch**, pick `main` and `/ (root)`, and save.
3. Edit `poa.md`: put your name in it.
4. After a minute your Poa is live at `https://<your-username>.github.io/poa/`.

Your Poa's address is `<your-username>.github.io/poa`. Give it to people so they can add you to their lists.

## Writing a post

1. Add a new file, for example `2026-11-20-my-post.md`. Starting the name with the date keeps posts in order.
2. Start it with a short header, then write in Markdown:

   ```markdown
   ---
   title: My post
   date: 2026-11-20
   ---
   Write here. **Markdown** works.
   ```

3. Add a line for it at the top of the Posts list in `poa.md`.

## Reading others

Add their addresses under "Poas I read" in `poa.md`, one per line:

```markdown
## Poas I read
- marta.github.io/poa
- jordi.github.io/poa
```

---

## The format (version 1)

**Address.** A Poa's address is the folder that holds `poa.md`. Readers add `/poa.md` themselves and assume `https://`. A full URL ending in `.md` is also accepted.

**`poa.md`** is the only required file:

```markdown
---
version: 1
name: Manu Järvinen
---
## Posts
- [Hello, Poa](2026-11-19-hello.md)

## Poas I read
- marta.github.io/poa
```

- The header sits between two `---` lines and holds `key: value` lines. `version: 1` is required. `name` is the name shown to readers.
- `## Posts` lists posts as Markdown links, newest first. Links are relative to `poa.md`.
- `## Poas I read` lists other Poas' addresses, one per line.

**Posts** are `.md` files with a header (`title`, `date` as `YYYY-MM-DD`) followed by Markdown (CommonMark). Readers must not run raw HTML in posts and only load images from the post's own site.

**Hosting.** Any host works if it serves the files over HTTPS. For web-based readers, the host must also allow cross-site requests (the header `Access-Control-Allow-Origin: *`). GitHub Pages does this by default.

**Offline means gone.** When a Poa's host is unreachable, readers show it as unreachable. They don't keep or pass on copies.

## This reader

`index.html` is a reader that shows your own Poa and lets you hop to the Poas you read. It's a single file with no build step.

**Search** follows the "Poas I read" lists outward from your Poa, up to 3 steps away by default (the Poas you read, the Poas they read, and so on), and searches names, post titles and the text of each Poa's 10 newest posts. It runs entirely in your browser; nothing is collected anywhere. The limits are at the top of the script in `index.html`. `markdown-it.min.js` is the Markdown renderer it uses (MIT licence). `.nojekyll` tells GitHub Pages to serve the `.md` files as they are.
