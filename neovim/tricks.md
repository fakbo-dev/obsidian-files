realtion: [[Neovim Commands]]
## highlight things
`vi'` -> highlight the first occurence in a quote
## Select within () and {}

`vi{ || vi(` -> larger
`vib` -> for () shorter
`viB` -> for {} shorter
`cib` -> change all in () and enter in insert mode
`ciB` -> change all in {} and enter in insert mode
## Edit multiple lines at Once
`C-v && I [text] ESC`
## re-highlight last highlighted
`gv && $ $$ A [Text] ESC`

## Toggle Case with ~ and g~
`~` -> Capitalize/Lower a letter
`g~w` -> Capitalize/Lower a letter
`g~it` -> for everithing between a tag

## Re-Ident the whole File
`gg=^g`

## Jump Between (), [], {} etc
`f(` -> jump to the first (
`f[` -> jump to the first [
`f{` -> jump to the first {
`f'` -> jump to the first '
`f"` -> jump to the first "
`%` -> jump between 
## Put vim in the background

`C-Z` go back to the terminal without close vim
`fg` -> to go to neovim again

## Open URL in the browser
`gx` -> open the url in the default browser

## Go to a local file
`gf` -> open the local file

## Mark Location and return to it
`m[word]` -> create a Local mark
`'[word]` -> go to the mark in local file
`m[^word]` -> create a global mark
`'[^word]` -> go to the mark in global files