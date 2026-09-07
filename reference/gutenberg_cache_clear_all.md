# Clear all files from the Gutenberg cache

Deletes all cached `.rds` files in the directory currently returned by
[`gutenberg_cache_dir()`](https://docs.ropensci.org/gutenbergr/reference/gutenberg_cache_dir.md).

## Usage

``` r
gutenberg_cache_clear_all(verbose = TRUE)
```

## Arguments

- verbose:

  Whether to show the status message confirming the path.

## Value

The number of files deleted (invisibly).

## Examples

``` r
if (FALSE) { # interactive()
# Clear entire current cache
gutenberg_cache_clear_all()
}
```
