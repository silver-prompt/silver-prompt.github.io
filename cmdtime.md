# `cmdtime`

![cmdtime](assets/cmdtime.png)

This module displays the time it took the last command to complete.
This module is not available on Bash.

## TOML

### `cmdtime_threshold`

The minimum duration of time to show the segment. For example, with the value of
`1s`, if the command took 500ms, the segment would not show, but if the command
took one second or more, the segment would show.

Suffixes include `ms` for milliseconds, `s` for seconds, `m` for minutes,
`h` for hours, and `d` for days. For example, a threshold value of `1d2h3m4s5ms`
would only display the command time if it took at least 1 day, 2 hours,
3 minutes, 4 seconds, and 5 milliseconds.
