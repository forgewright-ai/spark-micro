# micro with spark -- the cheatsheet

micro edits; spark writes with you. Section 1 is micro on its own,
section 2 is the one key that puts your own AI inside it.

The key spellings here are the editor's: `Alt-s` is Option-s on a Mac
(spark's Terminal profile makes Option the Meta key), or Esc and then
s, quickly. `Ctrl-q` means hold Ctrl and press q.

## 1. micro, the basics

Files

    Ctrl-s         save
    Ctrl-o         open a file
    Ctrl-q         quit (asks when unsaved)
    Ctrl-t         new tab; Alt-, and Alt-. switch tabs

Editing

    Ctrl-z         undo         Ctrl-y   redo
    Shift-arrows   select       Ctrl-a   select all
    Ctrl-c         copy         Ctrl-x   cut
    Ctrl-v         paste        Ctrl-k   cut this line

Finding

    Ctrl-f         find -- then Ctrl-n next match, Ctrl-p previous

The editor itself

    Ctrl-e         the command bar (goto 42, help spark, ...)
    Ctrl-w         jump between splits
    Ctrl-g         micro's own help

## 2. the text, with spark

One key: Alt-s. The `spark> ` prompt opens at the bottom; what you
type there decides what happens. A rewrite comes back selected -- a
proposal, never applied silently. Answers open in a pane on the
right; the pane is read-only and single keys act there.

    (nothing) Enter  complete at the cursor -- end your text with a
                     space or a new line first
    words            rewrite the selection (or the whole file):
                     select the whole unit you mean, not a word of it
    ? words          ask about the selection, in a pane
    ?                review: quoted notes, each checked against your
                     text -- an invented one says [not in the text]
    ?? words         go on in the newest pane's thread
    ledger [clear]   the notes you declined for this file
    Ctrl-z           undo any applied rewrite; Backspace drops a
                     fresh completion

In a spark pane

    q or Esc         close the pane
    Enter            jump to this note's quote in your file
    a                apply the code block under the cursor
    d                decline this note: the next review of this file
                     is told not to raise it again

By example

    fix grammar               rewrite the selection, grammar only
    shorter                   the same text, tighter
    translate to Portuguese   the selection, in Portuguese
    ? is the title too long   a question, answered in a pane
    ?                         review before you call it done

The same from the command bar (Ctrl-e): `spark shorter`,
`spark ? why`. Tell spark what the text is when it should not guess:
`setlocal spark.about "a novel chapter"`. `help spark` inside micro
says the rest.
