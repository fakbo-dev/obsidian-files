---
id: TMUX
aliases: [
- code
]
tags: []
---

## **Tmux Essentials Cheat Sheet**

session: [[Computer science]]

### **Sessions**

```bash
# Create a new session in a session (sibling)
prefix :new [name]
# Start new session
tmux new -s mysession

# List sessions
tmux ls

# Attach to session
tmux attach -t mysession

# Detach from session (inside tmux)
Ctrl-b d

# Rename current session Ctrl-b $

# Switch between sessions
Ctrl-b ( and Ctrl-b )  # Previous/next session
```

### **Windows**

```bash
# Create new window
Ctrl-b c

# Switch between windows
Ctrl-b n       # Next window
Ctrl-b p       # Previous window
Ctrl-b 0-9     # Jump to window number

# Rename current window
Ctrl-b ,

# Close current window
Ctrl-b &

# List windows interactively
Ctrl-b w
```

### **Panes**

```bash
# Split pane horizontally
Ctrl-b %

# Split pane vertically
Ctrl-b "

# Switch between panes
Ctrl-b arrow keys

# Close current pane
Ctrl-b x

# Toggle pane layouts
Ctrl-b Space

# Resize panes (hold Ctrl/Alt with arrows)
Ctrl-b Ctrl-arrow   # Resize by 1 cell
Ctrl-b Alt-arrow    # Resize by 5 cells
```

### **Copy Mode**

```bash
# Enter copy mode (scroll buffer)
Ctrl-b [

# Navigate: Arrow keys / PgUp / PgDn

# Start text selection
Space

# Copy selected text
Enter

# Paste copied text
Ctrl-b ]
```

### **Key Bindings**

```bash
# Command prompt (run any tmux command)
Ctrl-b :

# Show help (list all key bindings)
Ctrl-b ?

# Enter command to reload config
Ctrl-b :source-file ~/.tmux.conf

# Display clock
Ctrl-b t
```

### **Configuration**

```bash
# Enable mouse support (add to ~/.tmux.conf)
set -g mouse on

# Set vi-style navigation in copy mode
setw -g mode-keys vi

# Change prefix to Ctrl-a (example)
unbind C-b
set -g prefix C-a
bind C-a send-prefix

# Faster response for escape key
set -sg escape-time 0
```

### **Advanced Operations**

```bash
# Synchronize input to all panes (toggle)
Ctrl-b :setw synchronize-panes

# Save session layout/state
tmuxp save mysession

# Kill a session
tmux kill-session -t mysession

# List attached clients
tmux list-clients
```

### **Useful Aliases**

```bash
# Add to ~/.bashrc for quick access
alias t='tmux'
alias ta='tmux attach -t'
alias tl='tmux ls'
alias tn='tmux new -s'
```

### **Pro Tips**

```bash
# Quickly switch to last-used window
Ctrl-b l

# Reattach to a session in 1 command
tmux a || tmux new  # Attach or create new

# Zoom into a pane (toggle full-screen)
Ctrl-b z
```
