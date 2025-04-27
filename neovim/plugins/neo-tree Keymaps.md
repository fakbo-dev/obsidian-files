references: [[Neovim Commands]]
### Global Keymaps
- `\` -> Reveal Neo-tree
- `<leader>e` -> Toggle file explorer (left position)
- `<leader>ngs` -> Open floating git status window

### Neo-tree Keymaps (When Focused)
#### Navigation
- `<space>` -> Toggle node expansion
- `<2-LeftMouse>` -> Open file/directory
- `<cr>` -> Open file/directory
- `<bs>` -> Navigate up directory (filesystem)
- `.` -> Set current directory as root

#### File Operations
- `a` -> Add file/folder
- `A` -> Add directory
- `d` -> Delete file/folder
- `r` -> Rename file/folder
- `y` -> Copy to clipboard
- `x` -> Cut to clipboard
- `p` -> Paste from clipboard
- `c` -> Copy file/folder
- `m` -> Move file/folder

#### Window Management
- `S` -> Open in horizontal split
- `s` -> Open in vertical split
- `t` -> Open in new tab
- `w` -> Open with window picker
- `P` -> Toggle preview (floating window)
- `q` -> Close Neo-tree window

#### View Customization
- `z` -> Close all nodes
- `C` -> Close current node
- `R` -> Refresh tree
- `H` -> Toggle hidden files (filesystem)
- `/` -> Fuzzy finder
- `<c-x>` -> Clear current filter

#### Git Integration
- `[g` -> Previous git modified file
- `]g` -> Next git modified file
- `ga` -> Git add file
- `gu` -> Git unstage file
- `gr` -> Git revert file
- `gc` -> Git commit
- `gp` -> Git push
- `gg` -> Git commit & push

#### Sorting Options (Press `o` first)
- `oc` -> Order by created
- `od` -> Order by diagnostics
- `og` -> Order by git status
- `om` -> Order by modified
- `on` -> Order by name
- `os` -> Order by size
- `ot` -> Order by type

### Buffer Management
- `bd` -> Delete buffer (when in buffers source)
- `[g` -> Previous git modified buffer
- `]g` -> Next git modified buffer

### Preview Mode
- `P` -> Toggle floating preview
- `<esc>` -> Close preview/float


