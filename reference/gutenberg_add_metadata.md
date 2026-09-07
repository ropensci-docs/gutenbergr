# Join metadata fields to Gutenberg works

Join metadata fields to Gutenberg works

## Usage

``` r
gutenberg_add_metadata(gutenberg_tbl, meta_fields)
```

## Arguments

- gutenberg_tbl:

  A two column `tbl_df` from
  [`gutenberg_download()`](https://docs.ropensci.org/gutenbergr/reference/gutenberg_download.md).

- meta_fields:

  Additional fields describing each book, such as `title` and `author`,
  to add from
  [gutenberg_metadata](https://docs.ropensci.org/gutenbergr/reference/gutenberg_metadata.md).

## Value

A `tbl_df` of the Gutenberg works with joined metadata.
