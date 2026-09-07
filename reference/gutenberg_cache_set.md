# Set the Gutenberg cache type

Configures whether the cache should be temporary (per-session) or
persistent across sessions.

## Usage

``` r
gutenberg_cache_set(
  type = getOption("gutenbergr_cache_type", "session"),
  verbose = TRUE
)
```

## Arguments

- type:

  Either `"session"` (default) or `"persistent"`.

  - `"session"`: Files are stored in a
    [`tempdir()`](https://rdrr.io/r/base/tempfile.html). This is the
    default behavior.

  - `"persistent"`: Files are stored in an OS-specific user cache
    directory under `works_rds/`. These files persist across sessions,
    preventing redundant downloads of the same files in the future.

- verbose:

  Whether to show the status message confirming the path.

## Value

The active cache path (invisibly).

## Cache options

The following options control caching behavior:

- `gutenbergr_cache_type`: Character string indicating how downloaded
  works are cached. Must be either `"session"` (default) or
  `"persistent"`.

- `gutenbergr_base_cache_dir`: Base directory used for persistent
  caching when `gutenbergr_cache_type = "persistent"`.

  By default, this is an OS-specific cache directory determined by
  `tools::R_user_dir("gutenbergr", "cache")`. Advanced users may set
  this to a custom path.

## Examples

``` r
if (FALSE) { # interactive()
# Set to persistent (survives R sessions)
gutenberg_cache_set("persistent")

# Set back to session cache (temporary)
gutenberg_cache_set("session")

# Check current cache location
gutenberg_cache_dir()
}
```
