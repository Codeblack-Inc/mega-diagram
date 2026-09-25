# Third-party licenses

The mega-diagram skill is MIT-licensed (see [`LICENSE`](LICENSE)). It is a fork of diagram-design and bundles content from the following third-party sources, redistributed under their respective licenses.

## diagram-design (upstream)

- **License:** MIT — Copyright (c) 2025 Cathryn Lavery
- **Upstream:** https://github.com/cathrynlavery/diagram-design
- **Imported:** v2.6.33, commit `dc1ace47b99a419e42d01a03cb6ace5346efa8ae` (2026-09-19)
- **Used in:** the whole repository. The skill (`skills/mega-diagram/`), references, examples, commands, prompts, verification scripts, CI workflows, and ADRs come from diagram-design and were renamed and modified — mega palette, Pretendard for Hangul, transparent backgrounds, Korean document rules (`references/mega.md`), and mega manifests. Both copyright notices are kept in [`LICENSE`](LICENSE).

## Pretendard

- **License:** SIL Open Font License 1.1
- **Upstream:** https://github.com/orioncactus/pretendard
- **Used in:** loaded at render time (not bundled) from jsDelivr by the templates for Hangul labels.

## Space Grotesk

- **License:** SIL Open Font License 1.1
- **Upstream:** https://github.com/floriankarsten/space-grotesk
- **Used in:** outlined (converted to paths) in the `mega-diagram` wordmark under `docs/brand/`. No font file is bundled.

The icon sets below were bundled by diagram-design and are redistributed unchanged.

## Tabler Icons

- **License:** MIT
- **Upstream:** https://github.com/tabler/tabler-icons
- **Used in:** stroked icons in `skills/mega-diagram/references/primitive-icons.md` and `skills/mega-diagram/assets/icons.html` (categories: Compute, People, Network, Data, Kubernetes, Action, DevOps, plus the stroked Brand outlines for Docker, Terraform, AWS, Azure, GitHub).

The MIT license is reproduced in full at https://github.com/tabler/tabler-icons/blob/main/LICENSE.

## Simple Icons

- **License:** CC0 1.0 Universal (Public Domain Dedication)
- **Upstream:** https://github.com/simple-icons/simple-icons
- **Used in:** filled brand silhouettes in `skills/mega-diagram/references/primitive-icons.md` and `skills/mega-diagram/assets/icons.html` (Kubernetes, Google Cloud, PostgreSQL, Nginx, Gitea, Keycloak, MinIO, Apache NiFi, Apache Airflow, Trino, Apache Superset, Jupyter, Python, R).

The CC0 dedication is reproduced in full at https://github.com/simple-icons/simple-icons/blob/develop/LICENSE.md.

## log-z/logos

- **License:** MIT
- **Upstream:** https://github.com/log-z/logos/tree/main/website-logos
- **Used in:** filled brand silhouettes that aren't carried by Simple Icons or Tabler — currently MySQL, Redis, and StarRocks. Source SVGs are 100×100 with embedded `<style>` + class-based fills; the build script strips the style block and rewrites class refs to `currentColor` for monochrome consistency.

The MIT license is reproduced in full at https://github.com/log-z/logos/blob/main/LICENSE.

## Devicon

- **License:** MIT
- **Upstream:** https://github.com/devicons/devicon
- **Used in:** the RStudio and SPSS icons in `scripts/vendor/icons/devicon/`.

The MIT license is reproduced in full at https://github.com/devicons/devicon/blob/master/LICENSE.

## One-off sourced icons

The `scripts/vendor/icons/url/` directory contains one-off sourced icons for SAS, from [Wikimedia Commons](https://commons.wikimedia.org/wiki/File:SAS_logo_horiz.svg) (public domain), and Stata, from the [IcePanel Technology Icons collection](https://icon.icepanel.io/Technology/svg/Stata.svg) published via techicons.dev. Their provenance is recorded here; use of these product marks is covered by the Trademarks note below.

## Trademarks

Brand logos remain the trademarks of their respective owners. Their inclusion in this icon set is for documentation and illustrative use only. The presence of a brand mark in this repository does not imply endorsement, sponsorship, or affiliation.
