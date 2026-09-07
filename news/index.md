# Changelog

## gutenbergr (development version)

## gutenbergr 0.5.2

CRAN release: 2026-06-27

- [`gutenberg_get_all_mirrors()`](https://docs.ropensci.org/gutenbergr/reference/gutenberg_get_all_mirrors.md)
  now works with `readMDTable` (\>= 0.4.0), which returns a named list
  of tibbles from `read_md_table()` instead of a single tibble
  ([@jrdnbradford](https://github.com/jrdnbradford))

## gutenbergr 0.5.1

CRAN release: 2026-05-02

- Fixed an issue where
  [`gutenberg_download()`](https://docs.ropensci.org/gutenbergr/reference/gutenberg_download.md)
  duplicated every line for works with multiple authors
  ([@fditraglia](https://github.com/fditraglia),
  [\#148](https://github.com/ropensci/gutenbergr/issues/148);
  [@jrdnbradford](https://github.com/jrdnbradford),
  [\#149](https://github.com/ropensci/gutenbergr/issues/149))

## gutenbergr 0.5.0

CRAN release: 2026-03-15

- A new
  [`gutenberg_add_sections()`](https://docs.ropensci.org/gutenbergr/reference/gutenberg_add_sections.md)
  function is available to create forward-filled section markers
  ([@jrdnbradford](https://github.com/jrdnbradford),
  [\#138](https://github.com/ropensci/gutenbergr/issues/138))
- [`gutenberg_download()`](https://docs.ropensci.org/gutenbergr/reference/gutenberg_download.md)
  now adds a `User-Agent` string to identify itself to the Project
  Gutenberg mirror ([@jrdnbradford](https://github.com/jrdnbradford),
  [\#139](https://github.com/ropensci/gutenbergr/issues/139))
- Documentation now includes two vignettes that detail advanced usage
  ([@jrdnbradford](https://github.com/jrdnbradford),
  [\#142](https://github.com/ropensci/gutenbergr/issues/142),
  [\#143](https://github.com/ropensci/gutenbergr/issues/143),
  [\#144](https://github.com/ropensci/gutenbergr/issues/144))

## gutenbergr 0.4.1

CRAN release: 2026-01-19

- `cli` messaging has been improved
  ([@jrdnbradford](https://github.com/jrdnbradford),
  [\#134](https://github.com/ropensci/gutenbergr/issues/134))
- gutenbergr now has a logo
  ([@jrdnbradford](https://github.com/jrdnbradford),
  [\#133](https://github.com/ropensci/gutenbergr/issues/133))
- [`gutenberg_get_all_mirrors()`](https://docs.ropensci.org/gutenbergr/reference/gutenberg_get_all_mirrors.md)
  now provides helpful instructional messaging instead of erroring if
  <https://www.gutenberg.org/MIRRORS.ALL> is not unavailable or cannot
  be parsed ([@jrdnbradford](https://github.com/jrdnbradford),
  [\#132](https://github.com/ropensci/gutenbergr/issues/132))
- [`gutenberg_get_mirror()`](https://docs.ropensci.org/gutenbergr/reference/gutenberg_get_mirror.md)
  now falls back to a known stable mirror (<https://aleph.pglaf.org>) if
  there is no `gutenberg_mirror` option set and
  [`gutenberg_get_all_mirrors()`](https://docs.ropensci.org/gutenbergr/reference/gutenberg_get_all_mirrors.md)
  cannot determine a mirror
  ([@jrdnbradford](https://github.com/jrdnbradford),
  [\#132](https://github.com/ropensci/gutenbergr/issues/132))
- The package startup message now only appears if
  [`interactive()`](https://rdrr.io/r/base/interactive.html)
  ([@jrdnbradford](https://github.com/jrdnbradford),
  [\#128](https://github.com/ropensci/gutenbergr/issues/128))

## gutenbergr 0.4.0

CRAN release: 2026-01-12

- gutenbergr now caches works downloaded with
  [`gutenberg_download()`](https://docs.ropensci.org/gutenbergr/reference/gutenberg_download.md).
  They are saved in a temporary directory by default, but they can be
  configured to persist in your OS-specific application cache directory
  across sessions ([@jrdnbradford](https://github.com/jrdnbradford),
  [\#112](https://github.com/ropensci/gutenbergr/issues/112),
  [\#123](https://github.com/ropensci/gutenbergr/issues/123)).
- A new family of `gutenberg_cache_*` functions are now available. These
  allow users to list and delete items in their cache, as well as update
  their cache type ([@jrdnbradford](https://github.com/jrdnbradford),
  [\#112](https://github.com/ropensci/gutenbergr/issues/112),
  [\#123](https://github.com/ropensci/gutenbergr/issues/123)).
- The package index reference in the pkgdown site now separates
  functions and data by type
  ([@jrdnbradford](https://github.com/jrdnbradford),
  [\#114](https://github.com/ropensci/gutenbergr/issues/114)).
- Jordan Bradford ([@jrdnbradford](https://github.com/jrdnbradford)) is
  now the primary maintainer of this package. Thanks for taking the
  lead, Jordan!
  ([\#95](https://github.com/ropensci/gutenbergr/issues/95)).

## gutenbergr 0.3.1

CRAN release: 2025-12-14

- The `language` column in `gutenberg_languages` is now properly merged
  with the `language` column
  ([\#94](https://github.com/ropensci/gutenbergr/issues/94)).
- The default mirror is now determined from the available mirrors in
  [`gutenberg_get_all_mirrors()`](https://docs.ropensci.org/gutenbergr/reference/gutenberg_get_all_mirrors.md),
  rather than trying to be clever and find a local mirror.
- All datasets have been updated as of 2025-12-14.

## gutenbergr 0.3.0

CRAN release: 2025-05-29

- [`gutenberg_download()`](https://docs.ropensci.org/gutenbergr/reference/gutenberg_download.md)
  tries the `.txt` version of files when the `.zip` is unavailable
  ([@jrdnbradford](https://github.com/jrdnbradford),
  [\#55](https://github.com/ropensci/gutenbergr/issues/55),
  [\#70](https://github.com/ropensci/gutenbergr/issues/70)).
- New function
  [`gutenberg_get_all_mirrors()`](https://docs.ropensci.org/gutenbergr/reference/gutenberg_get_all_mirrors.md)
  retrieves all mirror data
  ([@jrdnbradford](https://github.com/jrdnbradford),
  [\#58](https://github.com/ropensci/gutenbergr/issues/58)).
- The package infrastructure has been updated to make the package more
  robust and maintainable
  ([\#60](https://github.com/ropensci/gutenbergr/issues/60),
  [\#64](https://github.com/ropensci/gutenbergr/issues/64),
  [\#69](https://github.com/ropensci/gutenbergr/issues/69)).
- We now verify that the `gutenberg_mirror` `option` is a URL to a
  working Gutenberg mirror
  ([@jrdnbradford](https://github.com/jrdnbradford),
  [\#83](https://github.com/ropensci/gutenbergr/issues/83)).
- We now use the base R pipe (`|>`) in code and examples, not the
  magrittr pipe (`%>%`) ([@jonthegeek](https://github.com/jonthegeek),
  [\#75](https://github.com/ropensci/gutenbergr/issues/75)).
- Some fields (`gutenberg_languages$language`,
  `gutenberg_metadata$language`, and `gutenberg_metadata$rights`) are
  now factors to reduce object size.

## gutenbergr 0.2.4

CRAN release: 2023-11-12

- Update data scraping process to use R end-to-end
  ([@jonthegeek](https://github.com/jonthegeek),
  [\#36](https://github.com/ropensci/gutenbergr/issues/36)).

## gutenbergr 0.2.3 (2022-12-13)

CRAN release: 2022-12-14

- minor patches for broken urls to comply with CRAN checks.

## gutenbergr 0.2.2 (2022-12-03)

- Updated metadata
  ([\#32](https://github.com/ropensci/gutenbergr/issues/32),
  [\#29](https://github.com/ropensci/gutenbergr/issues/29))
- minor bug fixes and improvements, including removing broken url and
  updating documentation to comply with CRAN roxygen2 requirements
  ([\#30](https://github.com/ropensci/gutenbergr/issues/30),
  [\#31](https://github.com/ropensci/gutenbergr/issues/31),
  [\#35](https://github.com/ropensci/gutenbergr/issues/35),
  [\#28](https://github.com/ropensci/gutenbergr/issues/28)).
- Changed maintainer
  ([\#30](https://github.com/ropensci/gutenbergr/issues/30)).

## gutenbergr 0.2.0

CRAN release: 2020-09-22

- Changed to comply with CRAN policies for API packages. Tests that do
  connect to Project Gutenberg are skipped on CRAN, and are supplemented
  with tests that mock the connection.
- Added gutenberg_languages dataset with one-row-per-language-per-work,
  which substantially speeds up gutenberg_works.
- This adds a files argument to gutenberg_download that is generally
  used only for testing.
- Made changes to work with dplyr 1.0.0, removing filter\_ and
  distinct\_.
- Fixed links to https

## gutenbergr 0.1.5

CRAN release: 2019-09-10

- Make compatible with tidyr v1.0.0
- data_frame is deprecated, use tibble (thanks
  [@evanodell](https://github.com/evanodell) for
  [\#21](https://github.com/ropensci/gutenbergr/issues/21))
- rOpenSci updates to README (thanks
  [@maelle](https://github.com/maelle) for
  [\#23](https://github.com/ropensci/gutenbergr/issues/23))

## gutenbergr 0.1.4

CRAN release: 2018-01-26

- Added curl to SUGGESTS, since if it’s not installed
  [`readr::read_lines`](https://readr.tidyverse.org/reference/read_lines.html)
  could fail

## gutenbergr 0.1.3

CRAN release: 2017-06-19

- The Project Gutenberg mirror in Maryland Public Libraries
  (<http://www.gutenberg.lib.md.us>) has been broken for months. When it
  is provided from robot/harvest, replaces with
  `http://aleph.gutenberg.org`.
- Changed test of .zip capability not to run on CRAN
- Removed rvest dependency

## gutenbergr 0.1.2

CRAN release: 2016-06-24

- Made compatible with change to `distinct` in dplyr 0.5 (which is about
  to be submitted to CRAN)
- Removed xml2 dependency

## gutenbergr 0.1.1

CRAN release: 2016-05-16

- Transferred repo ownership to
  [ropenscilabs](https://github.com/ropenscilabs)
- The license was changed from MIT to GPL-2. This is based on the
  realization that the catalog data is licensed under the GPL, and the
  package includes a processed version of the catalog data. (See
  [here](https://www.gutenberg.org/ebooks/offline_catalogs.html)).
- Updated datasets to 5/5/2016 and added a “date_updated” attribute to
  tell when they were last updated
- Added `all_languages` and `only_languages` arguments to
  `gutenberg_works`, allowing fine-grained control of languages. (For
  example, “either English or French” or “both English and French”)
- Changed get_gutenberg_mirror to use xml2 directly, in order to handle
  AppVeyor
- Removed use of data() in `gutenberg_works`, since it slows down
  `gutenberg_works` about 2X
- Various documentation, vignette, and README adjustments in response to
  rOpenSci feedback.
- Added AppVeyor for Windows continuous integration
- Added code coverage information through codecov.io and covr, along
  with tests to improve coverage

## gutenbergr 0.1

CRAN release: 2016-05-03

- First version of package, including
  - `gutenberg_download` function, for downloading one or more works
    from Project Gutenberg using Gutenberg IDs
  - Datasets of Project Gutenberg metadata: `gutenberg_metadata`,
    `gutenberg_subjects`, `gutenberg_authors`
  - `gutenberg_works` function to retrieve filtered version of
    `gutenberg_metadata`
  - Introductory vignette including basic examples of downloading books
  - Unit tests for `gutenberg_download` and `gutenberg_works`
- Added a `NEWS.md` file to track changes to the package.
