# Neovim Usage Guide for VS Code Users

Welcome to Neovim! This guide will help you transition from VS Code to Neovim by explaining concepts in familiar terms and providing hands-on exercises.

## 🎯 What is Neovim?

Think of Neovim as a **highly customizable, terminal-based VS Code** with some key differences:
- **Modal editing**: Different modes for different tasks
- **Extensible**: Plugins for everything (like VS Code extensions, but more powerful)
- **Keyboard-first**: Everything can be done without a mouse
- **Lightweight**: Fast startup and low resource usage
- **Vim-compatible**: Based on the legendary Vim editor

## 🚀 Getting Started

### Installation (Quick Setup)
```bash
# Ubuntu/Debian
sudo apt install neovim

# macOS
brew install neovim

# Arch Linux
sudo pacman -S neovim

# Or use snap
sudo snap install nvim --classic
```

### Opening Files (Like VS Code's File Explorer)

```bash
# Open a single file (like File > Open File in VS Code)
nvim myfile.txt

# Open a directory (like File > Open Folder in VS Code)
nvim .

# Start Neovim without a file (like starting VS Code empty)
nvim
```

### Understanding Modes (VS Code vs Neovim)

In **VS Code**: You're always in "edit mode" - you can type anywhere, anytime.

In **Neovim**: You switch between different modes:
- **Normal Mode** (default): Navigate and run commands (like having focus on VS Code's sidebar)
- **Insert Mode**: Actually type text (like having focus in VS Code's editor)
- **Visual Mode**: Select text (like click-and-drag in VS Code)
- **Command Mode**: Run commands (like VS Code's Command Palette)

## 📝 Your First File Edit - Step by Step

Let's create and edit a simple Python file together:

### Step 1: Create a New File
```bash
nvim hello.py
```

### Step 2: Enter Insert Mode and Add Content
1. Press `i` to enter Insert Mode (you'll see `-- INSERT --` at the bottom)
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

### Step 5: Quit Neovim
- Type `:q` and press `Enter`

Congratulations! You've just created, edited, saved, and run your first file in Neovim!

## 🎮 Essential Commands - VS Code Equivalents

### File Operations
| VS Code | Neovim | Description |
|---------|--------|-------------|
| `Ctrl+S` | `:w` | Save file |
| `Ctrl+O` | `:e filename` | Open file |
| `Ctrl+W` | `:q` | Close file |
| `Ctrl+Shift+S` | `:w filename` | Save as |
| `Ctrl+N` | `:enew` | New file |
| `Ctrl+Shift+P` | `:` | Command mode |

### Navigation
| VS Code | Neovim | Description |
|---------|--------|-------------|
| Arrow keys | `h j k l` | Move cursor (left, down, up, right) |
| `Ctrl+Home` | `gg` | Go to start of file |
| `Ctrl+End` | `G` | Go to end of file |
| `Ctrl+G` | `:123` | Go to line number |
| `Ctrl+F` | `/` | Find text |
| `F3` | `n` | Find next |
| `Shift+F3` | `N` | Find previous |

### Editing
| VS Code | Neovim | Description |
|---------|--------|-------------|
| `Delete` | `x` | Delete character |
| `Ctrl+Z` | `u` | Undo |
| `Ctrl+Y` | `Ctrl+r` | Redo |
| `Ctrl+C` | `y` | Copy (yank) |
| `Ctrl+V` | `p` | Paste |
| `Ctrl+A` | `ggVG` | Select all |

## 🎯 Hands-On Exercise 1: Basic Text Editing

Let's practice with a real example:

1. **Create a shopping list file:**
   ```bash
   nvim shopping.txt
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
   - Go to the last line (press `G`)
   - Press `o` to create a new line below and enter Insert Mode
   - Type "- Cheese"
   - Press `Esc`

5. **Save and quit:**
   - Type `:wq` and press `Enter`

## 🔍 Working with Multiple Files (Like VS Code Tabs)

### Opening Multiple Files
```bash
# Open multiple files at once
nvim file1.txt file2.txt file3.txt

# Or open files one by one
:e file2.txt
:e file3.txt
```

### Switching Between Files (Like VS Code Tabs)
| Action | Neovim Command | VS Code Equivalent |
|--------|----------------|-------------------|
| Next buffer | `:bn` or `:bnext` | `Ctrl+Tab` |
| Previous buffer | `:bp` or `:bprev` | `Ctrl+Shift+Tab` |
| List all buffers | `:ls` | View all open tabs |
| Switch to buffer | `:b filename` | Click on tab |
| Close current buffer | `:bd` | `Ctrl+W` |

### Window Splits (Like VS Code Split Editor)
| Action | Neovim Command | VS Code Equivalent |
|--------|----------------|-------------------|
| Split horizontally | `:split` or `:sp` | Split editor down |
| Split vertically | `:vsplit` or `:vsp` | Split editor right |
| Switch between windows | `Ctrl+w` then `h/j/k/l` | Click on split |
| Close current window | `:q` | Close split |

## 🎯 Hands-On Exercise 2: Multi-File Project with Splits

Let's create a simple Python project:

1. **Create project directory and open it:**
   ```bash
   mkdir my_project
   cd my_project
   nvim main.py
   ```

2. **Create main.py:**
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

3. **Open utils.py in a vertical split:**
   - Type `:vsp utils.py` and press `Enter`
   - Press `i` and add:
   ```python
   import math

   def calculate_area(radius):
       return math.pi * radius ** 2
   ```
   - Press `Esc`, then `:w`

4. **Navigate between splits:**
   - Press `Ctrl+w` then `h` to go to left window
   - Press `Ctrl+w` then `l` to go to right window

5. **Test the project:**
   - In main.py window, type `:!python main.py`

## 🎨 Visual Mode and Selection (Like VS Code Selection)

### Basic Selection
| VS Code | Neovim | Description |
|---------|--------|-------------|
| Click and drag | `v` then move | Select characters |
| `Ctrl+L` | `V` | Select whole lines |
| `Ctrl+Shift+Alt+Arrow` | `Ctrl+v` | Block selection |
| `Ctrl+D` | `*` | Select word under cursor |

### Advanced Selection
- `viw` - Select inner word (like double-click in VS Code)
- `vip` - Select inner paragraph
- `vi"` - Select inside quotes
- `va"` - Select around quotes (including quotes)
- `vit` - Select inside HTML/XML tags

## 🎯 Hands-On Exercise 3: Visual Mode and Text Objects

Let's practice with an HTML file:

1. **Create index.html:**
   ```bash
   nvim index.html
   ```

2. **Add HTML content:**
   ```html
   <!DOCTYPE html>
   <html>
   <head>
       <title>My Website</title>
   </head>
   <body>
       <h1>Welcome to my site</h1>
       <p>This is a paragraph with "quoted text" inside.</p>
       <div class="container">
           <p>Another paragraph here.</p>
       </div>
   </body>
   </html>
   ```

3. **Practice text objects:**
   - Place cursor on "quoted text"
   - Press `vi"` to select inside quotes
   - Press `va"` to select including quotes
   - Place cursor inside `<div>` tag
   - Press `vit` to select content inside div
   - Press `vat` to select entire div element

4. **Practice line selection:**
   - Press `V` to select current line
   - Press `j` or `k` to extend selection
   - Press `d` to delete selected lines
   - Press `u` to undo

## 🔧 Search and Replace (Like VS Code Find/Replace)

### Basic Search
| VS Code | Neovim | Description |
|---------|--------|-------------|
| `Ctrl+F` | `/pattern` | Search forward |
| `Ctrl+F` then up arrow | `?pattern` | Search backward |
| `F3` | `n` | Next result |
| `Shift+F3` | `N` | Previous result |
| `Ctrl+H` | `:%s/old/new/g` | Replace all |

### Advanced Search and Replace
```vim
" Replace all occurrences in file
:%s/old/new/g

" Replace with confirmation
:%s/old/new/gc

" Replace only in current line
:s/old/new/g

" Replace in visual selection (select first, then:)
:'<,'>s/old/new/g

" Case insensitive search
/pattern\c

" Use regex
:%s/\d\+/NUMBER/g  " Replace all numbers with "NUMBER"
```

## 🎯 Hands-On Exercise 4: Search and Replace

1. **Create a config file:**
   ```bash
   nvim config.txt
   ```

2. **Add configuration:**
   ```
   server_host=localhost
   server_port=8080
   database_host=localhost
   database_port=5432
   cache_host=localhost
   cache_port=6379
   debug_mode=true
   log_level=info
   ```

3. **Search and replace:**
   - Replace all "localhost" with "production.server.com":
     ```
     :%s/localhost/production.server.com/g
     ```
   - Search for port numbers:
     ```
     /\d\d\d\d
     ```
   - Replace "true" with "false" with confirmation:
     ```
     :%s/true/false/gc
     ```

## 🛠️ Basic Configuration (Like VS Code Settings)

### Creating Your First Config
Neovim config is stored in `~/.config/nvim/init.vim` (or `init.lua`):

```bash
# Create config directory
mkdir -p ~/.config/nvim

# Create basic config file
nvim ~/.config/nvim/init.vim
```

### Basic init.vim Configuration
```vim
" Basic settings (like VS Code preferences)
set number              " Show line numbers
set relativenumber      " Show relative line numbers
set tabstop=4          " Tab width
set shiftwidth=4       " Indent width
set expandtab          " Use spaces instead of tabs
set autoindent         " Auto indent
set smartindent        " Smart indent
set wrap               " Wrap long lines
set ignorecase         " Ignore case in search
set smartcase          " Case sensitive if uppercase used
set hlsearch           " Highlight search results
set incsearch          " Incremental search
set mouse=a            " Enable mouse support
set clipboard=unnamedplus  " Use system clipboard

" Color scheme
colorscheme desert

" Key mappings (like VS Code keybindings)
" Save with Ctrl+S (in insert mode)
inoremap <C-s> <Esc>:w<CR>a
" Save with Ctrl+S (in normal mode)
nnoremap <C-s> :w<CR>

" Clear search highlighting with Esc
nnoremap <Esc> :noh<CR>

" Better window navigation
nnoremap <C-h> <C-w>h
nnoremap <C-j> <C-w>j
nnoremap <C-k> <C-w>k
nnoremap <C-l> <C-w>l
```

## 🔌 Essential Plugins (Like VS Code Extensions)

### Plugin Manager Setup (vim-plug)
```bash
# Install vim-plug
curl -fLo ~/.local/share/nvim/site/autoload/plug.vim --create-dirs \
    https://raw.githubusercontent.com/junegunn/vim-plug/master/plug.vim
```

### Basic Plugin Configuration
Add to your `~/.config/nvim/init.vim`:

```vim
" Plugin section
call plug#begin('~/.local/share/nvim/plugged')

" File explorer (like VS Code sidebar)
Plug 'preservim/nerdtree'

" Fuzzy finder (like Ctrl+P in VS Code)
Plug 'junegunn/fzf', { 'do': { -> fzf#install() } }
Plug 'junegunn/fzf.vim'

" Status line (like VS Code status bar)
Plug 'vim-airline/vim-airline'
Plug 'vim-airline/vim-airline-themes'

" Git integration (like VS Code Git)
Plug 'tpope/vim-fugitive'

" Auto-completion (like IntelliSense)
Plug 'neoclide/coc.nvim', {'branch': 'release'}

" Color schemes
Plug 'morhetz/gruvbox'
Plug 'dracula/vim', { 'as': 'dracula' }

call plug#end()

" Plugin configurations
" NERDTree
nnoremap <C-n> :NERDTreeToggle<CR>

" FZF
nnoremap <C-p> :Files<CR>
nnoremap <C-f> :Rg<CR>

" Color scheme
colorscheme gruvbox
set background=dark
```

### Installing Plugins
1. Save your config: `:w`
2. Reload config: `:source %`
3. Install plugins: `:PlugInstall`

## 🎯 Hands-On Exercise 5: Setting Up Your Environment

1. **Create your config:**
   ```bash
   mkdir -p ~/.config/nvim
   nvim ~/.config/nvim/init.vim
   ```

2. **Add the basic configuration** (copy from above)

3. **Install vim-plug and plugins:**
   - Install vim-plug (command from above)
   - Add plugin section to config
   - Run `:PlugInstall`

4. **Test your setup:**
   - Open a project: `nvim .`
   - Try `Ctrl+n` for file explorer
   - Try `Ctrl+p` for fuzzy finder
   - Test your custom keybindings

## 🚀 Advanced Features

### Language Server Protocol (LSP) with CoC
After installing coc.nvim:

```vim
" CoC configuration
" Use tab for trigger completion
inoremap <silent><expr> <TAB>
      \ pumvisible() ? "\<C-n>" :
      \ <SID>check_back_space() ? "\<TAB>" :
      \ coc#refresh()

" Go to definition (like F12 in VS Code)
nmap <silent> gd <Plug>(coc-definition)
" Find references (like Shift+F12 in VS Code)
nmap <silent> gr <Plug>(coc-references)
" Rename symbol (like F2 in VS Code)
nmap <leader>rn <Plug>(coc-rename)
```

### Git Integration
With vim-fugitive:
- `:Git status` - Git status (like VS Code Source Control)
- `:Git add %` - Stage current file
- `:Git commit` - Commit changes
- `:Git push` - Push changes

## 🎯 Hands-On Exercise 6: Complete Development Workflow

Let's create a complete project workflow:

1. **Create a new project:**
   ```bash
   mkdir nvim_project
   cd nvim_project
   git init
   nvim .
   ```

2. **Use file explorer:**
   - Press `Ctrl+n` to open NERDTree
   - Navigate and create files

3. **Create multiple files:**
   - `main.py`
   - `utils.py`
   - `README.md`

4. **Use fuzzy finder:**
   - Press `Ctrl+p` to quickly open files
   - Type partial filename to find files

5. **Use Git integration:**
   - `:Git status` to see changes
   - `:Git add .` to stage all files
   - `:Git commit -m "Initial commit"`

6. **Use splits and buffers:**
   - Open multiple files in splits
   - Navigate between them efficiently

## 🎨 Customization Tips

### Color Schemes
```vim
" Try different themes
colorscheme gruvbox
colorscheme dracula
colorscheme desert

" Toggle background
set background=dark
set background=light
```

### Custom Key Mappings
```vim
" Map leader key (like a prefix for custom commands)
let mapleader = " "  " Use space as leader

" Custom mappings
nnoremap <leader>w :w<CR>           " Space+w to save
nnoremap <leader>q :q<CR>           " Space+q to quit
nnoremap <leader>e :NERDTreeToggle<CR>  " Space+e for file explorer
nnoremap <leader>f :Files<CR>       " Space+f for fuzzy finder

" Split navigation (more VS Code-like)
nnoremap <C-h> <C-w>h
nnoremap <C-j> <C-w>j
nnoremap <C-k> <C-w>k
nnoremap <C-l> <C-w>l
```

## 🆘 Getting Help and Troubleshooting

### Built-in Help System
| Command | Description |
|---------|-------------|
| `:help` | Open help system |
| `:help keyword` | Help for specific topic |
| `:help :command` | Help for command |
| `:help 'option'` | Help for option |

### Common Issues and Solutions

**Problem**: Can't exit Neovim
**Solution**: Press `Esc` then type `:q!` to force quit

**Problem**: Accidentally in wrong mode
**Solution**: Press `Esc` multiple times to get to Normal mode

**Problem**: Plugins not working
**Solution**: Check `:PlugStatus` and run `:PlugInstall`

**Problem**: Config not loading
**Solution**: Check `:echo $MYVIMRC` and verify file location

## 🎓 Graduation: You're Now a Neovim User!

Congratulations! You've learned:
- ✅ Modal editing concepts
- ✅ File operations and navigation
- ✅ Multi-file workflows with buffers and splits
- ✅ Visual mode and text objects
- ✅ Search and replace
- ✅ Basic configuration
- ✅ Essential plugins
- ✅ Development workflow

## 🔗 Next Steps

1. **Practice daily**: Use Neovim for your regular coding tasks
2. **Learn more motions**: Master text objects and advanced navigation
3. **Explore plugins**: Find plugins for your specific needs
4. **Learn Lua**: Modern Neovim configs use Lua instead of Vimscript
5. **Join the community**: Check out r/neovim and Neovim GitHub

## 🆘 Quick Reference for VS Code Users

### Most Important Commands to Remember:
- `i` - Start typing (Insert Mode)
- `Esc` - Stop typing (Normal Mode)
- `:w` - Save file
- `:q` - Quit
- `:wq` - Save and quit
- `/` - Search
- `u` - Undo
- `Ctrl+r` - Redo

### Emergency Commands:
- `Esc` - Get back to Normal Mode
- `:q!` - Quit without saving
- `:w!` - Force save
- `u` - Undo last change

### VS Code to Neovim Cheat Sheet:
| VS Code | Neovim | What it does |
|---------|--------|--------------|
| `Ctrl+S` | `:w` | Save |
| `Ctrl+P` | `:Files` (with fzf) | Quick open |
| `Ctrl+Shift+P` | `:` | Command palette |
| `Ctrl+F` | `/` | Find |
| `Ctrl+H` | `:%s/old/new/g` | Replace |
| `F12` | `gd` (with LSP) | Go to definition |
| `Shift+F12` | `gr` (with LSP) | Find references |
| `F2` | `<leader>rn` (with LSP) | Rename |

---

*Happy coding! Remember: Neovim has a learning curve, but once you master it, you'll have one of the most powerful and efficient editing environments available. Give yourself time to build muscle memory - it's worth it!*
