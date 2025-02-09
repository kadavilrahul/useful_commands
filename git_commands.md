Git Commands Documentation
1. Initial Setup
These commands are used to install Git and configure global settings for your user account.

# Install Git (Ubuntu/Debian)
sudo apt update
sudo apt install git

# Verify installation
git --version

# Configure global credentials
git config --global user.name "Your Name"
git config --global user.email "your.email@example.com"

# Verify configuration
git config --global --list

2. Repository Setup
Commands to initialize a new repository or clone an existing one, and set up the remote repository.

# Initialize new repository
git init

# Or clone existing repository
git clone https://github.com/username/repository_name.git
cd repository_name

# Add remote repository
git remote add origin https://github.com/username/repository_name.git

# Verify remote
git remote -v

3. Basic Workflow Commands
These commands are used for the basic Git workflow, including checking status, staging, committing, and pushing changes.

# Check repository status
git status

# Stage changes
git add .

# Commit changes
git commit -m "Descriptive message"

# Push changes
git push origin main

# Pull latest changes
git pull origin main

4. Branch Management
Commands to manage branches, including creating, switching, and viewing branch history.

# List all branches
git branch

# Create and switch to new branch
git checkout -b new-branch-name

# Switch between branches
git checkout branch-name

# View branch history
git log --oneline --decorate --all --graph

5. Credential Management
Commands to manage Git credentials, including caching and setting up remote URLs with tokens.

# Store credentials (cache method)
git config --global credential.helper cache

# Set credential timeout (optional)
git config --global credential.helper 'cache --timeout=3600'

# Set remote URL with token
git remote set-url origin https://TOKEN@github.com/username/repository_name.git

6. Advanced Commands
Additional commands for advanced Git operations, such as stashing changes and viewing commit history.

# Stash changes
git stash
git stash list
git stash pop

# View commit history
git log --oneline
git log --pretty=format:"%h %ad %s" --date=format:"%Y-%m-%d %H:%M:%S"

# Checkout specific commit
git checkout commit-hash

7. Unnecessary/Duplicate Commands
These commands are either redundant or situational and may not be required in most workflows.

# Alternative push methods (use standard push instead)
git push https://token@github.com/username/repository_name.git

# Combined commands (unnecessary if using proper workflow)
git add . && git commit -m "Update" && git push

# Check if directory is Git repository (rarely needed)
git rev-parse --is-inside-work-tree

8. Credentials Template
Store these securely, never in code:

Username: your-github-username
Email: your.email@example.com
Token: your-personal-access-token
