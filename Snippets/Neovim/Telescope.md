# Telescope

**Domain**:: #editor #neovim #Search
**Expertise**:: `⚡️ Intermediate`
**Last Used**:: 2025-05-31
**Related**:: [[Snippets]],[[Tricks]]
**Tags**:: #cheatsheet #reference #Telescope #neovim

## Core Syntax & Operations

```lua
-- Basic setup
require('telescope').setup{
  defaults = {
    file_ignore_patterns = { "node_modules", ".git", ".venv" },
    hidden = true,  -- Include hidden files
  }
}

-- Keymap template
vim.keymap.set('n', '<leader>sf', '<cmd>Telescope find_files<CR>', {})
```

## Productivity Shortcuts

```lua
-- Essential keymaps
vim.keymap.set('n', '<leader>sf', '<cmd>Telescope find_files<CR>', { desc = 'Search files' })
vim.keymap.set('n', '<leader>sg', '<cmd>Telescope live_grep<CR>', { desc = 'Live grep' })
vim.keymap.set('n', '<leader>sb', '<cmd>Telescope buffers<CR>', { desc = 'Find buffers' })
```

## Common Patterns

### Basic Usage

```lua
-- File search with hidden files
:Telescope find_files hidden=true

-- Grep in specific directory
:Telescope live_grep search_dirs={'src/', 'lib/'}
```

### Composite Workflow

```lua
-- Create custom picker for JavaScript files
local js_files = function()
  require('telescope.builtin').find_files({
    find_command = {'rg', '--files', '--type', 'js'},
    prompt_title = 'JavaScript Files'
  })
end

vim.keymap.set('n', '<leader>sj', js_files, {})
```

## Debugging Guide

```lua
-- Common issue: Slow performance?
:Telescope find_files previewer=false

-- Not finding files?
:checkhealth telescope  # Verify dependencies
```

## Real-World Examples

### Code Navigation

```lua
-- Find references of current word
vim.keymap.set('n', '<leader>sr', '<cmd>Telescope lsp_references<CR>', {})

-- Find symbol in workspace
vim.keymap.set('n', '<leader>ss', '<cmd>Telescope lsp_dynamic_workspace_symbols<CR>', {})
```

### Project Management

```lua
-- Search recent projects
vim.keymap.set('n', '<leader>sp', '<cmd>Telescope projects<CR>', {})

-- Git status viewer
vim.keymap.set('n', '<leader>gs', '<cmd>Telescope git_status<CR>', {})
```

## Advanced Techniques

```lua
-- Fuzzy search in current buffer
vim.keymap.set('n', '<leader>/', function()
  require('telescope.builtin').current_buffer_fuzzy_find({
    previewer = false,
    layout_config = { width = 0.9, height = 0.5 }
  })
end, {})
```

## Configuration Snippets

### Minimal Setup

```lua
require('telescope').setup{
  defaults = {
    mappings = {
      i = {
        ['<C-j>'] = require('telescope.actions').move_selection_next,
        ['<C-k>'] = require('telescope.actions').move_selection_previous,
      }
    }
  }
}
```

### Optimized Setup

```lua
-- Enable FZF sorting if available
pcall(require('telescope').load_extension, 'fzf')

-- UI Select integration
require('telescope').load_extension('ui-select')
```

## Cross-Tool Integration

```lua
-- With LSP
vim.keymap.set('n', 'gd', '<cmd>Telescope lsp_definitions<CR>', {})
vim.keymap.set('n', 'gr', '<cmd>Telescope lsp_references<CR>', {})

-- With Git
vim.keymap.set('n', '<leader>gc', '<cmd>Telescope git_commits<CR>', {})
```

## Version-Specific Notes

| Version | Changes            | Compatibility |
| ------- | ------------------ | ------------- |
| 0.1.x   | Basic pickers      | Neovim 0.5+   |
| Latest  | Extensions support | Neovim 0.9+   |

## Pro Tips

```lua
-- Create custom previewers
local previewers = require('telescope.previewers')
local new_maker = function(filepath, bufnr, opts)
  opts = opts or {}
  filepath = vim.fn.expand(filepath)
  vim.loop.fs_stat(filepath, function(_, stat)
    if not stat then return end
    if stat.size > 100000 then  -- Skip large files
      return
    else
      previewers.buffer_previewer_maker(filepath, bufnr, opts)
    end
  end)
end

require('telescope').setup{ defaults = { buffer_previewer_maker = new_maker } }
```

> **Remember**: Use `<C-q>` in Telescope to send multiple selections to quickfix list

## Reference Links

1. [Telescope GitHub](https://github.com/nvim-telescope/telescope.nvim)
2. [Telescope Wiki](https://github.com/nvim-telescope/telescope.nvim/wiki)
3. [Advanced Configuration Guide](https://www.chiarulli.me/neovim/08-telescope/)

---

### Complete Keymap Reference

```markdown
## Global Keymaps

<leader>sf Search files (including hidden)
<leader>sg Live grep search
<leader>sh Search help tags
<leader>sk Search keymaps
<leader>ss Select Telescope built-in pickers
<leader>sw Search current word
<leader>sd Search diagnostics
<leader>sr Resume previous search
<leader>s. Search recent files
<leader><leader> Find existing buffers
<leader>/ Fuzzy search in current buffer
<leader>s/ Live grep in open files

## Telescope UI Navigation

### Insert Mode

<C-j> Move to next result
<C-k> Move to previous result
<C-l> Open selected file
<C-/> Show help (keymaps list)
<C-q> Send to quickfix (multi-select)

### Normal Mode

? Show help (keymaps list)
```

### Special Features Configuration

```lua
-- Current buffer fuzzy find
require('telescope').setup{
  pickers = {
    current_buffer_fuzzy_find = {
      theme = "dropdown",
      previewer = false,
      layout_config = {
        width = 0.8,
        height = 0.4,
      }
    }
  }
}

-- Enable extensions
require('telescope').load_extension('fzf')      -- Better sorting
require('telescope').load_extension('ui-select') -- Dropdown UI
```

### Ignore Patterns

```lua
-- Default ignore patterns
file_ignore_patterns = {
  "node_modules/*",
  ".git/*",
  ".venv/*",
  "build/*",
  "dist/*",
  "yarn.lock",
  "package-lock.json"
}
```
