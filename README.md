# spark-micro -- spark inside micro

A plugin for the [micro](https://micro-editor.github.io) editor that puts
[spark](https://spark.forgewright.ai) -- your own AI, on your own machine
-- under one key. `Alt-s` (Option-s on a Mac) opens a `spark> ` prompt:

    (nothing) Enter    complete at the cursor
    words              rewrite the selection, or the whole file
    ? words            ask about it, in a pane on the right
    ?                  review: notes, each quote checked against your text
    ?? words           go on in the newest pane's thread
    ledger [clear]     the notes you declined for this file

The new text is left selected: a proposal, never applied silently.
`help spark` inside micro says the rest.

## Install

You need spark 1.7 or newer on this machine (`spark edit -h` answers), and
micro 2.0.7 or newer. Then:

```sh
git clone https://github.com/forgewright-ai/spark-micro ~/.config/micro/plug/spark
```

and one line in `~/.config/micro/bindings.json` (create it if absent):

```json
{
    "Alt-s": "lua:spark.prompt"
}
```

The plugin binds no key by itself: a rebind from inside makes micro rewrite
`bindings.json`. Update with `git -C ~/.config/micro/plug/spark pull`.
Not yet in micro's plugin channel; when it is, `micro -plugin install spark`
does the same.

## Options

- `spark.about` -- what the author says the text is, when spark should not
  guess: `setlocal spark.about "a novel chapter"`, or per folder in
  `settings.json`: `"*/Manuscripts/*.md": {"spark.about": "a novel chapter"}`.
- `spark.bin` -- the spark binary (default: `SPARK_BIN`, then
  `~/.local/bin/spark`, then `PATH`).
- `set spark false` switches the plugin off.
- `MICRO_TRUECOLOR=1` in your shell lets micro draw spark's palette when
  `spark shell on` has rendered its colorscheme.

## What leaves this machine

The file's name and its text -- 6 kB around the cursor for a completion,
12 kB for a rewrite, 16 kB for a question -- never its path, and only to
the brain spark is configured for. Every run is one call to `spark edit`
with the text on stdin; the plugin never speaks HTTP and never sees a
token. spark's README says the rest.

## Contributing

`git config core.hooksPath .githooks` once; the hook keeps the tree free of
private names, ASCII, and syntax-clean. `python3 tests/micro_pty.py` drives
a real micro in a pty against a stub spark (skips without micro). Another
editor joins spark the same way this one does: one client of `spark edit`,
in its own repo.

MIT. Credits in `CREDITS.md`. Built with Claude.
