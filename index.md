# Quick overview

## Subcommands

### `init`

This subcommand outputs shell script to be evaluated by your shell on startup.
Silver detects your shell by looking on the shell process name.

### `lprint`, `rprint`

These subcommands shouldn't be called by the user, but by the code `init` generates.
They output the left and right prompt respectively.

## Config structure

### `left`, `right`

These arrays contain every module, in order, you want in your left or right prompt
respectively. The elements in these arrays are dictionaries with keys
`name` - module name, `color` - dictionary with keys `background` and
`foreground` - segment background and foreground, and `args` - array of additional
parameters.

For example, if you wanted the `dir` module with black text on a blue background,
the element would be:

```toml
name = "dir"
color.background = "blue"
color.foreground = "black"
```

### `separator`

This dictionary has keys `right` and `left`, which in turn have keys `thin` and `thick`.
They are the separators between segments in left and right prompt respectively.
Thick separators are placed between segments of different background color and
thin - between segments of the same background color. The default values is

```toml
[separator.left]
thick = "\ue0b0"
thin = "\ue0b1"

[separator.right]
thick = "\ue0b2"
thin = "\ue0b3"
```

Example with `separator.left.thick = "\ue0b4"`:<br/>
![e0b4](e0b4.png)

Example with `separator.left.thick = "\ue0bc"`:<br/>
![e0bc](e0bc.png)

Thin separator example:<br/>
![thin-separator](thin-separator.png)

### `icon_set`

This string is a preset of every icon. Valid values are `nerd`, `unicode`, or `ascii`.
It defaults to `nerd`. For more information, see [Icons](#icons).

## Modules

* [OS](OS)
* [Status](Status)
* [User](User)
* [Directory](Directory)
* [Git](Git)
* [Command Time](Command-Time)
* [Time](Time)
* [Environment Variable](Environment-Variable)
* [virtualenv](virtualenv)
* [Conda](conda)

## Icons

Every icon is completely customizable through TOML.

There are three presets for icons (which can be set through [`icon_set`](#silver_icons)):

* `nerd` uses icons from [Nerd Fonts](https://github.com/ryanoasis/nerd-fonts)
* `unicode` uses Unicode (mostly emojis)
* `ascii` uses only ASCII

The default preset is `nerd`, but each individual icon can be set with TOML.
The variable to set is `icons.[icon name]`. For example, if you wanted to set the
`failed` icon to "&#x2717;", you would set `icons.failed` to `"\u2717"`.

Every icon name can be found on the appropriate module wiki page.

## Example configurations

`~/.config/silver/silver.toml`:

```toml
[[left]]
name = "dir"
color.background = "blue"
color.foreground = "black"

[[left]]
name = "git"
color.background = "green"
color.foreground = "black"

[[right]]
name = "status"
color.background = "white"
color.foreground = "black"

[[right]]
name = "cmdtime"
color.background = "magenta"
color.foreground = "black"

[[right]]
name = "shell"
color.background = "green"
color.foreground = "black"
```

`~/.bashrc`/`~/.zshrc`:

```sh
source <(silver init)
```

`~/.config/fish/config.fish`:

```fish
silver init | source
```

`~/.config/ion/initrc`:

```sh
eval $(silver init)
```
