# Initial Setup:

### Install Git (Ubuntu/Debian)
   ```bash
  sudo apt update
   ```
   ```bash
sudo apt install git
   ```

### Verify installation
   ```bash
git –version
   ```

### Configure global credentials
   ```bash
git config --global user.name "Your Name"
   ```
   ```bash
git config --global user.email your.email@example.com
   ```

### Verify configuration
   ```bash
git config --global --list
   ```

# Repository Setup:

### Initialize new repository
   ```bash
git init
   ```

### Or clone existing repository
   ```bash
git clone https://github.com/username/repository_name.git
   ```

   ```bash
cd repository_name
   ```

### Add remote repository
   ```bash
git remote add origin https://github.com/username/repository_name.git
   ```

### Verify remote
   ```bash
git remote -v
   ```

# Basic Workflow Commands:

### Check repository status
   ```bash
git status
   ```

### Stage changes
   ```bash
git add .
   ```

### Commit changes
   ```bash
git commit -m "Descriptive message"
   ```

### Push changes
   ```bash
git push origin main
   ```
### Force push changes
   ```bash
git push -f origin master
   ```
### Pull latest changes
   ```bash
git pull origin main
   ```

# Branch Management

### List all branches
   ```bash
git branch
   ```

### Create and switch to new branch
   ```bash
git checkout -b new-branch-name
   ```

### Switch between branches
   ```bash
git checkout branch-name
   ```

### View branch history
   ```bash
git log --oneline --decorate --all –graph
   ```

# Credential Management


### Store credentials (cache method)
   ```bash
git config --global credential.helper cache
   ```

### Set credential timeout (optional)
   ```bash
git config --global credential.helper 'cache --timeout=3600'
   ```

### Set remote URL with token
   ```bash
git remote set-url origin https://TOKEN@github.com/username/repository_name.git
   ```

# Advanced Commands

### Stash changes
   ```bash
git stash
   ```

   ```bash
git stash list
   ```

   ```bash
git stash pop
   ```

### View commit history
   ```bash
git log –oneline
   ```

   ```bash
git log --pretty=format:"%h %ad %s" --date=format:"%Y-%m-%d %H:%M:%S"
   ```

### Checkout specific commit
   ```bash
git checkout commit-hash
   ```
### To discard all changes after a specific commit:
   ```bash
git reset --hard abc123
   ```
### Revert specific commit but not commit immediately (for manual adjustments)
   ```bash
git revert <commit-hash> --no-commit
   ```

# Additional Commands

### Alternative push methods (use standard push instead)
   ```bash
git push https://token@github.com/username/repository_name.git
   ```

### Combined commands (unnecessary if using proper workflow)
   ```bash
git add . && git commit -m "Update" && git push
   ```

### Check if directory is Git repository (rarely needed)
   ```bash
git rev-parse --is-inside-work-tree
   ```


