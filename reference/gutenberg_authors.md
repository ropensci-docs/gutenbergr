# Metadata about Project Gutenberg authors

Data frame with metadata about each author of a Project Gutenberg work.
Although the Project Gutenberg raw data also includes metadata on
contributors, editors, illustrators, etc., this dataset contains only
people who have been the single author of at least one work.

## Usage

``` r
data(gutenberg_authors)
```

## Format

A
[`tibble::tibble()`](https://tibble.tidyverse.org/reference/tibble.html)
with one row for each author, with the columns:

- gutenberg_author_id:

  Unique identifier for the author that can be used to join with the
  [gutenberg_metadata](https://docs.ropensci.org/gutenbergr/reference/gutenberg_metadata.md)
  dataset

- author:

  The `agent_name` field from the original metadata

- alias:

  Alias

- birthdate:

  Year of birth

- deathdate:

  Year of death

- wikipedia:

  Link to Wikipedia article on the author. If there are multiple, they
  are "\|"-delimited

- aliases:

  Character vector of aliases. If there are multiple, they are
  "/"-delimited

## Details

To find the date on which this metadata was last updated, run
`attr(gutenberg_authors, "date_updated")`.

## See also

[gutenberg_metadata](https://docs.ropensci.org/gutenbergr/reference/gutenberg_metadata.md),
[gutenberg_subjects](https://docs.ropensci.org/gutenbergr/reference/gutenberg_subjects.md)

## Examples

``` r

# See date last updated
attr(gutenberg_authors, "date_updated")
#> [1] "2026-06-25"
```
