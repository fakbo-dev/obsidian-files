# LSP

**Domain**:: #neovim #editor #LSP
**Expertise**:: ` 🚀 Advanced`
**Last Used**:: 2025-05-31
**Related**:: [[Telescope]]
**Tags**:: #cheatsheet #reference #LSP #language-server

## Core Syntax & Operations

```lua
-- Basic LSP setup
local lsp = require('lspconfig')
lsp.tsserver.setup{}      -- TypeScript/JavaScript
lsp.ruff_lsp.setup{}       -- Python linting
lsp.lua_ls.setup{          -- Lua with custom config
  settings = {
    Lua = {
      runtime = { version = 'LuaJIT' },
      workspace = { library = vim.api.nvim_get_runtime_file("", true) },
      diagnostics = { disable = {'missing-fields'} }
    }
  }
}
```

## Productivity Shortcuts

```lua
-- Keymap template
vim.api.nvim_create_autocmd('LspAttach', {
  callback = function(args)
    local client = vim.lsp.get_client_by_id(args.data.client_id)
    local map = function(mode, lhs, rhs, desc)
      vim.keymap.set(mode, lhs, rhs, { buffer = args.buf, desc = desc })
    end

    -- Navigation
    map('n', 'gd', vim.lsp.buf.definition, 'Goto definition')
    map('n', 'gr', '<cmd>Telescope lsp_references<CR>', 'Goto references')
    map('n', 'gI', '<cmd>Telescope lsp_implementations<CR>', 'Goto implementation')
  end
})
```

## Common Patterns

### Basic Usage

```lua
-- Symbol navigation
map('n', '<leader>ds', vim.lsp.buf.document_symbol, 'Document symbols')
map('n', '<leader>ws', '<cmd>Telescope lsp_dynamic_workspace_symbols<CR>', 'Workspace symbols')
```

### Composite Workflow

```lua
-- Code modification
map('n', '<leader>rn', vim.lsp.buf.rename, 'Rename symbol')
map({'n', 'v'}, '<leader>ca', vim.lsp.buf.code_action, 'Code action')
```

## Debugging Guide

```lua
-- Common issues:
-- LSP not starting? Check:
:LspInfo          -- Verify server status
:MasonLog         -- View installation logs

-- Functionality missing?
:checkhealth lsp  -- Verify capabilities
```

## Real-World Examples

### Python Configuration

```lua
-- Disable pylsp plugins
lsp.pylsp.setup{
  settings = {
    pylsp = {
      plugins = {
        pyflakes = { enabled = false },
        pycodestyle = { enabled = false },
        -- ... other disabled plugins
      }
    }
  }
}
```

### Lua Configuration

```lua
-- Lua Language Server
lsp.lua_ls.setup{
  settings = {
    Lua = {
      completion = { callSnippet = "Replace" },
      telemetry = { enable = false },
      format = { enable = false }  -- Disable built-in formatting
    }
  }
}
```

## Advanced Techniques

```lua
-- Inlay hints toggle
local inlay_hints = require('lsp-inlayhints')
map('n', '<leader>th', function()
  inlay_hints.toggle()
end, 'Toggle inlay hints')

-- Document highlight
vim.api.nvim_create_autocmd({'CursorHold', 'CursorHoldI'}, {
  callback = function()
    vim.lsp.buf.document_highlight()
  end
})
```

## Configuration Snippets

### Minimal Setup

```lua
-- Basic capabilities
local capabilities = require('cmp_nvim_lsp').default_capabilities()

-- Auto-install servers
require('mason-lspconfig').setup_handlers {
  function(server_name)
    require('lspconfig')[server_name].setup {
      capabilities = capabilities
    }
  end
}
```

### Optimized Setup

```lua
-- Enhanced diagnostics
vim.diagnostic.config({
  virtual_text = true,
  signs = true,
  update_in_insert = false,
  severity_sort = true,
  float = { border = 'rounded' }
})
```

## Cross-Tool Integration

```lua
-- With Telescope
map('n', '<leader>D', '<cmd>Telescope lsp_type_definitions<CR>', 'Type definition')

-- With null-ls (formatters)
local null_ls = require('null-ls')
null_ls.setup({
  sources = {
    null_ls.builtins.formatting.stylua,  -- Lua formatter
    null_ls.builtins.diagnostics.ruff,   -- Python linter
  }
})
```

## Version-Specific Notes

| Version | Changes              | Compatibility |
| ------- | -------------------- | ------------- |
| 0.7+    | Native LSP support   | Neovim 0.7+   |
| 0.9+    | Improved inlay hints | Neovim 0.9+   |

## Pro Tips

```lua
-- Auto-format on save
vim.api.nvim_create_autocmd('BufWritePre', {
  callback = function()
    vim.lsp.buf.format({ async = false })
  end
})

-- Server-specific settings
lsp.terraformls.setup{
  filetypes = { 'terraform', 'tf' }
}
```

> **Remember**: Use `:LspInfo` to check active language servers

## Reference Links

1. [Neovim LSP Documentation](https://neovim.io/doc/user/lsp.html)
2. [Mason.nvim GitHub](https://github.com/williamboman/mason.nvim)
3. [nvim-lspconfig](https://github.com/neovim/nvim-lspconfig)

---

### Complete Keymap Reference

```markdown
## Navigation

gd Goto definition (Telescope)
gD Goto declaration
gr Goto references (Telescope)
gI Goto implementation (Telescope)
<leader>D Type definition (Telescope)
<leader>ds Document symbols
<leader>ws Workspace symbols

## Refactoring

<leader>rn Rename symbol
<leader>ca Code action (normal/visual)
<leader>th Toggle inlay hints

## Diagnostics

[g Previous diagnostic
]g Next diagnostic
<leader>d Show diagnostic float
<leader>q Open diagnostics list
```

### Installed LSP Servers

```markdown
- **tsserver** (TypeScript/JavaScript)
- **ruff** (Python linter)
- **pylsp** (Python) with disabled:
  - pyflakes, pycodestyle, autopep8, yapf
  - mccabe, mypy, black, isort
- **html**
- **cssls**
- **tailwindcss**
- **dockerls**
- **sqlls**
- **terraformls**
- **jsonls**
- **yamlls**
- **lua_ls** (Lua) with:
  - LuaJIT runtime
  - Workspace library inclusion
  - Formatting disabled
  - Snippet replacement
```

### Mason Tools

```markdown
- **stylua** (Lua formatter)
- **prettier** (JS/TS formatter)
- **black** (Python formatter)
- **shellcheck** (Shell script analyzer)
```

### Management Commands

```vim
:Mason        # Manage LSP servers/tools
:LspInfo      # Show active LSP servers
:LspInstall   # Install specific server
:LspRestart   # Restart current server
:MasonLog     # View installation logs
```
