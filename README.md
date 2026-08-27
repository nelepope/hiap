# hiap

The website for **Health Is a Privilege**, a new play — live at https://healthisaprivilege.com.

---

## Changing the words on the site

**Go to [app.pagescms.org](https://app.pagescms.org), open this repository, click *Website content*.**

You'll see a form: Logline, Synopsis, Cast, Venue, and so on. Change what you want, hit save, and
the live site catches up in about a minute. That's the whole job — no code, no installing anything.

A few things worth knowing:

- **Empty fields hide themselves.** There's no need to invent a running time or a press quote to
  fill a gap. If a field is empty, that part of the page quietly disappears rather than showing a
  hole. The exceptions are the venue and the cast names, which show a red dotted "to be confirmed"
  instead — deliberately, so nobody forgets them.
- **The Book tickets button only appears once there's a link in *Box office link*.** Until then the
  mailing list button takes its place.
- **Images** go in through the CMS. Upload them in the Production images section and they're
  resized, stored and linked automatically.
- **Every save is undoable.** Nothing is ever really lost — the full history of every change is
  kept, so a mistake is a five-minute fix, not a disaster. Edit freely.

### Getting access

Pen invites you by email from inside Pages CMS (*Settings → Collaborators*). You do **not** need a
GitHub account — you'll get an email, set a password, and that's it.

---

## For anyone editing the files directly

Nothing here needs a build step. GitHub Pages compiles the site with Jekyll on every push.

| File | What it is |
|---|---|
| `_data/play.yml` | **All the words.** This is what the CMS form writes to. |
| `index.html` | The layout. Design, CSS and the `{{ slots }}` that pull text from `play.yml`. |
| `.pages.yml` | Defines the CMS form — what fields exist and what the hints say. |
| `_config.yml` | Jekyll settings. Rarely needs touching. |
| `Pics/` | Images. The CMS uploads here. |
| `CNAME` | Points the site at healthisaprivilege.com. Don't delete it. |

Two things to be careful of:

1. **Don't remove the `---` lines at the top of `index.html`.** They're what tells GitHub Pages to
   build the file. Without them the page stops updating and nothing obvious tells you why.
2. **The CMS rewrites `_data/play.yml` when it saves, and strips the explanatory comments in it.**
   That's expected. The same guidance lives in `.pages.yml` as field hints, which survive.

### Working on it locally

Ruby 2.7+ is needed for Jekyll, which macOS doesn't ship (system Ruby is 2.6). If you want a local
preview:

```bash
brew install ruby && gem install jekyll bundler
```

Then, from this folder:

```bash
jekyll serve
```

Honestly, though — for a site this size it's usually easier to push and look at the real thing.

---

## First-time setup

Not yet done. In order:

1. Create a repository called `hiap` at https://github.com/new — public, and **don't** add a README,
   .gitignore or licence, because this folder already has them.
2. Push it:

```bash
git remote add origin git@github.com:nelepope/hiap.git && git push -u origin main
```

3. **Settings → Pages**, set source to `main` / root. Confirm the custom domain says
   `healthisaprivilege.com`, and tick **Enforce HTTPS** once the certificate has been issued (can
   take up to an hour after DNS propagates).
4. Point the domain at GitHub. At the registrar:

   | Type | Name | Value |
   |---|---|---|
   | A | @ | 185.199.108.153 |
   | A | @ | 185.199.109.153 |
   | A | @ | 185.199.110.153 |
   | A | @ | 185.199.111.153 |
   | CNAME | www | nelepope.github.io. |

5. Install the Pages CMS GitHub App on the `hiap` repository from
   https://github.com/marketplace/pages-cms, then sign in at https://app.pagescms.org.
6. Invite your collaborator by email from *Settings → Collaborators* in Pages CMS.

## Still to sort out

- The site uses `hello@` and `press@healthisaprivilege.com`. Neither exists yet — either set them
  up at the domain or swap them for real addresses in the CMS under *Contact*.
- No link-preview image yet, so pasting the URL into WhatsApp or Instagram shows no picture. Add a
  1200 × 630 image under *Search & sharing → Link preview image*.
- The writer credit is blank, not assumed.
