# Delete specific files from the cache

Delete specific files from the cache

## Usage

``` r
gutenberg_cache_remove_ids(ids, verbose = TRUE)
```

## Arguments

- ids:

  A numeric or character vector of Gutenberg IDs to remove from the
  current cache.

- verbose:

  Whether to show the status messages.

## Value

The number of files successfully deleted (invisibly).

## Examples

``` r
if (FALSE) { # interactive()
# Remove specific books from cache
gutenberg_cache_remove_ids(c(1, 2))

# Remove silently
gutenberg_cache_remove_ids(1, verbose = FALSE)
}
```
