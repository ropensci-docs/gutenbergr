# Get a filtered table of Gutenberg work metadata

Get a table of Gutenberg work metadata that has been filtered by some
common (settable) defaults, along with the option to add additional
filters. This function is for convenience when working with common
conditions when pulling a set of books to analyze. For more detailed
filtering of the entire Project Gutenberg metadata, use the
[gutenberg_metadata](https://docs.ropensci.org/gutenbergr/reference/gutenberg_metadata.md)
and related datasets.

## Usage

``` r
gutenberg_works(
  ...,
  languages = "en",
  only_text = TRUE,
  rights = c("Public domain in the USA.", "None"),
  distinct = TRUE,
  all_languages = FALSE,
  only_languages = TRUE
)
```

## Arguments

- ...:

  Additional filters, given as expressions using the variables in the
  [gutenberg_metadata](https://docs.ropensci.org/gutenbergr/reference/gutenberg_metadata.md)
  dataset (e.g. `author == "Austen, Jane"`).

- languages:

  Vector of languages to include.

- only_text:

  Whether the works must have Gutenberg text attached. Works without
  text (e.g. audiobooks) cannot be downloaded with
  [`gutenberg_download()`](https://docs.ropensci.org/gutenbergr/reference/gutenberg_download.md).

- rights:

  Values to allow in the `rights` field. By default allows public domain
  in the US or "None", while excluding works under copyright. `NULL`
  allows any value of Rights.

- distinct:

  Whether to return only one distinct combination of each title and
  `gutenberg_author_id`. If multiple occur (that fulfill the other
  conditions), it uses the one with the lowest ID.

- all_languages:

  Whether, if multiple languages are given, all of them need to be
  present in a work. For example, if `c("en", "fr")` are given, whether
  only `en/fr` as opposed to English or French works should be returned.

- only_languages:

  Whether to exclude works that have other languages besides the ones
  provided. For example, whether to include `en/fr` when English works
  are requested.

## Value

A
[`tibble::tibble()`](https://tibble.tidyverse.org/reference/tibble.html)
with one row for each work, in the same format as
[gutenberg_metadata](https://docs.ropensci.org/gutenbergr/reference/gutenberg_metadata.md).

## Details

By default, returns:

- English-language works.

- Works that are in text format in Gutenberg (as opposed to audio).

- Works whose text is not under copyright.

- At most one distinct field for each title/author pair.

## Examples

``` r
if (FALSE) { # interactive()
library(dplyr)

# Default: English, text-based, public domain works
gutenberg_works()

# Filter conditions using ...
gutenberg_works(author == "Shakespeare, William")

# Language specifications
gutenberg_works(languages = "es") |>
  count(language, sort = TRUE)

# Filter for works that are specifically English AND French
gutenberg_works(languages = c("en", "fr"), all_languages = TRUE)
}
```
