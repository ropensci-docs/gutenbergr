# Metadata about Project Gutenberg languages

Data frame with metadata about the languages of each Project Gutenberg
work.

## Usage

``` r
data(gutenberg_languages)
```

## Format

A
[`tibble::tibble()`](https://tibble.tidyverse.org/reference/tibble.html)
with one row for each work-language pair, with the columns:

- gutenberg_id:

  Unique identifier for the work that can be used to join with the
  [gutenberg_metadata](https://docs.ropensci.org/gutenbergr/reference/gutenberg_metadata.md)
  dataset

- language:

  Language ISO 639 code. Two letter code if one exists, otherwise three
  letter.

- total_languages:

  Number of languages for this work.

## Details

To find the date on which this metadata was last updated, run
`attr(gutenberg_languages, "date_updated")`.

## See also

[gutenberg_metadata](https://docs.ropensci.org/gutenbergr/reference/gutenberg_metadata.md),
[gutenberg_subjects](https://docs.ropensci.org/gutenbergr/reference/gutenberg_subjects.md)

## Examples

``` r

# See date last updated
attr(gutenberg_languages, "date_updated")
#> [1] "2026-06-25"
```
