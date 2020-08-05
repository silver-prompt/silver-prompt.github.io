# `dir`

![dir](assets/dir.png)

This module displays the current working directory.
If you are in your home directory, it is replaced with a home icon.

## TOML

### `dir.aliases`

This dictionary defines icon aliases for directories.
For example, if you wanted to replace `~/go/src` with `\ue627`, you would write

```toml
[dir.aliases]
"\ue627" = "~/go/src"
```

### `dir.length`

This variable defines the maximum amount of Unicode characters that are allowed
in the directory. The last directory is not affected.

Example with a value of `1`:

![shortdir](assets/shortdir.png)
