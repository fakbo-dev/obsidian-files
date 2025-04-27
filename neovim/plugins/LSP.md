Source: [[Neovim Commands]]
## LSP Configuration

### Keymaps (Active in LSP buffers)
- `gd` -> Goto definition (Telescope)
- `gr` -> Goto references (Telescope)
- `gI` -> Goto implementation (Telescope)
- `<leader>D` -> Type definition (Telescope)
- `<leader>ds` -> Document symbols
- `<leader>ws` -> Workspace symbols
- `<leader>rn` -> Rename symbol
- `<leader>ca` -> Code action (normal/visual modes)
- `gD` -> Goto declaration
- `<leader>th` -> Toggle inlay hints (if supported)

### Installed LSP Servers
- **tsserver** (TypeScript/JavaScript)
- **ruff** (Python linter)
- **pylsp** (Python) with disabled plugins:
  - pyflakes
  - pycodestyle
  - autopep8
  - yapf
  - mccabe
  - mypy
  - black
  - isort
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
  - Completion snippet replacement

### Mason Tools
- **stylua** (Lua formatter)

### Features
- Automatic server installation via Mason
- Document highlight on cursor hold
- Inlay hints toggle support
- Enhanced capabilities with nvim-cmp
- Workspace symbol search
- Code actions in normal/visual modes

### Special Configuration
- **Python**:
  - Uses ruff for linting
  - Disables pylsp formatting/linting plugins
- **Lua**:
  - Custom workspace libraries
  - Disabled missing-fields diagnostics
  - Snippet replacement in completions

### Management
- `:Mason` -> Manage installed LSP servers/tools
- Automatic setup for configured servers
- Fallback to default configurations when unspecified