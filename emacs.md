# Emacs Editor - Complete Guide

## Overview

Emacs is a powerful, extensible text editor that has been around since the 1970s. Think of it as a **highly customizable development environment** with some key differences from VS Code:
- **Keyboard-centric**: Everything can be done with keyboard shortcuts
- **Extensible**: Customize everything with Emacs Lisp
- **Self-documenting**: Built-in help system for everything
- **Buffers and windows**: Different concepts from VS Code tabs and panes
- **Modal-less editing**: Unlike Vim, you can type immediately
- **Living environment**: Can run shell, email, games, and more inside Emacs

## Installation

### Ubuntu/Debian
```bash
sudo apt update && sudo apt install emacs -y
```

### Alternative Installation Methods

#### Latest Version (Snap)
```bash
sudo snap install emacs --classic
```

#### Arch Linux
```bash
pacman -S emacs
```

#### macOS (Homebrew)
```bash
brew install emacs
# Or for GUI version
brew install --cask emacs
```

#### Windows
- Download from [GNU Emacs website](https://www.gnu.org/software/emacs/download.html)
- Or use Chocolatey: `choco install emacs`

### Verification

After installation, verify Emacs is working:
```bash
emacs --version
which emacs
```

## Getting Started - For VS Code Users

### Launching Emacs

```bash
# Launch GUI version (like opening VS Code)
emacs

# Launch terminal version (like VS Code in terminal)
emacs -nw

# Launch without configuration (clean slate)
emacs -Q

# Launch terminal version without configuration
emacs -Q -nw
```

### Understanding Emacs Concepts vs VS Code

| VS Code Concept | Emacs Concept | Description |
|----------------|---------------|-------------|
| Files/Tabs | Buffers | Open files are called buffers |
| Panes/Split View | Windows | Screen divisions are called windows |
| Workspace | Frame | The entire Emacs instance |
| Extensions | Packages | Add-ons to extend functionality |
| Settings | Configuration | Stored in `.emacs` or `init.el` |
| Command Palette | M-x | Execute commands by name |

### Key Notation in Emacs

- `C-` means Ctrl (e.g., `C-x` = Ctrl+x)
- `M-` means Alt/Meta (e.g., `M-x` = Alt+x)
- `S-` means Shift (e.g., `S-Tab` = Shift+Tab)
- Sequential keys: `C-x C-f` means Ctrl+x, then Ctrl+f

## Your First File Edit - Step by Step

Let's create and edit a simple Python file:

### Step 1: Launch Emacs
```bash
emacs
```

### Step 2: Open a New File
1. Press `C-x C-f` (Ctrl+x, then Ctrl+f)
2. Type `hello.py` in the minibuffer (bottom of screen)
3. Press `Enter`

### Step 3: Add Content
Unlike modal editors, you can start typing immediately:
```python
def greet(name):
    print(f"Hello, {name}!")

greet("World")
```

### Step 4: Save the File
- Press `C-x C-s` (Ctrl+x, then Ctrl+s)

### Step 5: Run the File
- Press `M-!` (Alt+!) to run shell command
- Type `python hello.py` and press `Enter`

### Step 6: Exit Emacs
- Press `C-x C-c` (Ctrl+x, then Ctrl+c)

Congratulations! You've just created, edited, and saved your first file in Emacs!

## Essential Commands - VS Code Equivalents

### File Operations
| VS Code | Emacs | Description |
|---------|-------|-------------|
| `Ctrl+N` | `C-x C-f` | New/Open file |
| `Ctrl+O` | `C-x C-f` | Open file |
| `Ctrl+S` | `C-x C-s` | Save file |
| `Ctrl+Shift+S` | `C-x C-w` | Save as |
| `Ctrl+W` | `C-x k` | Close file/buffer |
| `Ctrl+Shift+T` | `C-x b` | Switch between files/buffers |
| `Ctrl+Shift+N` | `C-x C-c` | Close application |

### Navigation
| VS Code | Emacs | Description |
|---------|-------|-------------|
| Arrow keys | `C-p C-n C-b C-f` | Move up, down, left, right |
| `Ctrl+Home` | `M-<` | Go to start of file |
| `Ctrl+End` | `M->` | Go to end of file |
| `Ctrl+G` | `M-g g` | Go to line number |
| `Ctrl+F` | `C-s` | Search forward |
| `Ctrl+H` | `M-%` | Find and replace |
| `Page Up` | `M-v` | Page up |
| `Page Down` | `C-v` | Page down |
| `Ctrl+Right` | `M-f` | Move forward by word |
| `Ctrl+Left` | `M-b` | Move backward by word |
| `Home` | `C-a` | Move to beginning of line |
| `End` | `C-e` | Move to end of line |

### Editing
| VS Code | Emacs | Description |
|---------|-------|-------------|
| `Ctrl+Z` | `C-/` or `C-x u` | Undo |
| `Ctrl+Y` | `C-g` then `C-/` | Redo |
| `Ctrl+C` | `M-w` | Copy |
| `Ctrl+X` | `C-w` | Cut |
| `Ctrl+V` | `C-y` | Paste |
| `Ctrl+A` | `C-x h` | Select all |
| `Delete` | `C-d` | Delete character forward |
| `Backspace` | `DEL` | Delete character backward |
| `Ctrl+K` | `C-k` | Delete to end of line |
| `Ctrl+Shift+K` | `C-S-backspace` | Delete entire line |

### Window Management
| VS Code | Emacs | Description |
|---------|-------|-------------|
| `Ctrl+\` | `C-x 3` | Split vertically |
| `Ctrl+Shift+\` | `C-x 2` | Split horizontally |
| `Ctrl+W` | `C-x 0` | Close current pane |
| `Ctrl+K Ctrl+W` | `C-x 1` | Close other panes |
| `Ctrl+K Arrow` | `C-x o` | Switch between panes |

## Hands-On Exercise 1: Basic Text Editing

Let's practice with a shopping list:

1. **Launch Emacs:**
   ```bash
   emacs
   ```

2. **Create a new file:**
   - Press `C-x C-f`
   - Type `shopping.txt`
   - Press `Enter`

3. **Add content (you can type immediately):**
   ```
   Shopping List:
   - Apples
   - Bread
   - Milk
   - Eggs
   ```

4. **Navigate and edit:**
   - Use `C-p` and `C-n` to move up/down lines
   - Move to "Bread" line using `C-n`
   - Press `C-e` to go to end of line
   - Type " (whole wheat)"

5. **Add a new item:**
   - Press `C-e` to go to end of last line
   - Press `Enter` to create new line
   - Type "- Cheese"

6. **Save and continue:**
   - Press `C-x C-s` to save

## Working with Multiple Files (Like VS Code Tabs)

### Opening Multiple Files
```bash
# Open multiple files at once
emacs file1.txt file2.txt file3.txt

# Or open files one by one
# C-x C-f for each file
```

### Buffer Management (Like VS Code Tabs)
| Action | Emacs Command | VS Code Equivalent |
|--------|---------------|-------------------|
| List all open files | `C-x C-b` | View all tabs |
| Switch to buffer | `C-x b` | `Ctrl+Tab` |
| Next buffer | `C-x →` | `Ctrl+PageDown` |
| Previous buffer | `C-x ←` | `Ctrl+PageUp` |
| Close buffer | `C-x k` | `Ctrl+W` |
| Switch to recent buffer | `C-x b` then `Enter` | `Ctrl+Tab` |

## Hands-On Exercise 2: Multi-File Project

Let's create a simple Python project:

1. **Launch Emacs:**
   ```bash
   emacs
   ```

2. **Create main.py:**
   - Press `C-x C-f`
   - Type `main.py` and press `Enter`
   - Add this content:
   ```python
   from utils import calculate_area

   def main():
       radius = 5
       area = calculate_area(radius)
       print(f"Circle area: {area}")

   if __name__ == "__main__":
       main()
   ```
   - Press `C-x C-s` to save

3. **Create utils.py:**
   - Press `C-x C-f`
   - Type `utils.py` and press `Enter`
   - Add this content:
   ```python
   import math

   def calculate_area(radius):
       return math.pi * radius ** 2
   ```
   - Press `C-x C-s` to save

4. **Switch between files:**
   - Press `C-x b` to switch buffers
   - Type the buffer name or use tab completion
   - Press `Enter`

5. **View all open buffers:**
   - Press `C-x C-b` to see buffer list
   - Use `C-x o` to switch to buffer list window
   - Use `C-p` and `C-n` to navigate
   - Press `Enter` to open selected buffer

## Selection and Region (Like VS Code Selection)

### Basic Selection
| VS Code | Emacs | Description |
|---------|-------|-------------|
| Click and drag | `C-Space` then move | Set mark and select |
| `Ctrl+L` | `C-a C-Space C-e` | Select whole line |
| `Ctrl+D` | `M-@` | Select word |
| `Ctrl+Shift+L` | `C-x h` | Select all |

### Working with Regions (Selected Text)
- `C-Space` - Set mark (start selection)
- Move cursor to extend selection
- `C-w` - Cut region
- `M-w` - Copy region
- `C-y` - Paste (yank)
- `C-g` - Cancel selection

## Hands-On Exercise 3: Selection and Editing

Let's practice with a CSS file:

1. **Create styles.css:**
   - Press `C-x C-f`
   - Type `styles.css` and press `Enter`

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

3. **Select and replace text:**
   - Move cursor to first "blue"
   - Press `C-Space` to set mark
   - Press `M-f` to select the word
   - Type "green" to replace
   - Repeat for other instances

## Search and Replace (Like VS Code Find/Replace)

### Basic Search
| VS Code | Emacs | Description |
|---------|-------|-------------|
| `Ctrl+F` | `C-s` | Search forward |
| `F3` | `C-s` (repeat) | Find next |
| `Shift+F3` | `C-r` | Search backward |
| `Escape` | `C-g` | Cancel search |

### Interactive Search
- `C-s` - Start incremental search
- Type search term (matches as you type)
- `C-s` again - Find next occurrence
- `C-r` - Search backward
- `Enter` - End search at current position
- `C-g` - Cancel and return to start

### Find and Replace
| VS Code | Emacs | Description |
|---------|-------|-------------|
| `Ctrl+H` | `M-%` | Query replace |
| | `M-x replace-string` | Replace all without asking |

### Replace Commands
- `M-%` - Query replace (asks for each replacement)
  - `y` - Yes, replace this one
  - `n` - No, skip this one
  - `!` - Replace all remaining
  - `q` - Quit replacing

## Hands-On Exercise 4: Search and Replace

1. **Create a config file:**
   - Press `C-x C-f`
   - Type `config.txt` and press `Enter`
   - Add:
   ```
   server_host=localhost
   server_port=8080
   database_host=localhost
   database_port=5432
   cache_host=localhost
   cache_port=6379
   ```

2. **Replace all "localhost" with "production.server.com":**
   - Press `M-%`
   - Type `localhost` and press `Enter`
   - Type `production.server.com` and press `Enter`
   - Press `!` to replace all

3. **Search for specific text:**
   - Press `C-s`
   - Type `8080`
   - Press `Enter` when found

## Menu System and Help (Like VS Code Command Palette)

### Accessing Menus
- `F10` - Access menu bar (in terminal version)
- `M-x` - Execute command by name (like VS Code Command Palette)
- `C-h` - Help prefix

### Help System (Like VS Code Help)
| Need | Emacs Command | Description |
|------|---------------|-------------|
| Command help | `C-h f` | Describe function |
| Key binding help | `C-h k` | Describe key |
| Variable help | `C-h v` | Describe variable |
| Mode help | `C-h m` | Describe current mode |
| Tutorial | `C-h t` | Built-in tutorial |
| Info manual | `C-h i` | Browse documentation |
| Apropos | `C-h a` | Search help by keyword |

## Package Management (Like VS Code Extensions)

### Built-in Package Manager
- `M-x package-list-packages` - Browse available packages
- `M-x package-install` - Install a package
- `M-x package-delete` - Remove a package

### Popular Packages for Modern Development
```elisp
;; Add to your configuration
(require 'package)
(add-to-list 'package-archives '("melpa" . "https://melpa.org/packages/") t)
(package-initialize)

;; Popular packages to consider:
;; - company (auto-completion)
;; - helm or ivy (better file/buffer switching)
;; - magit (Git integration)
;; - projectile (project management)
;; - lsp-mode (Language Server Protocol)
```

## Configuration (Like VS Code Settings)

### Configuration Files
Emacs configuration is stored in:
- `~/.emacs` - Traditional config file
- `~/.emacs.d/init.el` - Modern approach
- `~/.config/emacs/init.el` - XDG compliant

### Basic Configuration Example
```elisp
;; Basic Emacs configuration
;; Save in ~/.emacs.d/init.el

;; Package management
(require 'package)
(add-to-list 'package-archives '("melpa" . "https://melpa.org/packages/") t)
(package-initialize)

;; Basic settings
(setq inhibit-startup-message t)    ; Disable startup screen
(tool-bar-mode -1)                  ; Disable toolbar
(menu-bar-mode -1)                  ; Disable menu bar
(scroll-bar-mode -1)                ; Disable scroll bar
(global-display-line-numbers-mode 1) ; Show line numbers
(setq make-backup-files nil)        ; Don't create backup files

;; Better defaults
(setq-default indent-tabs-mode nil) ; Use spaces instead of tabs
(setq-default tab-width 4)          ; Set tab width
(electric-pair-mode 1)              ; Auto-close parentheses
(show-paren-mode 1)                 ; Highlight matching parentheses

;; Key bindings (more VS Code-like)
(global-set-key (kbd "C-z") 'undo)
(global-set-key (kbd "C-s") 'save-buffer)
(global-set-key (kbd "C-f") 'isearch-forward)

;; Theme
(load-theme 'wombat t)              ; Dark theme
```

## Programming Features (Like VS Code IntelliSense)

### Language Support
Emacs has built-in support for many languages and can be extended:

#### Python
```elisp
;; Python configuration
(add-hook 'python-mode-hook
          (lambda ()
            (setq python-indent-offset 4)))
```

#### JavaScript/Web Development
```elisp
;; JavaScript configuration
(setq js-indent-level 2)
```

### Language Server Protocol (LSP)
Install `lsp-mode` for modern IDE features:
```elisp
;; LSP configuration
(use-package lsp-mode
  :hook ((python-mode . lsp)
         (js-mode . lsp))
  :commands lsp)
```

## Hands-On Exercise 5: Programming Workflow

Let's work with a Python project:

1. **Create a Python file:**
   - Press `C-x C-f`
   - Type `calculator.py` and press `Enter`

2. **Add Python code:**
   ```python
   def add(a, b):
       """Add two numbers."""
       return a + b

   def subtract(a, b):
       """Subtract two numbers."""
       return a - b

   def multiply(a, b):
       """Multiply two numbers."""
       return a * b

   def divide(a, b):
       """Divide two numbers."""
       if b != 0:
           return a / b
       else:
           return "Cannot divide by zero"

   # Test the functions
   print(add(5, 3))
   print(subtract(10, 4))
   print(multiply(6, 7))
   print(divide(15, 3))
   ```

3. **Navigate the code:**
   - Use `M-f` and `M-b` to move by words
   - Use `C-M-f` and `C-M-b` to move by expressions
   - Use `C-M-a` and `C-M-e` to move by functions

4. **Run the code:**
   - Press `M-!`
   - Type `python calculator.py`
   - Press `Enter`

## Window and Frame Management

### Window Operations (Like VS Code Panes)
| Action | Emacs Command | Description |
|--------|---------------|-------------|
| Split horizontally | `C-x 2` | Create pane below |
| Split vertically | `C-x 3` | Create pane to right |
| Switch window | `C-x o` | Move to next pane |
| Close current window | `C-x 0` | Close current pane |
| Close other windows | `C-x 1` | Close all other panes |
| Balance windows | `C-x +` | Make all panes equal size |

### Frame Operations (Like VS Code Windows)
| Action | Emacs Command | Description |
|--------|---------------|-------------|
| New frame | `C-x 5 2` | Open new window |
| Switch frame | `C-x 5 o` | Switch between windows |
| Close frame | `C-x 5 0` | Close current window |

## Hands-On Exercise 6: Window Management

1. **Open a file:**
   - Press `C-x C-f`
   - Open any text file

2. **Split the window:**
   - Press `C-x 2` to split horizontally
   - Press `C-x 3` to split vertically

3. **Navigate between windows:**
   - Press `C-x o` to switch between panes
   - Open different files in each pane

4. **Manage windows:**
   - Press `C-x 1` to close all but current window
   - Practice splitting and switching

## Shell Integration (Like VS Code Terminal)

### Running Shell Commands
| Action | Emacs Command | Description |
|--------|---------------|-------------|
| Run shell command | `M-!` | Execute command and show output |
| Run command on region | `M-|` | Pipe selected text through command |
| Start shell | `M-x shell` | Open shell buffer |
| Start terminal | `M-x term` | Open terminal emulator |

### Compilation and Building
- `M-x compile` - Run build command
- `C-x `` - Jump to next error
- `M-x grep` - Search files with grep

## Customization and Themes

### Changing Themes
```elisp
;; List available themes
M-x customize-themes

;; Load a theme
(load-theme 'theme-name t)

;; Popular themes:
;; - wombat (dark)
;; - tango-dark (dark)
;; - light-blue (light)
;; - deeper-blue (dark)
```

### Customizing Key Bindings
```elisp
;; Custom key bindings
(global-set-key (kbd "C-c c") 'compile)
(global-set-key (kbd "C-c g") 'grep)
(global-set-key (kbd "C-x g") 'magit-status)
```

## Troubleshooting

### Common Issues

#### Emacs Feels Slow
1. Check your configuration for heavy packages
2. Use `emacs -Q` to test without configuration
3. Consider using `emacs --daemon` for faster startup

#### Key Bindings Not Working
1. Check if keys are bound to other functions: `C-h k`
2. Use `C-h b` to see all current bindings
3. Check for conflicting packages

#### Configuration Errors
1. Use `emacs --debug-init` to see startup errors
2. Comment out sections of config to isolate issues
3. Check the `*Messages*` buffer for errors

### Getting Help
- `C-h t` - Built-in tutorial
- `C-h i` - Info documentation
- `M-x doctor` - Emacs therapist (for fun!)
- [EmacsWiki](https://www.emacswiki.org/) - Community documentation

## Quick Reference for VS Code Users

### Most Important Commands to Remember:
- `C-x C-f` - Open file (like Ctrl+O)
- `C-x C-s` - Save file (like Ctrl+S)
- `C-x C-c` - Exit Emacs
- `C-x b` - Switch buffer (like Ctrl+Tab)
- `C-s` - Search (like Ctrl+F)
- `C-/` - Undo (like Ctrl+Z)
- `M-x` - Command palette (like Ctrl+Shift+P)
- `C-g` - Cancel current command (like Escape)

### When You're Stuck:
1. Press `C-g` to cancel current command
2. Press `C-h ?` for help options
3. Use `M-x recover-session` if Emacs crashed
4. Press `C-x C-c` to exit if needed

## Advanced Features

### Org Mode (Like Notion/OneNote)
Emacs includes Org mode for note-taking, planning, and documentation:
```
* TODO Learn Emacs
** DONE Install Emacs
** TODO Configure Emacs
** TODO Learn key bindings
* Notes
** Emacs is powerful
** Takes time to learn
```

### Version Control (Git Integration)
- `M-x vc-next-action` - Basic version control
- Install Magit for advanced Git features
- `C-x v =` - Show diff
- `C-x v l` - Show log

### Email and News
- `M-x gnus` - Read news and email
- `M-x rmail` - Read mail

## Final Challenge: Complete Development Workflow

Create a complete web development setup:

1. **Setup project structure:**
   ```bash
   mkdir web_project
   cd web_project
   emacs .
   ```

2. **Create multiple files:**
   - `index.html` - HTML structure
   - `style.css` - Styling
   - `script.js` - JavaScript functionality
   - `README.md` - Documentation

3. **Use advanced features:**
   - Split windows to view multiple files
   - Use search and replace across files
   - Run shell commands to test
   - Use version control commands

4. **Customize your setup:**
   - Add useful key bindings
   - Install helpful packages
   - Configure for your workflow

## Graduation: You're Now an Emacs User!

Congratulations! You've learned:
- ✅ Basic Emacs concepts and terminology
- ✅ File operations and navigation
- ✅ Buffer and window management
- ✅ Search and replace functionality
- ✅ Basic programming workflow
- ✅ Configuration and customization
- ✅ Help system usage

## Next Steps

1. **Practice daily**: Use Emacs for your regular tasks
2. **Learn incrementally**: Master one feature at a time
3. **Customize gradually**: Add configuration as you need it
4. **Join the community**: Visit [r/emacs](https://reddit.com/r/emacs) and [EmacsWiki](https://emacswiki.org)
5. **Explore packages**: Try popular packages like Helm, Magit, and Company
6. **Read the manual**: `C-h i` for comprehensive documentation

## Resources

- [GNU Emacs Manual](https://www.gnu.org/software/emacs/manual/)
- [EmacsWiki](https://www.emacswiki.org/) - Community documentation
- [Awesome Emacs](https://github.com/emacs-tw/awesome-emacs) - Curated packages
- [Emacs Rocks](http://emacsrocks.com/) - Video tutorials
- [Mastering Emacs](https://www.masteringemacs.org/) - Advanced tutorials

## Quick Reference Card

| Action | Key | VS Code Equivalent |
|--------|-----|-------------------|
| Open file | `C-x C-f` | `Ctrl+O` |
| Save file | `C-x C-s` | `Ctrl+S` |
| Switch buffer | `C-x b` | `Ctrl+Tab` |
| Search | `C-s` | `Ctrl+F` |
| Replace | `M-%` | `Ctrl+H` |
| Undo | `C-/` | `Ctrl+Z` |
| Copy | `M-w` | `Ctrl+C` |
| Cut | `C-w` | `Ctrl+X` |
| Paste | `C-y` | `Ctrl+V` |
| Select all | `C-x h` | `Ctrl+A` |
| Go to line | `M-g g` | `Ctrl+G` |
| Command palette | `M-x` | `Ctrl+Shift+P` |
| Help | `C-h` | `F1` |
| Exit | `C-x C-c` | `Alt+F4` |

---

*Happy editing! Emacs has a steep learning curve, but it's incredibly rewarding. Remember: Emacs is not just an editor, it's a way of life. Take your time, be patient with yourself, and enjoy the journey of mastering one of the most powerful text editors ever created.*