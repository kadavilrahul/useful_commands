# Initial Setup:

### Install Git (Ubuntu/Debian)
sudo apt update
sudo apt install git

### Verify installation
git --version

### Configure global credentials
git config --global user.name "Your Name"
git config --global user.email "your.email@example.com"

### Verify configuration
git config --global --list

# Repository Setup:

### Initialize new repository
git init

### Or clone existing repository
git clone https://github.com/username/repository_name.git
cd repository_name

### Add remote repository
git remote add origin https://github.com/username/repository_name.git

### Verify remote
git remote -v

# Basic Workflow Commands:

### Check repository status
git status

### Stage changes
git add .

### Commit changes
git commit -m "Descriptive message"

### Push changes
git push origin main

### Pull latest changes
git pull origin main

# Branch Management

### List all branches
git branch

### Create and switch to new branch
git checkout -b new-branch-name

### Switch between branches
git checkout branch-name

### View branch history
git log --oneline --decorate --all --graph

# Credential Management

### Store credentials (cache method)
git config --global credential.helper cache

### Set credential timeout (optional)
git config --global credential.helper 'cache --timeout=3600'

### Set remote URL with token
git remote set-url origin https://TOKEN@github.com/username/repository_name.git

# Advanced Commands

### Stash changes
git stash
git stash list
git stash pop

### View commit history
git log --oneline
git log --pretty=format:"%h %ad %s" --date=format:"%Y-%m-%d %H:%M:%S"

### Checkout specific commit
git checkout commit-hash

# Additional Commands

### Alternative push methods (use standard push instead)
git push https://token@github.com/username/repository_name.git

### Combined commands (unnecessary if using proper workflow)
git add . && git commit -m "Update" && git push

### Check if directory is Git repository (rarely needed)
git rev-parse --is-inside-work-tree


