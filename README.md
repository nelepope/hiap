# hiap

The website for **Health is a Privilege**, a play by Simonetta Gibejova — live at
https://healthisaprivilege.com.

---

## Changing the words on the site

**Go to [app.pagescms.org](https://app.pagescms.org), open this repository, click *Website content*.**

You'll see a form: Byline, Tagline, Synopsis, Cast, Venue, and so on. Change what you want, hit save, and
the live site catches up in about a minute. That's the whole job — no code, no installing anything.

A few things worth knowing:

- **Empty fields hide themselves.** There's no need to invent a running time or a press quote to
  fill a gap. If a field is empty, that part of the page quietly disappears rather than showing a
  hole. The exceptions are the venue and the cast names, which show a greyed "to be confirmed"
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
| `Pics/` | Web images. **Only the files listed in `.gitignore` are published** — anything else you drop in here stays local, which is deliberate. |
| `Pics/brand/` | The wordmark (transparent PNG) and the link-preview card, both generated from `Brand /whiteonblack.jpeg`. |
| `Pics/originals/` | Full-size originals. Local only, never published. |
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


## A note on the images

`Pics/` is whitelist-based: nothing in it reaches the live site unless it is
explicitly un-ignored in `.gitignore`. Drop originals, PDFs, raw files or anything
else in there freely — they stay on your Mac. To publish a new image, either upload
it through the CMS (which commits it directly and bypasses this) or add its filename
to the exceptions at the bottom of `.gitignore`.

The first two images in **Production images** are used differently from the rest:
they run full-screen between sections. Put the strongest ones first.

## A note on the design

The identity is the project's own: the handwritten wire wordmark, extracted to a
transparent PNG so it sits on black cleanly. Everything else is deliberately quiet —
light, widely letterspaced capitals — so the handwriting is the only voice on the
page. If you add type, keep it in that register.

## Setup status

- [x] Repository on GitHub — `nelepope/hiap`
- [x] GitHub Pages building from `main` / root
- [x] DNS at Porkbun, HTTPS certificate issued, Enforce HTTPS on
- [x] Live at https://healthisaprivilege.com
- [x] Pages CMS connected
- [ ] Collaborator invited (*Settings → Collaborators* in Pages CMS)
- [ ] Real copy in place — the site is hidden from search engines until it is

## Still to sort out

- The site uses `hello@` and `press@healthisaprivilege.com`. Neither exists yet — either set them
  up at the domain or swap them for real addresses in the CMS under *Contact*.
- The synopsis is empty, so the whole *The play* section is currently hidden. It appears as soon as
  there are words in it.
- The award band is empty. If you want the Warwick Film Festival win on the site, fill in *Award /
  accolade* — but note the award was for the film, so word it so it doesn't read as the play's.
- Casting is a single placeholder row. Add rows as people are cast, or leave it.
- The link-preview card is the wordmark on black. Swap it for a production still under
  *Search & sharing* if you'd rather.
