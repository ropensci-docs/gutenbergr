# Construct a Project Gutenberg path from an ID

Construct a Project Gutenberg path from an ID

## Usage

``` r
gutenberg_path_from_id(gutenberg_id)
```

## Arguments

- gutenberg_id:

  A vector of Project Gutenberg IDs, or a data frame containing a
  `gutenberg_id` column, such as from the results of
  [`gutenberg_works()`](https://docs.ropensci.org/gutenbergr/reference/gutenberg_works.md).

## Value

A character vector of paths.
