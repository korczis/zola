# Security policy

This repository is a **fork** of [getzola/zola](https://github.com/getzola/zola),
carrying a large-site performance program. It is not the upstream project and
does not speak for it.

## Reporting a vulnerability

**Use [private vulnerability reporting](https://github.com/korczis/zola/security/advisories/new).**
It is enabled on this repository. Please do not open a public issue for something
that looks exploitable.

Tell us what you can of: what you observed, the smallest way to reproduce it, the
commit or release you saw it on, and the platform. A report that says "this is
wrong and here is how I made it happen" is worth more than one that guesses at
severity.

There is no bounty and no service-level commitment. This is a fork maintained by
one person; you will get an honest answer, not a fast one.

## Which project is affected

Please establish this before reporting, because it decides who needs to know:

* **Upstream Zola** — reproduce it against an unmodified release, or against
  `9ec4407a` in this repository, which is upstream 0.23.3 with only measurement
  instrumentation added. Upstream does not currently have private vulnerability
  reporting enabled and has no `SECURITY.md`; the maintainer's contact address is
  in `Cargo.toml`. Report it there. If you tell us as well, we will help, but we
  cannot fix it for them.
* **This fork only** — report it here. The changes this fork carries are listed
  in `README.md` under "About this fork" and in `CHANGELOG.md`; the substantive
  ones touch the allocator, the render cache, syntax highlighting, template file
  hashing and `zola serve`'s in-memory store.

If you are not sure, report it here and say so. Working out which side of the
line something falls on is our job, not the reporter's.

## Scope

Zola is a build tool. Its templates, configuration and content are written by the
person running it, so "a template can do X" is usually a statement about the
author's own machine rather than a vulnerability. Two things make that judgement
less obvious, and reports about them are welcome:

* **Themes.** A site may pull in third-party templates, so a boundary that Zola
  states it enforces against templates is a real boundary.
* **Untrusted input.** A service that builds sites it did not author — a preview
  builder, a hosted platform — is relying on those same boundaries.

Known and already recorded: the containment check in `search_for_file` does not
hold on every path (`docs/performance/HOTSPOTS.md`). It is upstream behaviour, it
needs control of the templates, and it is documented rather than hidden.

## What we will do

Acknowledge the report, try to reproduce it, and tell you what we find — including
"we think this is working as intended, and here is why". If it turns out to be
upstream's, we will say so and, with your agreement, help get it there rather than
sitting on it.
