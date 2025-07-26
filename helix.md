# Helix Editor - Complete Guide

## Overview

Helix is a modern, terminal-based text editor written in Rust. Think of it as a **terminal-based VS Code** with some key differences:
- **Modal editing**: Like Vim, but more intuitive
- **Built-in Language Server Protocol (LSP) support**: No extensions needed for basic functionality
- **Tree-sitter syntax highlighting**: Advanced syntax highlighting out of the box
- **Multiple selections and cursors**: Like VS Code's multi-cursor, but more powerful
- **Keyboard-first**: Everything can be done without a mouse
- **No configuration required**: Works great out of the box

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

### Verification

After installation, verify Helix is working:
```bash
hx --version
which hx
```

## Getting Started - For VS Code Users

### Opening Files (Like VS Code's File Explorer)

```bash
# Open a single file (like File > Open File in VS Code)
hx filename.txt

# Open a directory (like File > Open Folder in VS Code)
hx .

# Start without opening a file (like starting VS Code empty)
hx
```

### Understanding Modes (VS Code vs Helix)

In **VS Code**: You're always in "edit mode" - you can type anywhere, anytime.

In **Helix**: You switch between different modes:
- **Normal Mode** (default): Navigate and run commands (like having focus on VS Code's sidebar)
- **Insert Mode**: Actually type text (like having focus in VS Code's editor)
- **Select Mode**: Select text (like click-and-drag in VS Code)

## Your First File Edit - Step by Step

Let's create and edit a simple Python file together:

### Step 1: Create a New File
```bash
hx hello.py
```

### Step 2: Enter Insert Mode and Add Content
1. Press `i` to enter Insert Mode (cursor changes to a line)
2. Type this Python code:
```python
def greet(name):
    print(f"Hello, {name}!")

greet("World")
```
3. Press `Esc` to return to Normal Mode

### Step 3: Save the File
- Type `:w` and press `Enter` (like Ctrl+S in VS Code)

### Step 4: Run the File (if Python is installed)
- Type `:!python hello.py` and press `Enter`

Congratulations! You've just created, edited, and saved your first file in Helix!

## Essential Commands - VS Code Equivalents

### File Operations
| VS Code | Helix | Description |
|---------|-------|-------------|
| `Ctrl+S` | `:w` | Save file |
| `Ctrl+O` | `Space + f` | Open file picker |
| `Ctrl+W` | `:q` | Close file |
| `Ctrl+Shift+S` | `:w filename` | Save as |
| `Ctrl+N` | `:new` | New file |
| `Ctrl+Shift+N` | `:wq` | Save and quit |
| | `:q!` | Quit without saving |

### Navigation
| VS Code | Helix | Description |
|---------|-------|-------------|
| Arrow keys | `h j k l` | Move left, down, up, right |
| `Ctrl+Home` | `gg` | Go to start of file |
| `Ctrl+End` | `ge` | Go to end of file |
| `Ctrl+G` | `:123` | Go to line number |
| `Ctrl+F` | `/` | Find text forward |
| `Ctrl+F` then `Shift+Enter` | `?` | Search backward |
| `F3` | `n` | Find next |
| `Shift+F3` | `N` | Find previous |
| `Ctrl+Right` | `w` | Move to next word |
| `Ctrl+Left` | `b` | Move to previous word |
| | `e` | Move to end of word |
| `Page Up` | `Ctrl+u` | Page up |
| `Page Down` | `Ctrl+d` | Page down |

### Editing
| VS Code | Helix | Description |
|---------|-------|-------------|
| `Delete` | `x` | Delete character |
| `Ctrl+Z` | `u` | Undo |
| `Ctrl+Y` | `U` | Redo |
| `Ctrl+C` | `y` | Copy (after selecting) |
| `Ctrl+V` | `p` | Paste after cursor |
| | `P` | Paste before cursor |
| `Ctrl+A` | `%` | Select all |
| | `d` | Delete selection |
| | `c` | Change (delete and enter insert mode) |

### Insert Mode Variations
- `i` - Insert before cursor
- `a` - Insert after cursor
- `I` - Insert at beginning of line
- `A` - Insert at end of line
- `o` - Open new line below
- `O` - Open new line above

### Selection Mode
- `v` - Enter selection mode
- `V` - Select entire lines
- `Ctrl+v` - Block selection

## Hands-On Exercise 1: Basic Text Editing

Let's practice with a real example:

1. **Create a shopping list file:**
   ```bash
   hx shopping.txt
   ```

2. **Add items (Insert Mode):**
   - Press `i` to enter Insert Mode
   - Type:
   ```
   Shopping List:
   - Apples
   - Bread
   - Milk
   - Eggs
   ```
   - Press `Esc` to exit Insert Mode

3. **Navigate and edit:**
   - Use `j` and `k` to move up/down lines
   - Move to "Bread" line
   - Press `A` to go to end of line and enter Insert Mode
   - Add " (whole wheat)"
   - Press `Esc`

4. **Add a new item:**
   - Go to the last line (press `ge`)
   - Press `o` to create a new line below and enter Insert Mode
   - Type "- Cheese"
   - Press `Esc`

5. **Save and quit:**
   - Type `:wq` and press `Enter`

## Working with Multiple Files (Like VS Code Tabs)

### Opening Multiple Files
```bash
# Open multiple files at once
hx file1.txt file2.txt file3.txt

# Or open files one by one using the file picker
# Press Space + f, then navigate and press Enter
```

### Switching Between Files (Like VS Code Tabs)
| Action | Helix Command | VS Code Equivalent |
|--------|---------------|-------------------|
| Next file | `Space + b` then `j/k` to select | `Ctrl+Tab` |
| Previous file | `Space + b` then `j/k` to select | `Ctrl+Shift+Tab` |
| Close current file | `:q` | `Ctrl+W` |
| File picker | `Space + f` | `Ctrl+P` |

## Hands-On Exercise 2: Multi-File Project

Let's create a simple Python project:

1. **Create project directory and open it:**
   ```bash
   mkdir my_project
   cd my_project
   hx .
   ```

2. **Create main.py:**
   - Press `Space + f` to open file picker
   - Type `main.py` and press `Enter`
   - Press `i` and add:
   ```python
   from utils import calculate_area

   def main():
       radius = 5
       area = calculate_area(radius)
       print(f"Circle area: {area}")

   if __name__ == "__main__":
       main()
   ```
   - Press `Esc`, then `:w`

3. **Create utils.py:**
   - Type `:new utils.py` and press `Enter`
   - Press `i` and add:
   ```python
   import math

   def calculate_area(radius):
       return math.pi * radius ** 2
   ```
   - Press `Esc`, then `:w`

4. **Switch between files:**
   - Press `Space + b` to see buffer list
   - Use `j/k` to navigate, `Enter` to select

## Selection and Multi-Cursor (Like VS Code)

### Basic Selection
| VS Code | Helix | Description |
|---------|-------|-------------|
| Click and drag | `v` then move | Select text |
| `Ctrl+L` | `V` | Select whole line |
| `Ctrl+D` | Select word, then `;` | Select word under cursor |

### Multi-Cursor Magic
Helix's multi-cursor is more powerful than VS Code's:

1. **Select all instances of a word:**
   - Place cursor on a word
   - Press `*` to select the word
   - Press `n` repeatedly to add more instances
   - Make changes - they apply to all selections!

2. **Add cursors manually:**
   - Press `C` to add cursor below
   - Press `Alt+C` to add cursor above

### Advanced Multiple Selections
- `;` - Collapse selections to cursor
- `Alt+;` - Flip selections

## Hands-On Exercise 3: Multi-Cursor Editing

Let's practice with a CSS file:

1. **Create styles.css:**
   ```bash
   hx styles.css
   ```

2. **Add CSS content:**
   ```css
   .button {
       background-color: blue;
       color: white;
       padding: 10px;
   }

   .header {
       background-color: blue;
       color: white;
       font-size: 24px;
   }

   .footer {
       background-color: blue;
       color: white;
       text-align: center;
   }
   ```

3. **Change all "blue" to "green":**
   - Place cursor on any "blue"
   - Press `*` to select the word
   - Press `n` to select next instance (repeat for all)
   - Press `c` to change (deletes and enters Insert Mode)
   - Type "green"
   - Press `Esc` - all instances change!

## Search and Replace (Like VS Code Find/Replace)

### Basic Search
| VS Code | Helix | Description |
|---------|-------|-------------|
| `Ctrl+F` | `/` | Search forward |
| `Ctrl+F` then `Shift+Enter` | `?` | Search backward |
| `F3` | `n` | Next result |
| `Shift+F3` | `N` | Previous result |

### Find and Replace
| VS Code | Helix | Description |
|---------|-------|-------------|
| `Ctrl+H` | `:%s/old/new/g` | Replace all in file |
| Replace in selection | Select first, then `:s/old/new/g` | Replace in selection |

## Hands-On Exercise 4: Search and Replace

1. **Create a config file:**
   ```
   server_host=localhost
   server_port=8080
   database_host=localhost
   database_port=5432
   cache_host=localhost
   cache_port=6379
   ```

2. **Replace all "localhost" with "production.server.com":**
   - Type `:%s/localhost/production.server.com/g`
   - Press `Enter`

3. **Search for specific ports:**
   - Type `/8080` to find the server port
   - Press `n` to find next occurrence

## Language Server Protocol (LSP) - Like IntelliSense

Helix has built-in LSP support (no extensions needed!):

### LSP Features
| Feature | Helix Command | VS Code Equivalent |
|---------|---------------|-------------------|
| Go to definition | `gd` | `F12` |
| Find references | `gr` | `Shift+F12` |
| Rename symbol | `Space + r` | `F2` |
| Code actions | `Space + a` | `Ctrl+.` |
| Show hover info | `Space + k` | Hover mouse |

### Installing Language Servers

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

## Hands-On Exercise 5: Using LSP Features

If you have Python LSP installed:

1. **Open a Python file with functions:**
   ```python
   def calculate_tax(amount, rate):
       return amount * rate

   def calculate_total(amount, tax_rate):
       tax = calculate_tax(amount, tax_rate)
       return amount + tax

   # Usage
   total = calculate_total(100, 0.08)
   print(total)
   ```

2. **Try LSP features:**
   - Place cursor on `calculate_tax` in the `calculate_total` function
   - Press `gd` to go to definition
   - Press `gr` to find all references
   - Try renaming: place cursor on function name, press `Space + r`

## Tree-sitter Syntax Highlighting

Helix uses tree-sitter for advanced syntax highlighting. Install grammars:
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
# "C-s" = ":w"  # Ctrl+S to save (more VS Code-like)
```

### Themes (Like VS Code Color Themes)
```bash
# See available themes
hx --health

# Change theme temporarily
:theme dracula

# Or edit ~/.config/helix/config.toml
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

## File Explorer and Navigation (Like VS Code Sidebar)
- `Space + f`: File picker (like Ctrl+P in VS Code)
- `Space + b`: Buffer list (like open tabs)
- `Space + ?`: Command palette (like Ctrl+Shift+P)

## Getting Help

| Need | Command | VS Code Equivalent |
|------|---------|-------------------|
| Interactive tutorial | `hx --tutor` | Built-in tutorials |
| Help system | `F1` or `:help` | `F1` |
| Command palette | `Space + ?` | `Ctrl+Shift+P` |
| Check health | `hx --health` | Extension status |

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

## Final Challenge: Complete Workflow

Create a simple web project:

1. **Setup:**
   ```bash
   mkdir web_project
   cd web_project
   hx .
   ```

2. **Create index.html:**
   - Use file picker (`Space + f`) to create `index.html`
   - Add basic HTML structure
   - Use multi-cursor to add multiple `<div>` elements

3. **Create style.css:**
   - Create CSS file
   - Use search and replace to update color schemes
   - Practice navigation between files

4. **Create script.js:**
   - Add JavaScript functions
   - Use LSP features if available (go to definition, etc.)

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

## Quick Reference for VS Code Users

### Most Important Commands to Remember:
- `i` - Start typing (Insert Mode)
- `Esc` - Stop typing (Normal Mode)
- `:w` - Save file
- `:q` - Quit
- `Space + f` - Open file (like Ctrl+P)
- `Space + ?` - Command palette (like Ctrl+Shift+P)
- `/` - Search (like Ctrl+F)
- `u` - Undo (like Ctrl+Z)

### When You're Stuck:
1. Press `Esc` to get back to Normal Mode
2. Press `F1` for help
3. Type `:q!` to quit without saving if needed

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

## Resources

- [Official Documentation](https://docs.helix-editor.com/)
- [GitHub Repository](https://github.com/helix-editor/helix)
- [Community Wiki](https://github.com/helix-editor/helix/wiki)
- [Keymap Reference](https://docs.helix-editor.com/keymap.html)

## Graduation: You're Now a Helix User!

Congratulations! You've learned:
- ✅ Modal editing concepts
- ✅ File operations and navigation
- ✅ Multi-file workflows
- ✅ Selection and multi-cursor editing
- ✅ Search and replace
- ✅ LSP features
- ✅ Basic customization

## Next Steps

1. **Practice daily**: Use Helix for your regular coding tasks
2. **Learn more shortcuts**: Run `hx --tutor` for advanced techniques
3. **Customize**: Set up your `config.toml` file
4. **Install language servers**: For your favorite programming languages
5. **Join the community**: Check out the [Helix GitHub](https://github.com/helix-editor/helix)

---

*Happy editing! Remember: Helix might feel different at first, but once you get the hang of it, you'll appreciate its efficiency and power. Give yourself a week of regular use to build muscle memory.*