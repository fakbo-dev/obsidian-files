# neo-tree

**Domain**:: #editor #neovim #Search
**Expertise**:: `⚡️ Intermediate`
**Last Used**:: 2025-05-31
**Related**:: [[Tricks|tricks]], [[Snippets|snippets]], [[Telescope]]
**Tags**:: #cheatsheet #reference #neovim #file-explorer #neo-tree

## Core Syntax & Operations

```lua
-- Basic setup
require('neo-tree').setup({
  window = {
    mappings = {
      ['<space>'] = 'toggle_node',  -- Toggle expansion
      ['<cr>'] = 'open',            -- Open file/directory
      ['<bs>'] = 'navigate_up',     -- Move up directory
    }
  }
})
```

## Productivity Shortcuts

```lua
-- Global keymaps
vim.keymap.set('n', '\\', '<cmd>Neotree reveal<CR>', { desc = 'Reveal Neo-tree' })
vim.keymap.set('n', '<leader>e', '<cmd>Neotree toggle position=left<CR>', { desc = 'Toggle file explorer' })
vim.keymap.set('n', '<leader>ngs', '<cmd>Neotree float git_status<CR>', { desc = 'Floating git status' })
```

## Common Patterns

### Basic Usage

```lua
-- Open file in various ways
['s'] = 'open_split',        -- Vertical split
['S'] = 'open_vsplit',       -- Horizontal split
['t'] = 'open_tabnew',       -- New tab
['w'] = 'open_with_window_picker'  -- Choose window
```

### Composite Workflow

```lua
-- Git workflow
['ga'] = 'git_add_file',     -- Stage file
['gu'] = 'git_unstage_file', -- Unstage file
['gc'] = 'git_commit',       -- Commit changes
['gp'] = 'git_push',         -- Push changes
```

## Debugging Guide

```lua
-- Common issues:
-- Not showing files? Use:
:R                  -- Refresh tree
:H                  -- Toggle hidden files

-- Navigation not working?
:checkhealth neo-tree  # Verify dependencies
```

## Real-World Examples

### File Operations

```lua
-- Copy/move workflow
['y'] = 'copy_to_clipboard', -- Yank (copy)
['x'] = 'cut_to_clipboard',  -- Cut (move)
['p'] = 'paste_from_clipboard', -- Paste

-- Create/delete
['a'] = 'add',               -- Add file
['A'] = 'add_directory',     -- Add folder
['d'] = 'delete',            -- Delete
['r'] = 'rename',            -- Rename
```

### View Management

```lua
-- Toggle views
['z'] = 'close_all_nodes',   -- Collapse all
['C'] = 'close_node',        -- Close current node
['P'] = 'toggle_preview',    -- Preview toggle
```

## Advanced Techniques

```lua
-- Sorting options (press 'o' first)
['oc'] = 'sort_by_created',   -- Created time
['od'] = 'sort_by_diagnostics',-- Diagnostics
['og'] = 'sort_by_git_status', -- Git status
['om'] = 'sort_by_modified',  -- Modified time
['on'] = 'sort_by_name',      -- Name
['os'] = 'sort_by_size',      -- Size
['ot'] = 'sort_by_type',      -- Type
```

## Configuration Snippets

### Minimal Setup

```lua
require('neo-tree').setup({
  filesystem = {
    filtered_items = {
      visible = true,         -- Show hidden files by default
      hide_dotfiles = false,
      hide_gitignored = false,
    }
  }
})
```

### Optimized Setup

```lua
-- Git integration
require('neo-tree').setup({
  source_selector = {
    winbar = true,
    sources = {
      { source = "filesystem" },
      { source = "git_status" },
      { source = "buffers" },
    }
  }
})
```

## Cross-Tool Integration

```lua
-- With Telescope
vim.keymap.set('n', '<leader>ff', function()
  require('neo-tree.command').execute({ action = 'focus', source = 'filesystem' })
end, { desc = 'Focus file explorer' })

-- With LSP diagnostics
['[d'] = 'prev_diag_item',  -- Previous diagnostic
[']d'] = 'next_diag_item',  -- Next diagnostic
```

## Version-Specific Notes

| Version | Changes             | Compatibility |
| ------- | ------------------- | ------------- |
| 2.x     | New source selector | Neovim 0.8+   |
| 3.x     | Improved git status | Neovim 0.9+   |

## Pro Tips

```lua
-- Quick file creation
vim.keymap.set('n', '<leader>nf', function()
  require('neo-tree.command').execute({ action = 'focus', source = 'filesystem' })
  vim.schedule(function() vim.cmd('normal a') end)
end, { desc = 'Create new file' })

-- Set root to current directory
vim.keymap.set('n', '<leader>.', '<cmd>Neotree filesystem reveal right<CR>', {})
```

> **Remember**: Use `?` in Neo-tree to show all available keymaps

## Reference Links

1. [Neo-tree GitHub](https://github.com/nvim-neo-tree/neo-tree.nvim)
2. [Neo-tree Wiki](https://github.com/nvim-neo-tree/neo-tree.nvim/wiki)
3. [Advanced Configuration](https://www.lazyvim.org/plugins/editor#neo-treenvim)

---

### Complete Keymap Reference

```markdown
## Global Keymaps

\\ Reveal Neo-tree
<leader>e Toggle file explorer (left)
<leader>ngs Open floating git status

## Navigation

<space> Toggle node expansion
<cr> Open file/directory
<bs> Navigate up directory
. Set current directory as root

## File Operations

a Add file
A Add directory
d Delete
r Rename
y Copy to clipboard
x Cut to clipboard
p Paste from clipboard
c Copy file (alternative)
m Move file (alternative)

## Window Management

s Open in vertical split
S Open in horizontal split
t Open in new tab
w Open with window picker
P Toggle preview
q Close Neo-tree

## View Customization

z Close all nodes
C Close current node
R Refresh
H Toggle hidden files
/ Fuzzy finder
<C-x> Clear filter

## Git Integration

[g Previous git modified
]g Next git modified
ga Git add file
gu Git unstage file
gr Git revert file
gc Git commit
gp Git push
gg Git commit & push

## Sorting (Press 'o' first)

oc Order by created
od Order by diagnostics
og Order by git status
om Order by modified
on Order by name
os Order by size
ot Order by type

## Buffer Management

bd Delete buffer (buffers source)

## Preview Mode

P Toggle floating preview
<esc> Close preview
```

### Special Features

```lua
-- Floating window configuration
require('neo-tree').setup({
  popup_border_style = "rounded",
  default_component_configs = {
    floating = {
      position = "50%",
      width = 80,
      height = 30,
    }
  }
})
```

### Ignore Patterns

```lua
filesystem = {
  filtered_items = {
    hide_by_pattern = {
      "*.meta",
      "*/build/*",
      "*/__pycache__/*",
      "*.class",
      "*.log"
    }
  }
}
```
