# Check if a URL resolves to a working Gutenberg mirror

Checks for a root level `README` file at `url` with reference to
`GUTINDEX.ALL`. If this exists, `url` is most likely a working Gutenberg
mirror.

## Usage

``` r
is_working_gutenberg_mirror(url)
```

## Arguments

- url:

  An http(s) or ftp(s) URL to check.

## Value

Boolean: whether the `url` resolves to a mirror.
