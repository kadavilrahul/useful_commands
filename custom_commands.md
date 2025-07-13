# Custom Commands

## Shell Aliases

### Clear Command Alias
**Purpose**: Quick shortcut for clearing the terminal screen

**Implementation**:
```bash
# Add to ~/.bashrc
alias c='clear'
```

**Usage**:
```bash
c  # Clears the terminal screen
```

**Setup**:
1. Add the alias to your shell configuration file:
   ```bash
   echo "alias c='clear'" >> ~/.bashrc
   ```
2. Reload the configuration:
   ```bash
   source ~/.bashrc
   ```

## Smart Functions

### Clone Command with Fuzzy Search
**Purpose**: Quickly clone GitHub repositories using keywords with tab completion

**Features**:
- Fuzzy search by repository name keywords
- Tab completion for common keywords
- Clones to current directory and automatically enters the folder
- Shows repository info after cloning
- Handles multiple matches with interactive selection

**Implementation**:
```bash
# Smart clone function is stored in /root/.clone_helper.sh
# Automatically loaded via ~/.bashrc
```

**Usage**:
```bash
clone email      # Finds email_automation_private, setup_email_system, etc.
clone html       # Finds generate_html_from_csv, etc.
clone wordpress  # Finds install_wordpress_on_lamp, etc.
clone useful     # Finds useful_commands repo
```

**Tab Completion Keywords**:
- `email`, `html`, `csv`, `wordpress`, `woocommerce`, `automation`
- `generate`, `import`, `install`, `migration`, `backup`, `clone`
- `useful`, `commands`, `agent`, `streamlit`, `python`, `nodejs`, `go`

**Setup**:
1. The function is automatically available after running the setup
2. Uses your existing GitHub configuration from `/root/projects/Repositories/clone_repos/config.json`
3. Works with both public and private repositories (if token is configured)

**Interactive Features**:
- If multiple matches found, shows numbered list for selection
- Press Enter to select the first option
- Shows README preview and recent commits after cloning
- Handles existing directories gracefully