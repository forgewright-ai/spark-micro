# Changelog

## Unreleased

- CI runs the pty test on Arch too (micro from pacman, in a container).

## 1.4.0

- Its own home: the plugin moved out of the spark repository, where it
  shipped under `spark shell on` since spark v1.5. Install is a clone into
  `~/.config/micro/plug/spark` and one binding line; spark installs no
  editor and no plugin any more (spark v1.10).
- The pty test came along (`tests/micro_pty.py`), with its own CI on Ubuntu
  and macOS.

## 1.3.0 and before

Shipped inside spark: 1.0.0 with spark v1.5 (the prompt, complete, rewrite,
ask), 1.1.0 and 1.2.0 with v1.7 (the pane and its keys, `?? words`,
`--sel`, the thread), 1.3.0 with v1.7 (`ledger`, a Lua error is an infobar
line). spark's `CHANGELOG.md` has the detail.
