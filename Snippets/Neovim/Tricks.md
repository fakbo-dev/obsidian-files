# Tricks

**Domain**:: #editor #neovim
**Expertise**:: ` 🚀 Advanced`
**Last Used**:: 2025-05-31
**Related**:: [[Snippets|snippets]]
**Tags**:: #cheatsheet #reference #neovim #tricks

## Core Syntax & Operations

```vim
" Yank entire file
:ygg  " Yank from top to cursor
:yG   " Yank from cursor to bottom

" Jump between brackets
%     " Jump between matching (), [], {}
f(    " Jump to next '('
f[    " Jump to next '['

" Find operations
f<char>  " Find next occurrence of char
F<char>  " Find previous occurrence of char
;        " Repeat last find
,        " Repeat last find backward
```

## Productivity Shortcuts

```vim
" Text objects
vi'    " Select inside single quotes
vi"    " Select inside double quotes
vib    " Select inside parentheses ()
viB    " Select inside braces {}
ciB    " Change inside braces and enter insert mode

" Case toggling
~      " Toggle case of current character
g~w    " Toggle case of current word
g~it   " Toggle case inside HTML tag
```

## Common Patterns

### Basic Usage

```vim
" Visual block editing
Ctrl-v  " Enter visual block mode
I       " Insert text at beginning of selection
A       " Append text at end of selection

" Re-select previous visual selection
gv      " Reselect last visual selection
$       " Extend to end of line
```

### Composite Workflow

```vim
" Format entire file
gg=G  " Reindent entire file

" Edit multiple lines simultaneously
Ctrl-v  " Select block
j/k     " Move down/up
I       " Insert mode
[text]  " Type text
Esc     " Apply to all lines
```

## Debugging Guide

```vim
" Common issue: Marks not working
:marks  " List all marks

" URL not opening?
:checkhealth  " Verify netrw configuration
```

## Real-World Examples

### Navigation Workflow

```vim
" Mark current position
ma     " Set mark 'a'
'      " Go to mark (normal mode)
`      " Go to exact mark position

" Global marks (work across files)
mA     " Set global mark 'A'
'A     " Jump to global mark 'A'
```

### Editing Workflow

```vim
" Change content inside brackets
ci(    " Change inside ()
ci[    " Change inside []
ci{    " Change inside {}
```

## Advanced Techniques

```vim
" Terminal control
Ctrl-z  " Suspend Neovim (return to terminal)
fg      " Resume Neovim

" Open resources
gx      " Open URL under cursor
gf      " Open local file under cursor
```

## Configuration Snippets

### Minimal Setup

```lua
-- Enable advanced text objects
vim.g.textobj_entire_no_mappings = 1
vim.cmd[[
  omap ae <Plug>(textobj-entire-a)
  omap ie <Plug>(textobj-entire-i)
]]
```

### Optimized Setup

```lua
-- Enhanced jump to character
vim.keymap.set('n', 'f', "<cmd>lua require('hop').hint_char1()<CR>", {})
vim.keymap.set('n', 'F', "<cmd>lua require('hop').hint_char1({ direction = require'hop.hint'.HintDirection.BEFORE_CURSOR })<CR>", {})
```

## Cross-Tool Integration

```lua
-- Open URLs with browser
vim.keymap.set('n', 'gx', '<cmd>!xdg-open <cfile><CR>', { silent = true })

-- Open local files with telescope
vim.keymap.set('n', 'gf', '<cmd>Telescope find_files<CR>', {})
```

## Version-Specific Notes

| Version | Changes              | Compatibility |
| ------- | -------------------- | ------------- |
| 0.7+    | Improved textobjs    | Lua plugins   |
| 0.9+    | Better terminal mgmt | All systems   |

## Pro Tips

```vim
" Center screen after jumps
:nnoremap n nzz
:nnoremap N Nzz

" Keep cursor position when joining lines
:nnoremap J mzJ`z

" Persistent marks across sessions
:set viminfo+=!  " Save global marks
```

> **Remember**: Use `:h text-objects` to discover more editing targets

## Reference Links

1. [Neovim Text Objects Guide](https://neovim.io/doc/user/motion.html#text-objects)
2. [Advanced Vim Movements](https://github.com/phaazon/hop.nvim)
3. [Neovim Productivity Tips](https://github.com/mhinz/vim-galore)

---

### Complete Tricks Reference

```markdown
## Editing Magic

- `ci"` - Change inside double quotes
- `ciw` - Change entire word
- `cis` - Change entire sentence
- `vip` - Select entire paragraph

## Navigation Tricks

- `H` - Top of screen
- `M` - Middle of screen
- `L` - Bottom of screen
- `zz` - Center cursor line
- `Ctrl-o` - Jump back to previous position
- `Ctrl-i` - Jump forward

## Visual Mode Tricks

- `o` - Move to other end of selection
- `U` - Uppercase selection
- `u` - Lowercase selection
- `~` - Toggle case

## Command Line Magic

- `:saveas %:h/newfile` - Save in new directory
- `:r !date` - Insert current date
- `:!python %` - Execute current file
```

### Mark Mastery

```markdown
| Command  | Description                    |
| -------- | ------------------------------ |
| `m[a-z]` | Set local mark in current file |
| `m[A-Z]` | Set global mark across files   |
| `'mark`  | Jump to mark line              |
| ``mark`  | Jump to exact mark position    |
| `:marks` | List all marks                 |
```
