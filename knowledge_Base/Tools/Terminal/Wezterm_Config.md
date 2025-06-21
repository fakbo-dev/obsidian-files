# Wezterm_Config

**Domain**:: #terminal
**Expertise**:: `⚡️ Intermediate`
**Last Used**:: 2025-06-02
**Related**:: [[Bash_Commands|bash_Commands]]
**Tags**:: #cheatsheet #reference #wezterm #terminal #CLI

### useful thing

```lua
ALT + ENTER === ZENMODE

```

### Core Syntax & Operations

```lua
-- Basic terminal configuration
config.front_end = "WebGpu"
config.max_fps = 144
config.default_cursor_style = "BlinkingBlock"
config.cursor_blink_rate = 500
config.term = "xterm-256color"
config.window_background_opacity = 0.9
config.font_size = 11.0
config.initial_cols = 80
```

### Productivity Shortcuts

```lua
-- Tmux-style navigation
config.leader = { key = "b", mods = "CTRL" }

{ key = "-", mods = "LEADER", action = act.SplitVertical({ domain = "CurrentPaneDomain" }) },
{ key = "\\", mods = "LEADER", action = act.SplitHorizontal({ domain = "CurrentPaneDomain" }) },
{ key = "z", mods = "LEADER", action = "TogglePaneZoomState" },
{ key = "h", mods = "LEADER", action = act.ActivatePaneDirection("Left") },
{ key = "j", mods = "LEADER", action = act.ActivatePaneDirection("Down") },
{ key = "k", mods = "LEADER", action = act.ActivatePaneDirection("Up") },
{ key = "l", mods = "LEADER", action = act.ActivatePaneDirection("Right") },
```

### Common Patterns

#### Color Scheme Toggling

```lua
wezterm.on("toggle-colorscheme", function(window, pane)
  local overrides = window:get_config_overrides() or {}
  if overrides.color_scheme == "Zenburn" then
    overrides.color_scheme = "Cloud (terminal.sexy)"
  else
    overrides.color_scheme = "Zenburn"
  end
  window:set_config_overrides(overrides)
end)

-- Trigger with CTRL+SHIFT+ALT+E
{ key = "E", mods = "CTRL|SHIFT|ALT", action = wezterm.action.EmitEvent("toggle-colorscheme") }
```

#### Pane Management

```lua
-- Resize panes
{ key = "H", mods = "LEADER|SHIFT", action = act.AdjustPaneSize({ "Left", 5 }) },
{ key = "J", mods = "LEADER|SHIFT", action = act.AdjustPaneSize({ "Down", 5 }) },
{ key = "K", mods = "LEADER|SHIFT", action = act.AdjustPaneSize({ "Up", 5 }) },
{ key = "L", mods = "LEADER|SHIFT", action = act.AdjustPaneSize({ "Right", 5 }) },

-- Close pane/tab
{ key = "x", mods = "LEADER", action = act.CloseCurrentPane({ confirm = true }) },
{ key = "&", mods = "LEADER|SHIFT", action = act.CloseCurrentTab({ confirm = true }) },
```

### Configuration Snippets

#### Minimal Setup

```lua
local wezterm = require("wezterm")
local config = wezterm.config_builder()

config.font = wezterm.font("FiraCode Nerd Font Mono")
config.font_size = 11.0
config.color_scheme = "Zenburn"
config.default_prog = { "powershell.exe", "-NoLogo" }

return config
```

#### Optimized Setup

```lua
-- Performance-optimized settings
config.front_end = "WebGpu"
config.max_fps = 144
config.prefer_egl = true
config.animation_fps = 1
config.cell_width = 0.9  -- Improves text rendering

-- Window optimization
config.window_padding = { left = 0, right = 0, top = 0, bottom = 0 }
config.window_decorations = "NONE | RESIZE"
```

### Advanced Techniques

```lua
-- Dynamic opacity toggle
{
  key = "O",
  mods = "CTRL|ALT",
  action = wezterm.action_callback(function(window, _)
    local overrides = window:get_config_overrides() or {}
    overrides.window_background_opacity = overrides.window_background_opacity == 1.0 and 0.9 or 1.0
    window:set_config_overrides(overrides)
  end)
},

-- Tab switching with leader
{ key = "1", mods = "LEADER", action = act.ActivateTab(0) },
-- ... repeat for 2-9 ...
{ key = "9", mods = "LEADER", action = act.ActivateTab(8) }
```

### Pro Tips

```lua
-- Use Iosevka for window frame to match editor fonts
config.window_frame = {
  font = wezterm.font({ family = "Iosevka Custom", weight = "Regular" }),
  active_titlebar_bg = "#0c0b0f"
}

-- Clean tab bar configuration
config.hide_tab_bar_if_only_one_tab = true
config.use_fancy_tab_bar = false
```

> **Remember**: Use `CTRL+b` as your leader key for tmux-style navigation, followed by single-key commands for pane/tab management.

### Reference Links

1. [WezTerm Configuration Docs](https://wezfurlong.org/wezterm/config/files.html)
2. [Lua API Reference](https://wezfurlong.org/wezterm/config/lua/index.html)
3. [Key Binding Cheat Sheet](https://wezfurlong.org/wezterm/config/keys.html)

### Version-Specific Notes

| Version           | Changes                 | Compatibility  |
| ----------------- | ----------------------- | -------------- |
| v20240612-3a87700 | WebGPU backend stable   | ✅ Recommended |
| v20230712         | Initial Windows support | ⚠️ Limited     |

### Color Configuration

```lua
config.colors = {
  background = "#0c0b0f",
  cursor_bg = "#bea3c7",
  tab_bar = {
    background = "#0c0b0f",
    active_tab = { fg_color = "#bea3c7" },
    inactive_tab = { fg_color = "#f8f2f5" }
  }
}
```

### Clipboard Integration

```lua
{ key = "v", mods = "SHIFT|CTRL", action = act.PasteFrom("Clipboard") },
{ key = "c", mods = "SHIFT|CTRL", action = act.CopyTo("Clipboard") }
```
