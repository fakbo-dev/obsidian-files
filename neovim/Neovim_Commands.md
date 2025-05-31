---
id: Neovim Commands
aliases: []
tags: []
---

`:Tutor` -> Get in to the Tutorial for neovim
`:help` -> get the all the commands

## Move the cursor

In normal Mode
`h` -> Left
`l` -> Right
`j` -> down
`k` -> up

          ↑
          k         Hint: The `h`{normal} key is at the left and moves left.
     ← h    l →           The `l`{normal} key is at the right and moves right.
         j                The `j`{normal} key looks like a down arrow.
         ↓

## Exit Neovim

`:q` -> quit Neovim (give an option to save or quit whitout save the file)
`:q!` -> quit neovim and discard all the changes
`wq` -> safe the changes in the file and quit

## DELETE

Many commands that change text are made from an (operator) and a (navigation).
The format for a delete command with the (d) delete operator is as follows:

    d   motion

Where:
d - is the delete operator.
motion - is what the operator will operate on (listed below).

A short list of motions:
(w) - until the start of the next word, EXCLUDING its first character.
(e) - to the end of the current word, INCLUDING the last character.
($) - to the end of the line, INCLUDING the last character.

Thus typing `de`{normal} will delete from the cursor to the end of the word.

`x` -> delete the character under the cursor
`dw` -> delete a word in the cursor
`d$` -> delete to the end of the line.
`d[number]w` -> delete `[number]` words
`dd` -> delete the whole line
`[number]dd` -> delete `[number]` lines

# Text editing: INSERTION

`i` -> enter in insertion mode before the cursor
`I` -> enter in insertion mode at the beginning of the line
`a` -> enter in insertion mode after the cursor
`A` -> enter in the insertion mode at the end of the line
`o` -> enter in the insertion mode in te next line
`O` -> enter in the insertion mode in the current line and push down the old line

## Using a count for a motion

Typing a number before a motion repeats it that many times.

`[number]w` -> move the cursor `[number]` words forward.
`[number]e` -> to move the cursor to the end of the `[number]` word forward.
`0` -> move to the start of the line

## UNDO COMMAND

`u` -> undo the last commands
`U` -> to fix the whole line
`crtl + r` -> to undo the undos

## PUT COMMANDS

`p` -> put previously deleted text after the cursor.
`P` -> put previously deleted text before the cursor

## REPLACE COMMAND

`r[word]` -> replace the character at the cursor with `[word]`
`R[word]` -> to replace more than one character

## Change Operator

`C [number] motion`

`ce` -> change until the end of a word
cw -> change the current word
`c$` -> change the word after the cursor

## Cursor location and file status

`ctrl + g` -> show your location in a file and the file status.
`gg` -> go to the beggining of the file
`G` -> go tho the end of the file
`[number]G` go to the `[number]` line

## THE SEARCH COMMAND

`/` -> followed by a phrase to search for the phrase
`n` -> search for the same phrase again
`N` -> search for the same phrase in opposite direction
`?` -> search for a phrasein the backward direction
`crtl + o` -> go back where you came from
`crtl + i` -> to go back further

## Matching parentheses search

`%` -> to find a matching ), ], }.

## THE SUBSTITUDE COMMAND

4.  To substitute new for the first old in a line type

```cmd
        :s/old/new
```

    To substitute new for all olds on a line type

```cmd
        :s/old/new/g
```

    To substitute phrases between two line #'s type

```cmd
        :#,#s/old/new/g
```

    To substitute all occurrences in the file type

```cmd
        :%s/old/new/g
```

    To ask for confirmation each time add 'c'

```cmd
        :%s/old/new/gc
```

## HOW TO EXECUTE AN EXTERNAL COMMAND

`:!` -> followed by an external command to execute that command
`:w` -> safe the changes in the file
`:w FILENAME` ->save change
`:!dir` -> list the folders in the current workstate
`:!del FILENAME` -> delete a file from neovim

## SELECTING TEXT TO WRITE

## RETRIEVING AND MERGIN FILES

`:r FILENAME` -> retrieve the contentsof a file
`:r !dir` -> reads the output of the ls commandand puts it below the cursor.

1.  :!command executes an external command.

    Some useful examples are:
    `:!dir`{vim} - shows a directory listing
    `:!del FILENAME`{vim} - removes file FILENAME

2.  (:w) FILENAME writes the current Neovim file to disk with
    name FILENAME.

3.  (v) motion :w FILENAME saves the Visually selected lines in file
    FILENAME.

4.  (:r) FILENAME retrieves disk file FILENAME and puts it
    below the cursor position.

5.                     reads the output of the dir command and
                             puts it below the cursor position.

## COPY AND PASTE TEXT

`y` -> copy a text
`y[word]` copy a word
`p` -> paste a text
`P` -> paste before the cursor

## SET OPTION

6.  Typing "(:set) xxx" sets the option "xxx". Some options are:

        'ic' 'ignorecase'   ignore upper/lower case when searching
        'is' 'incsearch'    show partial matches for a search phrase
        'hls' 'hlsearch'    highlight all matching phrases

    You can either use the long or the short option name.

7.  Prepend "no" to switch an option off:

```cmd
        :set noic
```

8.  Prepend "inv" to invert an option:

```cmd
        :set invic
```
