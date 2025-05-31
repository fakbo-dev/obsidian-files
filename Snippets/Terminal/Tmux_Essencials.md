# Tmux_Essencials

**Domain**:: #CLI
**Expertise**:: ` ⚡️ Intermediate`
**Last Used**:: 2025-05-31
**Related**:: [[Bash_Commands|bash_Commands]],[[wezterm config|Wezterm config]]
**Tags**:: #cheatsheet #reference #tmux #terminal

## Core Syntax & Operations

```bash
# Session Management
tmux new -s mysession          # Create named session
tmux attach -t mysession       # Attach to session
tmux ls                        # List sessions
tmux kill-session -t mysession # Terminate session
tmux rename-session -t old new # Rename session

# Window Operations
tmux new-window -n "Logs"      # Create named window
tmux kill-window               # Close current window
```

## Productivity Shortcuts

```bash
# Aliases for quick access
alias t='tmux'
alias ta='tmux attach -t'
alias tl='tmux ls'
alias tn='tmux new -s'
alias tk='tmux kill-session -t'
```

## Common Patterns

### Basic Usage

```bash
# Session navigation
prefix (  # Previous session
prefix )  # Next session
prefix $  # Rename current session

# Window management
prefix c  # Create new window
prefix ,  # Rename current window
prefix &  # Close current window
prefix 0  # Jump to window 0
```

### Composite Workflow

```bash
# Dev environment setup
tmux new -s project -d         # Create detached
tmux send-keys -t project:1 "nvim src" C-m
tmux split-window -h -t project:1
tmux send-keys -t project:1.1 "npm run dev" C-m
tmux attach -t project
```

## Debugging Guide

```bash
# Reload config without restart
prefix :source-file ~/.tmux.conf

# Common error:
ERROR: "sessions should be nested with care"
FIX: "unset TMUX before creating new session"
```

## Real-World Examples

### Development Workflow

```bash
# IDE-like layout
prefix "  # Split vertically
prefix %  # Split horizontally
prefix z  # Zoom active pane
prefix Space  # Toggle layouts
```

### Session Restoration

```bash
# Save/restore sessions
tmuxp save ~/.tmuxp/dev.yaml  # Save layout
tmuxp load dev                # Restore layout
```

## Advanced Techniques

```bash
# Session persistence
prefix + Ctrl-s  # Save session state (resurrect plugin)
prefix + Ctrl-r  # Restore session state

# Pair programming
tmux -S /tmp/pair new -s shared  # Shared socket
chmod 777 /tmp/pair              # Allow connections
```

## Configuration Snippets

### Minimal Setup

```bash
# ~/.tmux.conf essentials
set -g prefix C-a         # Change prefix to Ctrl-a
unbind C-b                # Unbind default prefix
bind C-a send-prefix      # Pass Ctrl-a to apps
set -g mouse on           # Enable mouse
setw -g mode-keys vi      # Vi-style navigation
set -sg escape-time 0     # Faster response
```

### Optimized Setup

```bash
# Enhanced workflow
set -g base-index 1           # Start window numbering at 1
set -g pane-base-index 1      # Start pane numbering at 1
set -g renumber-windows on    # Renumber windows when closed
set -g history-limit 100000   # Increase scrollback buffer

# Vi-mode copy/paste
bind-key -T copy-mode-vi v send-keys -X begin-selection
bind-key -T copy-mode-vi y send-keys -X copy-selection
```

## Cross-Tool Integration

```bash
# With Neovim (send commands from Vim)
:!tmux new-window -n debugger

# With SSH (auto-attach)
ssh user@host -t 'tmux attach -t dev || tmux new -s dev'
```

## Version-Specific Notes

| Version | Changes            | Compatibility      |
| ------- | ------------------ | ------------------ |
| 3.0+    | Mouse improvements | Linux/macOS        |
| 3.2+    | Pane zoom toggle   | Requires recompile |

## Pro Tips

```bash
# Faster navigation
bind -n M-Left select-pane -L   # Alt-arrow navigation
bind -n M-Right select-pane -R
bind -n M-Up select-pane -U
bind -n M-Down select-pane -D

# Quick config reload
bind r source-file ~/.tmux.conf \\; display "Config reloaded!"
```

> **Remember**: Use `prefix + ?` to see all available key bindings

## Reference Links

1. [Tmux Official Documentation](https://man7.org/linux/man-pages/man1/tmux.1.html)
2. [Tmux Cheat Sheet](https://tmuxcheatsheet.com/)
3. [Advanced Tmux Configuration](https://github.com/gpakosz/.tmux)

---

### Key Bindings Reference

```bash
# Sessions
prefix :new [name]  # Create sibling session
prefix d            # Detach from session
prefix (            # Previous session
prefix )            # Next session
prefix $            # Rename current session

# Windows
prefix c       # Create new window
prefix n       # Next window
prefix p       # Previous window
prefix 0-9     # Jump to window number
prefix ,       # Rename current window
prefix &       # Close current window
prefix w       # List windows interactively
```

```bash
# Panes
prefix %       # Split horizontally
prefix '"'       # Split vertically
prefix arrow   # Switch between panes
prefix x       # Close current pane
prefix Space   # Toggle pane layouts
prefix z       # Zoom pane (toggle full-screen)
prefix Ctrl-arrow   # Resize by 1 cell
prefix Alt-arrow    # Resize by 5 cells

# Copy Mode
prefix [       # Enter copy mode
Space          # Start text selection
Enter          # Copy selected text
prefix ]       # Paste copied text

# Utilities
prefix :       # Command prompt
prefix ?       # Show key bindings
prefix t       # Display clock
prefix :setw synchronize-panes  # Sync input to all panes
```

### Advanced Operations

```
# Quickly switch to last-used window
prefix l

# Reattach or create new session
tmux a || tmux new

# List attached clients
tmux list-clients

# Save session layout
tmuxp save mysession
```
