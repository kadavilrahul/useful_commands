# Helix Editor - Installation and Usage Guide

## Overview

Helix is a modern, terminal-based text editor written in Rust. It features:
- Modal editing (similar to Vim but with improvements)
- Built-in Language Server Protocol (LSP) support
- Tree-sitter syntax highlighting
- Multiple selections and cursors
- No configuration required to get started

## Installation

### Ubuntu/Debian (Snap)
```bash
sudo snap install helix --classic
```

### Alternative Installation Methods

#### From Source (Latest Version)
```bash
# Install Rust if not already installed
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
source ~/.cargo/env

# Clone and build Helix
git clone https://github.com/helix-editor/helix
cd helix
cargo install --path helix-term --locked
```

#### Using Cargo
```bash
cargo install helix-term
```

#### Arch Linux
```bash
pacman -S helix
```

#### macOS (Homebrew)
```bash
brew install helix
```

## Verification

After installation, verify Helix is working:
```bash
hx --version
which hx
```

## Basic Usage

### Starting Helix

```bash
# Open a specific file
hx filename.txt

# Open current directory (file picker)
hx .

# Start without opening a file
hx
```

### Modal Editing Basics

Helix uses modal editing with several modes:

#### Normal Mode (Default)
- Navigate and manipulate text
- Press `Esc` to return to normal mode from any other mode

#### Insert Mode
- `i` - Insert before cursor
- `a` - Insert after cursor
- `I` - Insert at beginning of line
- `A` - Insert at end of line
- `o` - Open new line below
- `O` - Open new line above

#### Selection Mode
- `v` - Enter selection mode
- `V` - Select entire lines
- `Ctrl+v` - Block selection

### Essential Commands

#### Navigation
- `h`, `j`, `k`, `l` - Move left, down, up, right
- `w` - Move to next word
- `b` - Move to previous word
- `e` - Move to end of word
- `gg` - Go to beginning of file
- `ge` - Go to end of file
- `Ctrl+u` - Page up
- `Ctrl+d` - Page down

#### Editing
- `x` - Delete character
- `d` - Delete selection
- `c` - Change (delete and enter insert mode)
- `y` - Yank (copy)
- `p` - Paste after cursor
- `P` - Paste before cursor
- `u` - Undo
- `U` - Redo

#### File Operations
- `:w` - Save file
- `:q` - Quit
- `:wq` - Save and quit
- `:q!` - Quit without saving

#### Search and Replace
- `/` - Search forward
- `?` - Search backward
- `n` - Next search result
- `N` - Previous search result
- `:s/old/new/g` - Replace all occurrences in current line
- `:%s/old/new/g` - Replace all occurrences in file

### Advanced Features

#### Multiple Selections
- `C` - Add cursor below
- `Alt+C` - Add cursor above
- `;` - Collapse selections to cursor
- `Alt+;` - Flip selections

#### Language Server Protocol (LSP)
Helix has built-in LSP support for many languages. Install language servers for enhanced features:

```bash
# Python
pip install python-lsp-server

# JavaScript/TypeScript
npm install -g typescript-language-server typescript

# Rust (usually comes with rustup)
rustup component add rust-analyzer

# Go
go install golang.org/x/tools/gopls@latest
```

#### Tree-sitter
Helix uses tree-sitter for syntax highlighting. Install grammars:
```bash
hx --grammar fetch
hx --grammar build
```

## Configuration

### Config Directory
Helix configuration is stored in:
- Linux: `~/.config/helix/`
- macOS: `~/Library/Application Support/helix/`
- Windows: `%AppData%\helix\`

### Basic Configuration File (`config.toml`)
```toml
theme = "onedark"

[editor]
line-number = "relative"
mouse = true
middle-click-paste = true
scroll-lines = 3
shell = ["bash", "-c"]
text-width = 80
completion-trigger-len = 2
auto-completion = true
auto-format = true
auto-save = false
idle-timeout = 400
preview-completion-insert = true
completion-replace = false
auto-info = true
true-color = false
rulers = [80]
bufferline = "never"
color-modes = false

[editor.statusline]
left = ["mode", "spinner"]
center = ["file-name"]
right = ["diagnostics", "selections", "position", "file-encoding", "file-line-ending", "file-type"]
separator = "│"

[editor.lsp]
display-messages = true
auto-signature-help = true
display-inlay-hints = true
display-signature-help-docs = true

[editor.cursor-shape]
insert = "bar"
normal = "block"
select = "underline"

[editor.file-picker]
hidden = false

[editor.auto-pairs]
'(' = ')'
'{' = '}'
'[' = ']'
'"' = '"'
'`' = '`'
'<' = '>'

[editor.search]
smart-case = true
wrap-around = true

[editor.whitespace]
render = "all"

[editor.indent-guides]
render = true
character = "╎"
skip-levels = 1

[keys.normal]
# Custom key bindings can be added here
```

### Themes
List available themes:
```bash
hx --health
```

Change theme in config.toml or temporarily:
```
:theme dracula
```

### Language Configuration (`languages.toml`)
```toml
[[language]]
name = "python"
auto-format = true
formatter = { command = "black", args = ["--quiet", "-"] }

[[language]]
name = "javascript"
auto-format = true
formatter = { command = "prettier", args = ["--parser", "typescript"] }

[[language]]
name = "rust"
auto-format = true
```

## Useful Tips

1. **Help System**: Press `F1` or `:help` for built-in help
2. **Health Check**: Run `hx --health` to check LSP and tree-sitter status
3. **Tutor**: Run `hx --tutor` for an interactive tutorial
4. **Multiple Files**: Use `:open filename` to open additional files
5. **Buffer Navigation**: Use `:buffer-next` and `:buffer-previous` or `Space + b`
6. **File Explorer**: Use `Space + f` for file picker
7. **Command Palette**: Use `Space + ?` for command palette

## Common Workflows

### Opening and Editing Files
```bash
# Open file
hx myfile.py

# Navigate to function
/def function_name

# Edit function
# Use 'i' to enter insert mode, make changes, 'Esc' to exit

# Save and quit
:wq
```

### Working with Multiple Files
```bash
# Open directory
hx .

# Use file picker to open files
# Space + f to open file picker
# Navigate with j/k, Enter to open
```

### Programming Workflow
```bash
# Open project directory
hx .

# Open file with Space + f
# Use LSP features:
# - gd: Go to definition
# - gr: Go to references
# - Space + a: Code actions
# - Space + r: Rename symbol
```

## Troubleshooting

### LSP Not Working
1. Check if language server is installed: `hx --health`
2. Install missing language servers
3. Check language configuration in `languages.toml`

### Themes Not Loading
1. Ensure theme name is correct: `hx --health`
2. Check config.toml syntax
3. Try built-in themes first

### Performance Issues
1. Disable unnecessary features in config
2. Check if large files are causing issues
3. Update to latest version

## Resources

- [Official Documentation](https://docs.helix-editor.com/)
- [GitHub Repository](https://github.com/helix-editor/helix)
- [Community Wiki](https://github.com/helix-editor/helix/wiki)
- [Keymap Reference](https://docs.helix-editor.com/keymap.html)

## Quick Reference Card

| Action | Key |
|--------|-----|
| Insert mode | `i` |
| Visual mode | `v` |
| Save | `:w` |
| Quit | `:q` |
| Undo | `u` |
| Redo | `U` |
| Search | `/` |
| Go to line | `:123` |
| File picker | `Space + f` |
| Command palette | `Space + ?` |
| Help | `F1` |

---

*This guide covers the basics of Helix editor. For more advanced features and detailed documentation, visit the official Helix documentation.*
