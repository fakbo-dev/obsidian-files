# Snippets

**Domain**:: #editor #neovim
**Expertise**:: `⚡️ Intermediate `
**Last Used**:: 2025-05-31
**Related**:: [[]]
**Tags**:: #cheatsheet #reference #neovim #keymaps

## Core Syntax & Operations

```lua
-- Basic movement
vim.keymap.set('n', 'x', '"_x', { desc = 'Delete char without yanking' })
vim.keymap.set('n', 'n', 'nzzzv', { desc = 'Next match and center' })
vim.keymap.set('n', 'N', 'Nzzzv', { desc = 'Previous match and center' })

-- Buffer management
vim.keymap.set('n', '<leader>b', ':enew<CR>', { desc = 'New buffer' })
vim.keymap.set('n', '<leader>x', ':bd<CR>', { desc = 'Close buffer' })
```

## Productivity Shortcuts

```lua
-- Quick save/quit
vim.keymap.set('n', '<C-s>', ':w<CR>', { desc = 'Save file' })
vim.keymap.set('n', '<leader>sn', ':noa w<CR>', { desc = 'Save without formatting' })
vim.keymap.set('n', '<C-q>', ':q<CR>', { desc = 'Quit' })

-- Window navigation
vim.keymap.set('n', '<C-j>', '<C-w>j', { desc = 'Move to lower split' })
vim.keymap.set('n', '<C-k>', '<C-w>k', { desc = 'Move to upper split' })
vim.keymap.set('n', '<C-h>', '<C-w>h', { desc = 'Move to left split' })
vim.keymap.set('n', '<C-l>', '<C-w>l', { desc = 'Move to right split' })
```

## Common Patterns

### Basic Usage

```lua
-- Buffer navigation
vim.keymap.set('n', '<Tab>', ':bnext<CR>', { desc = 'Next buffer' })
vim.keymap.set('n', '<S-Tab>', ':bprevious<CR>', { desc = 'Previous buffer' })

-- Window management
vim.keymap.set('n', '<leader>v', ':vsplit<CR>', { desc = 'Vertical split' })
vim.keymap.set('n', '<leader>h', ':split<CR>', { desc = 'Horizontal split' })
```

### Composite Workflow

```lua
-- Resize windows with arrow keys
vim.keymap.set('n', '<Up>', ':resize -2<CR>', { desc = 'Resize window up' })
vim.keymap.set('n', '<Down>', ':resize +2<CR>', { desc = 'Resize window down' })
vim.keymap.set('n', '<Left>', ':vertical resize -2<CR>', { desc = 'Resize window left' })
vim.keymap.set('n', '<Right>', ':vertical resize +2<CR>', { desc = 'Resize window right' })
```

## Debugging Guide

```lua
-- Show keymaps
vim.keymap.set('n', '<leader>km', ':Telescope keymaps<CR>', { desc = 'Show all keymaps' })

-- Common issue:
-- Keymap not working? Check conflicts with:
-- :verbose nmap <keysequence>
```

## Real-World Examples

### Diagnostic Workflow

```lua
-- LSP diagnostics
vim.keymap.set('n', '[d', vim.diagnostic.goto_prev, { desc = 'Previous diagnostic' })
vim.keymap.set('n', ']d', vim.diagnostic.goto_next, { desc = 'Next diagnostic' })
vim.keymap.set('n', '<leader>d', vim.diagnostic.open_float, { desc = 'Show diagnostic' })
vim.keymap.set('n', '<leader>q', vim.diagnostic.setloclist, { desc = 'Diagnostics list' })
```

### Tab Management

```lua
-- Tab navigation
vim.keymap.set('n', '<leader>to', ':tabnew<CR>', { desc = 'New tab' })
vim.keymap.set('n', '<leader>tx', ':tabclose<CR>', { desc = 'Close tab' })
vim.keymap.set('n', '<leader>tn', ':tabnext<CR>', { desc = 'Next tab' })
vim.keymap.set('n', '<leader>tp', ':tabprevious<CR>', { desc = 'Previous tab' })
```

## Advanced Techniques

```lua
-- Terminal mode navigation
vim.keymap.set('t', '<Esc>', '<C-\\><C-n>', { desc = 'Exit terminal mode' })

-- Keep selection after indent
vim.keymap.set('v', '<', '<gv', { desc = 'Indent left and keep selection' })
vim.keymap.set('v', '>', '>gv', { desc = 'Indent right and keep selection' })
```

## Configuration Snippets

### Minimal Setup

```lua
-- Basic keymaps
vim.keymap.set('n', '<leader>se', '<C-w>=', { desc = 'Balance window sizes' })
vim.keymap.set('n', '<leader>xs', ':close<CR>', { desc = 'Close split' })
vim.keymap.set('n', '<leader>lw', ':set wrap!<CR>', { desc = 'Toggle line wrap' })
```

### Optimized Setup

```lua
-- Enhanced navigation
vim.keymap.set('n', '<A-h>', '<C-w>h', { desc = 'Move to left window' })
vim.keymap.set('n', '<A-l>', '<C-w>l', { desc = 'Move to right window' })

-- Smart paste in visual mode
vim.keymap.set('v', 'p', '"_dP', { desc = 'Paste without overwriting register' })
```

## Cross-Tool Integration

```lua
-- Telescope integration
vim.keymap.set('n', '<leader>ff', ':Telescope find_files<CR>', { desc = 'Find files' })
vim.keymap.set('n', '<leader>fg', ':Telescope live_grep<CR>', { desc = 'Live grep' })
```

## Version-Specific Notes

| Version | Changes              | Compatibility   |
| ------- | -------------------- | --------------- |
| 0.9+    | Improved diagnostics | Lua keymaps     |
| Nightly | Enhanced window opts | Requires update |

## Pro Tips

```lua
-- Create keymap groups
local function map(mode, lhs, rhs, opts)
  local options = { noremap = true, silent = true }
  if opts then options = vim.tbl_extend('force', options, opts) end
  vim.keymap.set(mode, lhs, rhs, options)
end

-- Usage:
map('n', '<leader>w', ':w<CR>', { desc = 'Save file' })
```

> **Remember**: Use `:Telescope keymaps` to discover and manage your keybindings

## Reference Links

1. [Neovim Keymap Documentation](https://neovim.io/doc/user/map.html)
2. [Lua Keymaps Guide](https://github.com/nanotee/nvim-lua-guide#keybindings)
3. [Best Keymap Practices](https://www.getman.io/posts/proper-neovim-setup/)

---

### Complete Keymap Reference

```lua
---------- NORMAL MODE ----------
-- File Operations
<C-s>         Save file
<leader>sn    Save without formatting
<C-q>         Quit file

-- Editing
x             Delete char without yanking
<leader>lw    Toggle line wrapping

-- Navigation
<C-d>         Scroll down and center
<C-u>         Scroll up and center
n             Next match and center
N             Previous match and center
<Tab>         Next buffer
<S-Tab>       Previous buffer

-- Window Management
<Up>          Resize window up (-2 lines)
<Down>        Resize window down (+2 lines)
<Left>        Resize window left (-2 cols)
<Right>       Resize window right (+2 cols)
<leader>v     Vertical split
<leader>h     Horizontal split
<leader>se    Balance window sizes
<leader>xs    Close current split
<C-j>         Move to lower split
<C-k>         Move to upper split
<C-h>         Move to left split
<C-l>         Move to right split
<A-h>         Move to left window
<A-l>         Move to right window

-- Buffers & Tabs
<leader>b     New buffer
<leader>x     Close buffer
<leader>to    New tab
<leader>tx    Close tab
<leader>tn    Next tab
<leader>tp    Previous tab

-- Diagnostics
[d            Previous diagnostic
]d            Next diagnostic
<leader>d     Show diagnostic float
<leader>q     Open diagnostics list

---------- VISUAL MODE ----------
<             Indent left (keep selection)
>             Indent right (keep selection)
p             Paste without overwriting register
```

### Diagnostic Keymaps

```lua
-- LSP Diagnostics
[g            Previous diagnostic (git signs)
]g            Next diagnostic (git signs)
<leader>df    Fix diagnostic (LSP)
<leader>dl    Toggle diagnostic loclist
```
