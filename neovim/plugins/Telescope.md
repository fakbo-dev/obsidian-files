Reference [[Neovim Commands]]
## Telescope Keymaps

### Global Keymaps
- `<leader>sh` -> Search help tags
- `<leader>sk` -> Search keymaps
- `<leader>sf` -> Search files (including hidden)
- `<leader>ss` -> Select Telescope built-in pickers
- `<leader>sw` -> Search current word
- `<leader>sg` -> Live grep search
- `<leader>sd` -> Search diagnostics
- `<leader>sr` -> Resume previous search
- `<leader>s.` -> Search recent files
- `<leader><leader>` -> Find existing buffers
- `<leader>/` -> Fuzzy search in current buffer
- `<leader>s/` -> Live grep in open files

### Telescope UI Keymaps
#### Insert Mode
- `<C-k>` -> Move to previous result
- `<C-j>` -> Move to next result
- `<C-l>` -> Open selected file
- `<C-/>` -> Show help (keymaps list)

#### Normal Mode
- `?` -> Show help (keymaps list)

### Features
- **File Search**:
  - Ignores: `node_modules`, `.git`, `.venv`
  - Includes hidden files
- **Live Grep**:
  - Searches hidden files by default
  - Same ignore patterns as file search
- **UI Enhancements**:
  - FZF native sorting (if available)
  - Dropdown theme for UI Select

### Special Functions
- `current_buffer_fuzzy_find` -> Fuzzy search within current buffer with: 
  - 10% window blend
  - Dropdown theme
  - Disabled previewer

### Extensions
- `fzf` -> Enabled if make is installed
- `ui-select` -> Provides dropdown UI elements