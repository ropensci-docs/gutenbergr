# Construct a Project Gutenberg url

Construct a Project Gutenberg url

## Usage

``` r
gutenberg_url(gutenberg_id, mirror, verbose)
```

## Arguments

- gutenberg_id:

  A vector of Project Gutenberg IDs, or a data frame containing a
  `gutenberg_id` column, such as from the results of
  [`gutenberg_works()`](https://docs.ropensci.org/gutenbergr/reference/gutenberg_works.md).

- mirror:

  A mirror URL to retrieve the books from. By default uses the mirror
  from
  [`gutenberg_get_mirror()`](https://docs.ropensci.org/gutenbergr/reference/gutenberg_get_mirror.md).

- verbose:

  Whether to show messages about the Project Gutenberg mirror that was
  chosen.

## Value

A named character vector of urls.
