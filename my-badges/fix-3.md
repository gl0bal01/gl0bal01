<img src="https://my-badges.github.io/my-badges/fix-3.png" alt="I did 3 sequential fixes." title="I did 3 sequential fixes." width="128">
<strong>I did 3 sequential fixes.</strong>
<br><br>

Commits:

- <a href="https://github.com/gl0bal01/lecodex/commit/bad65554ed116943d3484c07619bc80a12f645cd">bad6555</a>: fix(seo): canonical URLs pointed at 404s; new brand favicon

Every canonical on the site was unreachable. Head.tsx appended a
trailing slash unconditionally, but nginx serves pages extensionless and
without one, so /CTF/CTF-Index/ 404'd while /CTF/CTF-Index served 200.
Folder and tag pages were worse: their slug keeps an "index" leaf that
is not part of the URL, so they advertised /Investigations/index/.
Confirmed against production before fixing. Search engines honour
rel=canonical, so this is how pages get dropped from an index.

Canonical is now derived from the served path: strip the "index" leaf,
no trailing slash except the site root. og:url and twitter:url follow.
Verified by serving the output under the production nginx config and
requesting all 310 unique canonicals: 310 x 200, none failing.

content-index emits folder pages with a trailing slash, which disagreed
with the canonical, so the sitemap is normalised in the same build step
as the JSON-LD injection. Canonical and sitemap URL sets are now
identical (310 each, zero mismatches).

Icons: the old set was a LE CODEX wordmark on rust-red — the pre-rebrand
palette, and illegible below ~64px. Replaced with an LC monogram on the
navy/cyan brand ground, checked at 16px and 32px, with the mark inside
the safe zone on the maskable variants. scripts/build-icons.mjs
regenerates the whole set; favicon.ico derives from icon.png at build.
- <a href="https://github.com/gl0bal01/lecodex/commit/de90657a46413b67050aaf02c87cb4f3a051b55e">de90657</a>: fix(cache): stop pinning stale CSS in browsers, CDN and the service worker

The palette shipped but visitors kept seeing the old orange. Three
layers were holding the previous build:

- nginx served every .css/.js as `max-age=2592000, immutable`, on the
  assumption in its own comment that "Quartz emits content-hashed
  JS/CSS". It does not: index.css, prescript.js and postscript.js keep
  stable names and are rewritten in place each build, so `immutable`
  pinned a stale copy in every browser for 30 days with no revalidation.
  They now get 5 minutes plus must-revalidate; ETag keeps that a 304.
  Fonts and images, which really are stable, keep the long cache.
- Cloudflare had cached the same response (cf-cache-status HIT, age 46 h)
  and will keep serving it until the zone is purged.
- the service worker caches .css cache-first under a VERSION hashed only
  over its own template and the precached icons/manifest, so a CSS-only
  change never invalidated it — installed clients would have kept the old
  asset cache indefinitely. VERSION now comes from a GIT_SHA build arg,
  so every build gets a new cache and activate() drops the old one.

Verified on the built image: index.css and prescript.js revalidate,
static icons unchanged, and sw.js carries the injected version.
- <a href="https://github.com/gl0bal01/lecodex/commit/df9101b8d330dc6e08be3998bbdf10616aab7b2a">df9101b</a>: fix: real commit dates for content, drop stray content gitlink

CI removed content/.git before the image build, so CreatedModifiedDate's
`git` priority never fired and any page without a frontmatter date fell
back to filesystem mtime — which, after actions/checkout, is build time.

The removal was defensive and unnecessary: this is a multi-stage build
and the runtime stage only copies public/ out of a discarded builder, so
the vault history never had a path into the shipped image. Verified on
the built image: no .git anywhere.

Keeping it needs the .dockerignore exception too, since **/.git would
otherwise strip it from the build context.

Effect, measured locally: sop-malware-analysis now reports its real last
commit date (2026-04-26) instead of the build date. Pages that carry a
frontmatter date keep it — frontmatter still wins by priority order.

Also drop the stray `content` gitlink (mode 160000, no .gitmodules) that
had replaced content/.gitkeep in the index, and restore the .gitkeep.


Created by <a href="https://github.com/my-badges/my-badges">My Badges</a>