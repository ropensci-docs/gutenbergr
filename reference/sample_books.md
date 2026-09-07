# Sample Book Downloads

A
[`tibble::tibble()`](https://tibble.tidyverse.org/reference/tibble.html)
of book text for two sample books, generated using
[`gutenberg_download()`](https://docs.ropensci.org/gutenbergr/reference/gutenberg_download.md).

## Usage

``` r
data(sample_books)
```

## Format

A
[`tibble::tibble()`](https://tibble.tidyverse.org/reference/tibble.html)
with one row for each line of text from each book, with columns:

- gutenberg_id:

  Unique identifier for the work that can be used to join with the
  [gutenberg_metadata](https://docs.ropensci.org/gutenbergr/reference/gutenberg_metadata.md)
  dataset.

- text:

  A character vector of lines of text.

- title:

  The title of this work.

- author:

  The author of this work.

## Details

This code was used to download the books:
`gutenberg_download(c(109, 105), meta_fields = c("title", "author"))`
