<img src="https://my-badges.github.io/my-badges/fix-2.png" alt="I did 2 sequential fixes." title="I did 2 sequential fixes." width="128">
<strong>I did 2 sequential fixes.</strong>
<br><br>

Commits:

- <a href="https://github.com/gl0bal01/lecodex/commit/50e98589589f642f0363f2b966bbda67dc16ecd6">50e9858</a>: fix(ui): hide TOC on homepage

Article body is hidden by HomeHero on slug=index, so the right-sidebar
.toc and mobile .mobile-toc reference headings that aren't visible.
Hide both on the homepage.
- <a href="https://github.com/gl0bal01/lecodex/commit/f81dc42d00c434af83ad076d062e0681db3639e6">f81dc42</a>: fix(ui): inline icon next to card title on landing

Wrap icon + h3 in .landing-card-head flex row so they share a line
instead of stacking. Icon size dropped to 1.6rem; flex-shrink:0
keeps it from collapsing on narrow widths.


Created by <a href="https://github.com/my-badges/my-badges">My Badges</a>