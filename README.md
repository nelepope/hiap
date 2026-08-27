# hiap

Site for **Health Is a Privilege**, a new play — served at https://healthisaprivilege.com via GitHub Pages.

Single static page, no build step. Everything lives in `index.html`: markup, CSS and the small
scroll-reveal script. Edit it directly and push.

## What still needs filling in

Every placeholder is marked two ways: an HTML comment starting `REPLACE:` above the block, and a
red dotted underline on the page itself (the `.tbc` class). When you replace the text, drop the
`tbc` class so the underline goes.

Find them all with:

```bash
grep -n "REPLACE\|tbc" index.html
```

The list, in page order:

- **Logline** — the one-sentence hook in the hero.
- **Venue name** — appears twice (hero meta strip and the tickets card) plus the venue address,
  the venue website link in the footer, and the `TheaterEvent` block in `<head>`.
- **Running time.**
- **Synopsis** — the pull-quote and three paragraphs.
- **Content note** — fill in or delete the block.
- **Cast & creatives** — every name and bio. Delete rows you don't need, duplicate the ones you do.
- **Press quotes** — leave the section deleted until there are real reviews to quote.
- **Production images** — see below.
- **Email addresses** — currently `hello@` and `press@healthisaprivilege.com`. Either set those up
  at the domain or swap them for the addresses you actually want public.
- **Mailing list** — the primary button is a `mailto:` for now. Swap the `href` for a signup URL
  (Mailchimp, Substack, whatever the producer uses) when there is one.
- **Instagram** link in the footer.

Once dates are confirmed: replace "To be announced" in the hero meta and the tickets card,
uncomment the **Book tickets** button and point it at the box office, and add `startDate` /
`endDate` to the `TheaterEvent` JSON-LD in `<head>`.

## Images

Drop files into `Pics/` and swap each placeholder figure in the gallery for:

```html
<figure class="shot"><img src="/Pics/filename.jpg" alt="Describe the moment shown"></figure>
```

For link previews on social, add a 1200×630 image at `Pics/og.jpg` and uncomment the two
`og:image` / `twitter:image` lines in `<head>`.

## DNS

Point healthisaprivilege.com at GitHub Pages with these records at the registrar:

| Type  | Name | Value                 |
|-------|------|-----------------------|
| A     | @    | 185.199.108.153       |
| A     | @    | 185.199.109.153       |
| A     | @    | 185.199.110.153       |
| A     | @    | 185.199.111.153       |
| CNAME | www  | nelepope.github.io.   |

Then in the repo: **Settings → Pages**, set the source to `main` / root, confirm the custom domain
reads `healthisaprivilege.com`, and tick **Enforce HTTPS** once the certificate has been issued
(that can take up to an hour after DNS propagates).

## Local preview

```bash
python3 -m http.server 8000
```

Then open http://localhost:8000.
