# File Editors Command Comparison

A comprehensive comparison of commands between VS Code, Neovim, and Helix editors.

## File Operations

| Action | VS Code | Neovim | Helix |
|--------|---------|--------|-------|
| Open file | `Ctrl+O` | `:e filename` | `Space + f` |
| Save file | `Ctrl+S` | `:w` | `:w` |
| Save as | `Ctrl+Shift+S` | `:w filename` | `:w filename` |
| New file | `Ctrl+N` | `:new` | `:new` |
| Close file | `Ctrl+W` | `:q` | `:q` |
| Close without saving | `Ctrl+W` (with prompt) | `:q!` | `:q!` |
| Save and quit | `Ctrl+S` then `Ctrl+W` | `:wq` or `ZZ` | `:wq` |
| Open folder/directory | `Ctrl+K Ctrl+O` | `:e .` | `hx .` |
| Recent files | `Ctrl+R` | `:oldfiles` | `Space + f` (shows recent) |

## Navigation

| Action | VS Code | Neovim | Helix |
|--------|---------|--------|-------|
| Move cursor left | `←` | `h` | `h` |
| Move cursor down | `↓` | `j` | `j` |
| Move cursor up | `↑` | `k` | `k` |
| Move cursor right | `→` | `l` | `l` |
| Go to start of line | `Home` | `0` or `^` | `Home` or `^` |
| Go to end of line | `End` | `$` | `End` or `$` |
| Go to start of file | `Ctrl+Home` | `gg` | `gg` |
| Go to end of file | `Ctrl+End` | `G` | `ge` |
| Go to line number | `Ctrl+G` | `:line_number` or `line_number G` | `Ctrl+G` |
| Page up | `Page Up` | `Ctrl+B` | `Page Up` |
| Page down | `Page Down` | `Ctrl+F` | `Page Down` |
| Word forward | `Ctrl+→` | `w` | `w` |
| Word backward | `Ctrl+←` | `b` | `b` |
| Jump to matching bracket | `Ctrl+Shift+\` | `%` | `mm` |

## Editing

| Action | VS Code | Neovim | Helix |
|--------|---------|--------|-------|
| Enter insert mode | N/A (always in insert) | `i` | `i` |
| Insert at line start | N/A | `I` | `I` |
| Insert at line end | N/A | `A` | `A` |
| Insert new line below | `Enter` (at end) | `o` | `o` |
| Insert new line above | `Shift+Enter` | `O` | `O` |
| Delete character | `Delete` | `x` | `d` |
| Delete line | `Ctrl+Shift+K` | `dd` | `dd` |
| Delete word | `Ctrl+Delete` | `dw` | `dw` |
| Delete to end of line | `Ctrl+K` | `D` | `D` |
| Undo | `Ctrl+Z` | `u` | `u` |
| Redo | `Ctrl+Y` | `Ctrl+R` | `U` |
| Copy line | `Ctrl+C` (select line first) | `yy` | `yy` |
| Cut line | `Ctrl+X` (select line first) | `dd` | `dd` |
| Paste | `Ctrl+V` | `p` | `p` |
| Paste above | N/A | `P` | `P` |

## Selection

| Action | VS Code | Neovim | Helix |
|--------|---------|--------|-------|
| Select all | `Ctrl+A` | `ggVG` | `%` |
| Select line | `Ctrl+L` | `V` | `x` |
| Select word | `Ctrl+D` | `viw` | `w` (in select mode) |
| Select to end of line | `Shift+End` | `v$` | `Shift+End` |
| Select to start of line | `Shift+Home` | `v^` | `Shift+Home` |
| Extend selection | `Shift+arrows` | `v` + movement | `v` + movement |
| Multi-cursor select | `Ctrl+D` (multiple) | N/A (use visual block) | `C` |
| Select inside brackets | N/A | `vi(` `vi[` `vi{` | `mi(` `mi[` `mi{` |
| Select around brackets | N/A | `va(` `va[` `va{` | `ma(` `ma[` `ma{` |

## Search and Replace

| Action | VS Code | Neovim | Helix |
|--------|---------|--------|-------|
| Find | `Ctrl+F` | `/` | `/` |
| Find next | `F3` or `Ctrl+G` | `n` | `n` |
| Find previous | `Shift+F3` | `N` | `N` |
| Replace | `Ctrl+H` | `:s/old/new/` | `:s/old/new/` |
| Replace all | `Ctrl+Alt+Enter` | `:%s/old/new/g` | `:%s/old/new/g` |
| Find in files | `Ctrl+Shift+F` | `:grep pattern` | `Space + /` |
| Find and replace in files | `Ctrl+Shift+H` | `:cfdo %s/old/new/g` | N/A |

## View and Windows

| Action | VS Code | Neovim | Helix |
|--------|---------|--------|-------|
| Split window horizontally | `Ctrl+\` | `:split` or `Ctrl+W s` | `Ctrl+W s` |
| Split window vertically | `Ctrl+Shift+\` | `:vsplit` or `Ctrl+W v` | `Ctrl+W v` |
| Switch between windows | `Ctrl+1,2,3...` | `Ctrl+W w` | `Ctrl+W w` |
| Close current window | `Ctrl+W` | `Ctrl+W q` | `Ctrl+W q` |
| Zoom in | `Ctrl++` | N/A | N/A |
| Zoom out | `Ctrl+-` | N/A | N/A |
| Toggle sidebar | `Ctrl+B` | N/A | N/A |
| Toggle terminal | `Ctrl+`` | `:terminal` | `:sh` |

## File Management

| Action | VS Code | Neovim | Helix |
|--------|---------|--------|-------|
| File explorer | `Ctrl+Shift+E` | `:Explore` or `:E` | `Space + f` |
| Switch between open files | `Ctrl+Tab` | `:bnext` `:bprev` | `Space + b` |
| Close all files | `Ctrl+K Ctrl+W` | `:qall` | `:qa` |
| Open command palette | `Ctrl+Shift+P` | `:` | `:` |
| Quick open | `Ctrl+P` | `:FZF` (with plugin) | `Space + f` |

## Code Navigation

| Action | VS Code | Neovim | Helix |
|--------|---------|--------|-------|
| Go to definition | `F12` | `gd` (with LSP) | `gd` |
| Go to references | `Shift+F12` | `gr` (with LSP) | `gr` |
| Go to symbol | `Ctrl+Shift+O` | `:LSPDocumentSymbol` | `Space + s` |
| Go to symbol in workspace | `Ctrl+T` | `:LSPWorkspaceSymbol` | `Space + S` |
| Peek definition | `Alt+F12` | N/A | N/A |
| Show hover info | `Ctrl+K Ctrl+I` | `K` (with LSP) | `K` |

## Formatting and Code

| Action | VS Code | Neovim | Helix |
|--------|---------|--------|-------|
| Format document | `Shift+Alt+F` | `:LSPFormat` | `Space + f` |
| Format selection | `Ctrl+K Ctrl+F` | `gq` | `Space + f` (selection) |
| Comment line | `Ctrl+/` | `gcc` (with plugin) | `Ctrl+c` |
| Comment block | `Shift+Alt+A` | `gc` (with plugin) | `Ctrl+c` |
| Indent line | `Ctrl+]` | `>>` | `>` |
| Unindent line | `Ctrl+[` | `<<` | `<` |
| Auto-complete | `Ctrl+Space` | `Ctrl+N` (with LSP) | `Ctrl+x` |

## Running Code

| Action | VS Code | Neovim | Helix |
|--------|---------|--------|-------|
| Run file | `F5` (with debugger) | `:!interpreter filename` | `:!interpreter filename` |
| Run selection | `F8` | `:!` (with selection) | `:!` (with selection) |
| Open terminal | `Ctrl+`` | `:terminal` | `:sh` |
| Run task | `Ctrl+Shift+P` → Tasks | `:make` | `:!make` |

## Special Helix Features

| Action | VS Code Equivalent | Neovim Equivalent | Helix |
|--------|-------------------|-------------------|-------|
| Select and edit | Multi-cursor | Visual mode | `s` (select) then edit |
| Expand selection | `Shift+Alt+→` | N/A | `)` |
| Shrink selection | `Shift+Alt+←` | N/A | `(` |
| Select parent node | N/A | N/A | `Alt+p` |
| Select child node | N/A | N/A | `Alt+o` |
| Multiple cursors | `Ctrl+D` | N/A | `C` |
| Split selection | N/A | N/A | `S` |
| Join lines | N/A | `J` | `J` |

## Mode Indicators

| Editor | Normal Mode | Insert Mode | Visual/Select Mode |
|--------|-------------|-------------|-------------------|
| VS Code | N/A | Always active | Selection highlight |
| Neovim | `-- NORMAL --` | `-- INSERT --` | `-- VISUAL --` |
| Helix | `NOR` | `INS` | `SEL` |

---

## Notes

- **VS Code**: GUI-based editor, always in "insert" mode
- **Neovim**: Modal editor, extensive plugin ecosystem
- **Helix**: Modal editor with built-in features, selection-first approach

This comparison covers the most commonly used commands. Each editor has many more specialized commands and features.
