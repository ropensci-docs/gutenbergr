# Gutenberg metadata about the subject of each work

Gutenberg metadata about the subject of each work, particularly Library
of Congress Classifications (lcc) and Library of Congress Subject
Headings (lcsh).

## Usage

``` r
data(gutenberg_subjects)
```

## Format

A
[`tibble::tibble()`](https://tibble.tidyverse.org/reference/tibble.html)
with one row for each pairing of work and subject, with columns:

- gutenberg_id:

  ID describing a work that can be joined with
  [gutenberg_metadata](https://docs.ropensci.org/gutenbergr/reference/gutenberg_metadata.md)

- subject_type:

  Either "lcc" (Library of Congress Classification) or "lcsh" (Library
  of Congress Subject Headings)

- subject:

  Subject

## Details

Find more information about Library of Congress Categories here:
<https://www.loc.gov/catdir/cpso/lcco/>, and about Library of Congress
Subject Headings here: <https://id.loc.gov/authorities/subjects.html>.

To find the date on which this metadata was last updated, run
`attr(gutenberg_subjects, "date_updated")`.

## See also

[gutenberg_metadata](https://docs.ropensci.org/gutenbergr/reference/gutenberg_metadata.md),
[gutenberg_authors](https://docs.ropensci.org/gutenbergr/reference/gutenberg_authors.md)

## Examples

``` r
if (FALSE) { # interactive()

library(dplyr)
library(stringr)

gutenberg_subjects |>
  filter(subject_type == "lcsh") |>
  count(subject, sort = TRUE)

sherlock_holmes_subjects <- gutenberg_subjects |>
  filter(str_detect(subject, "Holmes, Sherlock"))

sherlock_holmes_subjects

sherlock_holmes_metadata <- gutenberg_works() |>
  filter(author == "Doyle, Arthur Conan") |>
  semi_join(sherlock_holmes_subjects, by = "gutenberg_id")

sherlock_holmes_metadata

# \donttest{
holmes_books <- gutenberg_download(sherlock_holmes_metadata$gutenberg_id)

holmes_books
# }

# See date last updated
attr(gutenberg_subjects, "date_updated")
}
```
