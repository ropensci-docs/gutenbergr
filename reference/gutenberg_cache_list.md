# List files in the Gutenberg cache

Provides a detailed list of files currently stored in the directory
returned by
[`gutenberg_cache_dir()`](https://docs.ropensci.org/gutenbergr/reference/gutenberg_cache_dir.md).

## Usage

``` r
gutenberg_cache_list(verbose = TRUE)
```

## Arguments

- verbose:

  Whether to show the status message showing the cache directory path.

## Value

A
[`tibble::tibble()`](https://tibble.tidyverse.org/reference/tibble.html)
with the following columns:

- title:

  The title of the work.

- author:

  The author(s) of the work.

- file:

  The filename.

- size_mb:

  Size of the file in megabytes.

- modified:

  The last modification time.

- path:

  The file's absolute path.

## Examples

``` r
if (FALSE) { # interactive()
# List all works in the currently set cache
gutenberg_cache_list()

# Suppress the directory path message
gutenberg_cache_list(verbose = FALSE)
}
```
