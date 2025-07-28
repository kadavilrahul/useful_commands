# Essential CLI Tools for eCommerce & Development

A curated list of command-line tools for eCommerce website owners, developers, and system administrators.

## 📋 Table of Contents
- [File & System Management](#️-file--system-management)
- [Cloud Services](#️-cloud-services)
- [Development Tools](#️-development-tools)
- [Monitoring & Performance](#-monitoring--performance)
- [Text Processing & Search](#-text-processing--search)
- [Multimedia & Data](#-multimedia--data)
- [Network & Security](#-network--security)
- [Security & Backup](#️-security--backup)
- [Performance & Optimization](#-performance--optimization)
- [Mobile & Social Media](#-mobile--social-media)
- [eCommerce & Analytics](#-ecommerce--analytics)
- [Web Scraping & Data Collection](#-web-scraping--data-collection)
- [Automation & Deployment](#-automation--deployment)
- [Financial & Business Intelligence](#-financial--business-intelligence)
- [Apps & Utilities](#-apps--utilities)

## 🗂️ File & System Management

### Commands
```bash
# Advanced file operations - Install: apt install ncdu duf bat fd-find tree mc ranger
ncdu                                 # Interactive disk usage analyzer with ncurses interface
  apt install ncdu                   # Install ncdu
  ncdu /path/to/analyze              # Analyze specific directory
  ncdu -x /                          # Exclude mounted filesystems
  # Use arrow keys to navigate, 'd' to delete, 'q' to quit

duf                                  # Modern disk usage utility with colorful output
  apt install duf                    # Install duf
  duf                                # Show all mounted filesystems
  duf --sort size                    # Sort by size
  duf --only local                   # Show only local filesystems
  duf --hide-mp /snap                # Hide specific mount points

eza                                  # Modern replacement for ls with Git integration - Install: already available
                                     # Already installed on most modern systems
  eza                                # List files in current directory
  eza -l                             # Long format (like `ls -l`)
  eza -la                            # Long format including hidden files
  eza -lh                            # Human-readable file sizes
  eza --tree                         # Tree view of directories
  eza --git                          # Show git status per file
  eza -l --icons                     # Show file icons (needs Nerd Font terminal)

lsd                                  # Next-gen ls command with icons and colors - Install: already available
  # Already installed on most modern systems
  lsd -la                            # List all files with details
  lsd --tree                         # Tree view with icons

fd                                   # Simple, fast alternative to find - Install: apt install fd-find (use as fdfind)
  apt install fd-find                # Install fd (use as fdfind command)
  fdfind pattern                     # Find files matching pattern
  fdfind -e py                       # Find files with .py extension
  fdfind -t f pattern /path          # Find files only in specific path
  fdfind -H pattern                  # Include hidden files

bat                                  # Cat clone with syntax highlighting - Install: apt install bat (use as batcat)
  apt install bat                    # Install bat (use as batcat command)
  batcat /path/filename.py           # Show file with syntax highlighting
  batcat -A filename                 # Show all characters including tabs/spaces
  batcat --list-languages            # List supported languages
  echo "code" | batcat -l python     # Pipe with language specification
  # Navigation: q = quit, Space = next page, b = previous page, /pattern = search, h = help

tree                                 # Display directory structure as a tree
  apt install tree                   # Install tree
  tree                               # Show current directory tree
  tree -L 3                          # Limit depth to 3 levels
  tree -a                            # Include hidden files
  tree -I "node_modules|__pycache__" # Ignore specific patterns

mc                                   # Midnight Commander - powerful file manager
  apt install mc                     # Install Midnight Commander
  mc                                 # Start Midnight Commander
  # F5 = copy, F6 = move, F8 = delete, F10 = quit
  # Tab = switch panels, Ctrl+O = show/hide panels

ranger                               # Console file manager with vi key bindings
  apt install ranger                 # Install ranger
  ranger                             # Start ranger
  # j/k = up/down, h/l = back/forward, Space = select, q = quit

vidir                                # Edit directory contents in your favorite editor - Install: apt install moreutils
  apt install moreutils              # Install vidir
  vidir                              # Edit current directory
  vidir /path/to/dir                 # Edit specific directory
  # Example: Opens editor showing "1  ./file1.txt", "2  ./file2.py"
  # - Change "file1.txt" to "newname.txt" to rename file
  # - Delete entire line to delete that file
  # - Save and exit editor to apply all changes at once

# File compression & archives - Install: apt install p7zip-full fdupes
7z                                   # 7-Zip archiver for high compression ratios
  7z a archive.7z file1 file2        # Create archive
  7z x archive.7z                    # Extract archive
  7z l archive.7z                    # List archive contents
  7z t archive.7z                    # Test archive integrity

atool                                # Archive tool wrapper for various formats - Install: apt install atool
  atool -x archive.tar.gz            # Extract any archive format
  atool -a archive.tar.gz files/     # Create archive
  atool -l archive.zip               # List contents

fdupes                               # Find and remove duplicate files
  fdupes /path/to/search             # Find duplicates
  fdupes -r /path                    # Search recursively
  fdupes -d /path                    # Delete duplicates interactively
  fdupes -S /path                    # Show size of duplicates

jdupes                               # Advanced duplicate file finder (better than fdupes) - Install: snap install jdupes
  jdupes -r /path                    # Find duplicates recursively
  jdupes -M /path                    # Print matches in machine-readable format

# File synchronization - Install: apt install rsync rclone aria2
rsync                                # Fast, versatile file copying tool
  rsync -av source/ dest/            # Archive mode with verbose output
  rsync -avz --progress src/ dest/   # With compression and progress
  rsync -av --delete src/ dest/      # Delete files not in source
  rsync -av user@host:/path/ local/  # Sync from remote host

rclone                               # Sync files to cloud storage providers
  rclone config                      # Configure cloud storage
  rclone copy local/ remote:folder/  # Copy to cloud storage
  rclone sync local/ remote:folder/  # Sync (dangerous - deletes!)
  rclone ls remote:                  # List remote files

aria2                                # Advanced download utility with resume support
  aria2c URL                         # Download file
  aria2c -c URL                      # Continue partial download
  aria2c -x 8 URL                    # Use 8 connections
  aria2c -i urls.txt                 # Download from URL list
```

## ☁️ Cloud Services

### Commands
```bash
# Google Cloud Platform
gcloud        # Official Google Cloud CLI for managing GCP resources
  gcloud auth login                    # Authenticate with Google Cloud
  gcloud projects list                 # List available projects
  gcloud config set project PROJECT   # Set default project
  gcloud compute instances list        # List VM instances

# Cloudflare - Install: npm install -g wrangler
wrangler      # Build and deploy Cloudflare Workers applications
  wrangler login                       # Authenticate with Cloudflare
  wrangler init my-worker              # Create new Worker project
  wrangler dev                         # Start local development server
  wrangler deploy                      # Deploy Worker to Cloudflare

# GitHub - Install: apt install gh
gh            # Official GitHub CLI for repository management
  gh auth login                        # Authenticate with GitHub
  gh repo list                         # List your repositories
  gh repo clone OWNER/REPO             # Clone repository
  gh pr list                           # List pull requests
  gh issue create                      # Create new issue

# Redis - Install: apt install redis-tools
redis-cli     # Redis command line interface for database operations
  redis-cli ping                       # Test Redis connection
  redis-cli set key value              # Set a key-value pair
  redis-cli get key                    # Get value by key
  redis-cli keys "*"                   # List all keys
  redis-cli flushall                   # Clear all data
```

### Apps & Utilities
- **[Dropbox Uploader](https://github.com/andreafabrizi/Dropbox-Uploader)** - Bash script for Dropbox file operations
- **[gdrive](https://github.com/prasmussen/gdrive)** - Command line tool for Google Drive
- **gdocs2md** - Convert Google Docs to Markdown format
- **Microsoft Graph API Scripts** - Custom scripts for Office 365 integration

## 🛠️ Development Tools

### Commands
```bash
# Version Control - Install: apt install git
git           # Distributed version control system
  git status                           # Check repository status
  git add .                            # Stage all changes
  git commit -m "message"              # Commit with message
  git push origin main                 # Push to remote repository
  git pull                             # Pull latest changes
  git branch -a                        # List all branches
  git checkout -b feature-branch       # Create and switch to new branch

gitui         # Terminal UI for Git with intuitive interface
tig           # Text-mode interface for Git repositories
lazygit       # Simple terminal UI for Git commands

# Code Quality & Analysis - Install: apt install ripgrep
ripgrep       # Ultra-fast text search tool (rg command)
  rg "pattern" --type py               # Search in Python files
  rg "TODO" -A 3 -B 1                 # Show context around matches
  rg "function" --stats                # Show search statistics
  rg "class.*:" --only-matching        # Show only matching part

ag            # The Silver Searcher - fast code search
tokei         # Count lines of code quickly - Install: cargo install tokei
scc           # Fast lines of code counter (better than cloc)
diff-so-fancy # Better looking diffs with highlighting

# Terminal Multiplexers - Install: apt install tmux
tmux          # Terminal multiplexer for session management
  tmux new-session -s mysession        # Create new session
  tmux attach -t mysession             # Attach to session
  tmux list-sessions                   # List all sessions
  tmux kill-session -t mysession       # Kill session
  # Ctrl+b % = split vertical, Ctrl+b " = split horizontal

screen        # Terminal multiplexer with session persistence
zellij        # Modern terminal workspace
byobu         # Enhanced tmux/screen wrapper

# Package Managers - Install: apt install just
nala          # Beautiful frontend for APT package manager
just          # Modern command runner (better than make)
  just --list                          # List available commands
  just --justfile justfile build       # Run build command
  just --working-directory path cmd    # Run in specific directory

# Text Editors - Install: apt install micro && snap install nvim
micro         # Modern text editor with intuitive shortcuts
  micro filename.txt                   # Open file for editing
  # Ctrl+S = save, Ctrl+Q = quit, Ctrl+G = help

neovim        # Extensible vim-based editor
  nvim filename.txt                    # Open file for editing
  # :q = quit, :w = save, :wq = save and quit
  # i = insert mode, Esc = normal mode

# AI & Machine Learning
huggingface-cli # Hugging Face model hub command line interface
agno          # AI-powered code generation tool
tgpt          # Terminal-based AI chatbot (GitHub project)
```

## 📊 Monitoring & Performance

### Commands
```bash
# System Monitoring - Install: apt install htop glances iftop nethogs
htop          # Interactive process viewer
  htop                               # Start interactive process viewer
  # F2 = setup, F3 = search, F4 = filter, F5 = tree view, F9 = kill, F10 = quit
  # Space = tag process, U = untag all, c = command line toggle

btop          # Resource monitor with modern interface - Install: snap install btop
  btop                               # Start modern resource monitor
  # q = quit, + = zoom in, - = zoom out, m = menu

bpytop        # Resource monitor with better interface - Install: pip install bpytop
  bpytop                             # Start Python-based resource monitor

atop          # Advanced system and process monitor - Install: apt install atop
  atop                               # Start atop monitor
  atop -w logfile                    # Write to log file
  atop -r logfile                    # Read from log file

glances       # Cross-platform system monitoring tool
  glances                            # Start glances monitor
  glances -w                         # Web server mode
  glances -s                         # Server mode
  glances -c @server                 # Connect to remote server

nvtop         # GPU process monitor - Install: apt install nvtop
  nvtop                              # Monitor GPU usage (NVIDIA)

iftop         # Network bandwidth usage monitor
  iftop                              # Monitor network bandwidth
  iftop -i eth0                      # Monitor specific interface
  iftop -p                           # Show port numbers

nethogs       # Network traffic monitor per process
  nethogs                            # Monitor per-process network usage
  nethogs eth0                       # Monitor specific interface

bandwhich     # Network utilization by process - Install: cargo install bandwhich
  sudo bandwhich                     # Monitor network usage by process

procs         # Modern process viewer (better than ps) - Install: cargo install procs
  procs                              # Show all processes
  procs --tree                       # Tree view
  procs firefox                      # Filter by process name

ctop          # Container metrics and monitoring - Install: docker run --rm -ti --volumes-from ctop -v /var/run/docker.sock:/var/run/docker.sock quay.io/vektorlab/ctop:latest
  ctop                               # Monitor Docker containers

iostat        # I/O statistics for devices and partitions - Install: apt install sysstat
  iostat                             # Show I/O statistics
  iostat -x 1                        # Extended stats every second
  iostat -c 1                        # CPU stats only

vmstat        # Virtual memory statistics
  vmstat                             # Show memory statistics
  vmstat 1                           # Update every second
  vmstat -s                          # Summary since boot

mpstat        # Multiple processor usage
  mpstat                             # Show CPU usage
  mpstat 1                           # Update every second
  mpstat -P ALL                      # All processors

# Performance Testing - Install: apt install speedtest-cli iperf3 && cargo install hyperfine
hyperfine     # Command-line benchmarking tool
  hyperfine 'command1' 'command2'    # Benchmark commands
  hyperfine --warmup 3 'command'     # Warm up runs
  hyperfine --export-json results.json 'cmd'  # Export results

iperf3        # Network performance measurement tool
  iperf3 -s                          # Start server
  iperf3 -c server-ip                # Connect to server
  iperf3 -c server-ip -P 4           # 4 parallel streams

speedtest-cli # Internet speed test from command line
  speedtest-cli                      # Run speed test
  speedtest-cli --simple             # Simple output
  speedtest-cli --list               # List servers

speedtest     # Internet speed test from terminal - Install: curl -s https://packagecloud.io/install/repositories/ookla/speedtest-cli/script.deb.sh | sudo bash && apt install speedtest
  speedtest                          # Run Ookla speed test

gping         # Interactive ping tool with graphs - Install: cargo install gping
  gping google.com                   # Ping with graph
  gping google.com 1.1.1.1          # Ping multiple hosts

# Log Analysis - Install: apt install lnav entr && cargo install watchexec-cli
lnav          # Advanced log file viewer and analyzer
  lnav /var/log/syslog               # View system log
  lnav /path/to/logs/                # View directory of logs
  # Press 'h' for help, 'q' to quit

entr          # Run commands when files change
  find . -name "*.py" | entr pytest # Run tests when Python files change
  echo file.txt | entr cat file.txt  # Monitor single file

watchexec     # Execute commands when files change
  watchexec -e py pytest             # Run pytest when .py files change
  watchexec -w src/ npm run build    # Watch specific directory

# Process Management - Install: cargo install pueue && apt install task-spooler
pueue         # Task queue manager for long-running processes
  pueue add 'long-command'           # Add command to queue
  pueue status                       # Show queue status
  pueue follow 0                     # Follow task output

task-spooler  # Queue system for shell commands
  tsp command                        # Add command to queue
  tsp -l                             # List tasks
  tsp -c 0                           # Show task output
```

## 🔍 Text Processing & Search

### Commands
```bash
# Text Processing
sed           # Stream editor for filtering and transforming text
awk           # Pattern scanning and processing language
jq            # Command-line JSON processor
yq            # YAML processor (like jq for YAML)
rpl           # Replace text in files efficiently
sd            # Intuitive find and replace (better than sed)
most          # Multi-window scroll pager (better than less)
column        # Format text into columns
join          # Join lines of files on common fields
cut           # Extract columns from text

# Search & Navigation
fzf           # Fuzzy finder for command-line - Install: apt install fzf
  apt install fzf                      # Install fzf
  fzf                                  # Interactive file finder
  history | fzf                        # Search command history
  find . -type f | fzf                 # Find files interactively
  # Ctrl+R integration for history search (after setup)
  # Ctrl+T for file completion, Alt+C for directory completion

fzy           # Fast fuzzy text selector
autojump      # Smart directory navigation - Install: apt install autojump
  apt install autojump                 # Install autojump
  echo '. /usr/share/autojump/autojump.sh' >> ~/.bashrc  # Bash integration
  j documents                          # Jump to documents directory
  j proj                               # Jump to project directory (partial match)
  jo music                             # Open directory in file manager

zoxide        # Smarter cd command with frecency algorithm - Install: apt install zoxide
  apt install zoxide                   # Install zoxide
  echo 'eval "$(zoxide init bash)"' >> ~/.bashrc    # Bash integration
  echo 'eval "$(zoxide init zsh)"' >> ~/.zshrc      # Zsh integration
  echo 'zoxide init fish | source' >> ~/.config/fish/config.fish  # Fish integration
  # Restart shell 
  z documents                          # Jump to documents directory
  z proj                               # Jump to project directory (partial match)
  zi                                   # Interactive directory picker
  z foo bar                            # Jump to directory matching "foo" and "bar"
  zoxide query foo                     # Query database for directories matching "foo"
  zoxide remove /path/to/dir           # Remove directory from database

tre                                    # Tree listing with numbered items for quick navigation - Install: cargo install tre-command
  apt install tre-command            # Install tre
  tre                                  # Show current directory tree with numbers
  tre /path/to/dir                     # Show specific directory tree
  tre -a                               # Include hidden files
  tre -L 3                             # Limit depth to 3 levels
  # After running tre, use numbers to navigate:
  cd 2                                 # Change to directory #2
  cat 5                                # View file #5
  vim 3                                # Edit file #3

# Documentation
tldr          # Simplified man pages with practical examples - Install: apt install tldr
  apt install tldr                     # Install tldr
  tldr ls                              # Get examples for ls command
  tldr tar                             # Get examples for tar command
  tldr --update                        # Update tldr database
  tldr --list                          # List all available commands

cheat         # Interactive cheat sheets - Install: snap install cheat
  cheat ls                             # Show cheat sheet for ls
  cheat -l                             # List available cheat sheets
  cheat -e ls                          # Edit cheat sheet for ls

navi          # Interactive cheat sheet tool - Install: cargo install navi
  navi                                 # Start interactive cheat sheet browser
  navi --print                         # Print command without executing

# Enhanced History Tools
atuin         # Shell history replacement with sync and search - Install: cargo install atuin
  cargo install atuin                  # Install atuin
  atuin import auto                    # Import existing history
  atuin sync                           # Sync history across machines
  # Ctrl+R for enhanced history search (after setup)
```

## 🎵 Multimedia & Data

### Commands
```bash
# Media Processing
ffmpeg        # Complete multimedia framework
imagemagick   # Image manipulation and conversion suite
convert       # ImageMagick image manipulation tool
pdftk         # PDF toolkit for manipulation
qrencode      # QR code generator
zbar          # QR/barcode scanner
exiftool      # Read/write metadata from files

# Download Tools
yt-dlp        # Download videos from YouTube and other sites
wget          # Network downloader
curl          # Transfer data to/from servers
axel          # Download accelerator

# Entertainment
ani-cli       # Anime streaming from terminal
manga-cli     # Manga reader for terminal

# Calculators
qalculate     # Advanced calculator with unit conversion
bc            # Arbitrary precision calculator
```

## 🔒 Network & Security

### Commands
```bash
# Network Tools
nmap          # Network discovery and security scanner
mtr           # Network diagnostic tool (traceroute + ping)
fping         # Send ICMP echo probes to network hosts
netstat       # Display network connections and routing tables
ss            # Socket statistics (netstat replacement)
whois         # Domain registration information lookup
dig +short yourdomain.com  # Check DNS A record of your domain
dog           # Modern DNS lookup client (better than dig)
http          # HTTPie command line HTTP client
nc            # Netcat - network utility for reading/writing network connections
ipcalc        # IP address calculator

# Password & Authentication Tools - Install: apt install sshpass expect
sshpass       # SSH password authentication tool
  sshpass -p 'password' ssh user@host        # SSH with password
  sshpass -f passwordfile ssh user@host      # SSH with password from file
  sshpass -p 'password' scp file user@host:/path  # SCP with password

expect        # Automate interactive programs with passwords
  expect -c "spawn su; expect 'Password:'; send 'password\r'; interact"  # Automate su command
  expect -c "spawn ssh user@host; expect 'password:'; send 'pass\r'; interact"  # Automate SSH

# Built-in password handling
sudo -S       # Read password from stdin
  echo 'password' | sudo -S command          # Sudo with password from stdin
  printf 'password\n' | sudo -S apt update   # Alternative syntax

# Security
age           # Simple, modern file encryption tool
pwgen         # Generate secure passwords
rip           # Safe deletion tool (better than rm)
strace        # System call tracer
```

## 🛡️ Security & Backup

### Commands
```bash
# Server Security
fail2ban      # Intrusion prevention system
ufw           # Uncomplicated firewall management
iptables      # Linux firewall administration
certbot       # Let's Encrypt SSL certificate management
openssl       # SSL/TLS toolkit

# Backup & Recovery
tar           # Archive files for backup
gzip/gunzip   # File compression utilities
mysqldump     # MySQL database backup
pg_dump       # PostgreSQL database backup
wp db export  # WordPress database export

# File Integrity
sha256sum     # Calculate SHA256 checksums
md5sum        # Calculate MD5 checksums
diff          # Compare files line by line
 Compare two saved versions:
 diff -u your_file.bak your_file.py
 View differences side-by-side:
 diff -y file1.py file2.py
dua-cli       # Disk usage analyzer (better than du)
```

## ⚡ Performance & Optimization

### Commands
```bash
# Web Performance
pagespeed     # Google PageSpeed Insights CLI
lighthouse    # Web page performance auditing
webpagetest   # Website speed testing
siege         # HTTP load testing utility
ab            # Apache HTTP server benchmarking tool

# Image Optimization
jpegoptim     # JPEG optimization utility
optipng       # PNG optimization program
webp          # WebP image conversion
imagemin      # Image minification

# Caching
varnish       # HTTP accelerator and caching
redis-cli     # Redis caching operations
memcached     # Distributed memory caching
```

## 📱 Mobile & Social Media

### Commands
```bash
# Social Media APIs
tweepy        # Twitter API Python library
facebook-cli  # Facebook Graph API tools
instagram-api # Instagram automation tools
linkedin-api  # LinkedIn API integration

# Mobile Development
adb           # Android Debug Bridge
fastboot      # Android bootloader interface
ionic         # Mobile app development
```

## 📈 eCommerce & Analytics

### Commands & APIs
```bash
# WordPress Management
wp            # Official WordPress CLI for site management
wp-cli-backup # WordPress backup automation via CLI

# Google Services APIs
google-ads    # Google Ads API integration scripts
google-analytics # Google Analytics reporting via API
google-search-console # Search Console data via API

# Database Management
mysql         # MySQL command line client
mysqldump     # MySQL database backup utility
wp db         # WordPress database operations

# System Utilities
watch         # Execute commands repeatedly and show output
cron          # Schedule automated tasks
systemctl     # Control systemd services
```

## 🛒 Web Scraping & Data Collection

### Commands
```bash
# Web Scraping
scrapy        # Professional web scraping framework
selenium      # Browser automation for dynamic content
puppeteer     # Headless Chrome automation
playwright    # Modern browser automation
beautifulsoup # Python HTML parsing library

# Data Processing
csvkit        # Command-line CSV processing toolkit
miller        # Data processing like awk/sed/cut for CSV/JSON
pandas        # Python data analysis (via scripts)
sqlite3       # Lightweight database for data storage

# API Testing & Development
httpie        # User-friendly HTTP client
postman-cli   # Postman API testing from command line
newman        # Postman collection runner
insomnia-cli  # Insomnia API client CLI
```

## 🔄 Automation & Deployment

### Commands
```bash
# Container Management
docker        # Container platform for application deployment
docker-compose # Multi-container Docker applications
podman        # Alternative container engine

# Process Automation
ansible       # Infrastructure automation and configuration
fabric        # Python deployment automation
pm2           # Node.js process manager
supervisor    # Process control system

# Backup & Sync
borgbackup    # Deduplicating backup program
duplicity     # Encrypted backup using rsync
restic        # Modern backup program
lsyncd        # Live syncing daemon

# Job Queues
redis-server  # In-memory data store for queues
celery        # Distributed task queue
pueue         # Command-line task management
```

## 💰 Financial & Business Intelligence

### Commands & Tools
```bash
# Cryptocurrency & Payments
ccxt          # Cryptocurrency exchange trading library
stripe-cli    # Stripe payment platform CLI
paypal-cli    # PayPal API command line tools

# Price Monitoring
price-tracker # Custom scripts for competitor price monitoring
curl + jq     # API-based price fetching and processing

# Business Analytics
metabase      # Open source business intelligence
grafana-cli   # Grafana dashboard management
```

## 🔧 Apps & Utilities

### Terminal Enhancements
- **fish/zsh** - Advanced shells with better autocompletion
  ```bash
  # Fish shell - Install: apt install fish
  apt install fish                     # Install fish shell
  chsh -s /usr/bin/fish               # Set as default shell
  fish_config                         # Open web-based configuration
  
  # Zsh with Oh My Zsh - Install: apt install zsh
  apt install zsh                     # Install zsh
  sh -c "$(curl -fsSL https://raw.github.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"  # Install Oh My Zsh
  chsh -s /bin/zsh                    # Set as default shell
  ```
- **oh-my-zsh** - Framework for managing Zsh configuration
- **neovim** - Modern Vim with better plugin support
- **micro** - Modern terminal text editor
- **lynx** - CLI web browser
  ```bash
  lynx https://example.com
  ```
- **browsh** - Modern CLI web browser with graphics support
  ```bash
  browsh
  ```
- **w3m** - Text-based web browser
- **cmus** - Terminal music player
- **mutt** - Terminal email client
- **newsboat** - RSS feed reader
- **buku** - Terminal bookmark manager
- **weechat** - Extensible chat client
- **fasd** - Command-line productivity booster

### System Tools
- **chezmoi** - Manage dotfiles across multiple machines
- **stow** - Symlink farm manager for dotfiles
- **topgrade** - Upgrade all the things with one command
- **lazydocker** - Terminal Docker management
- **kdash** - Kubernetes dashboard
- **taskwarrior** - Command-line task management

### Window Managers & Desktop Environment
- **niri** - Scrollable-tiling Wayland compositor - Install: Build from source
  ```bash
  # Install dependencies (Ubuntu/Debian)
  sudo apt install build-essential rustc cargo libxkbcommon-dev \
    libwayland-dev libinput-dev libdbus-1-dev libsystemd-dev \
    libudev-dev libseat-dev libdrm-dev libgbm-dev libegl-dev \
    libgles2-mesa-dev libpango1.0-dev libcairo-gobject2 \
    libgtk-4-dev libadwaita-1-dev
  
  # Clone and build niri
  git clone https://github.com/YaLTeR/niri.git
  cd niri
  cargo build --release
  
  # Install binary
  sudo cp target/release/niri /usr/local/bin/
  
  # Create config directory and copy example config
  mkdir -p ~/.config/niri
  cp resources/default-config.kdl ~/.config/niri/config.kdl
  
  # Start niri (from TTY)
  niri
  ```

### Fun & Productivity
- **fortune + cowsay + lolcat** - Fun terminal messages
- **fortune** - Random quote generator
- **cava** - Console audio visualizer
- **tty-clock** - Terminal clock
- **thefuck** - Correct previous console commands
- **figlet** - Create ASCII art text
- **neofetch** - System information display
- **xsel** - Access X clipboard from command line

## 🚀 Installation Examples

### Ubuntu/Debian
```bash
# Essential tools and dependencies
sudo apt update && sudo apt install -y \
  htop ncdu duf bat exa fd-find ripgrep \
  tmux git curl wget ffmpeg imagemagick \
  tree mc ranger vim neovim mysql-client \
  fail2ban ufw certbot jpegoptim optipng \
  python3-pip

# Web scraping tools
pip3 install scrapy beautifulsoup4 selenium requests

# Modern alternatives (via snap/cargo)
sudo snap install btop docker
cargo install lsd zoxide tokei hyperfine
```

### Hetzner Cloud Specific Setup
```bash
# Install essential server tools for eCommerce
curl -fsSL https://get.docker.com -o get-docker.sh
sudo sh get-docker.sh

# WordPress CLI
curl -O https://raw.githubusercontent.com/wp-cli/builds/gh-pages/phar/wp-cli.phar
chmod +x wp-cli.phar
sudo mv wp-cli.phar /usr/local/bin/wp

# Cloudflare Wrangler
npm install -g wrangler

# Setup authentication (after creating API token with Workers permissions)
export CLOUDFLARE_API_TOKEN=your_token_here
# Or add to ~/.bashrc for persistence:
echo 'export CLOUDFLARE_API_TOKEN=your_token_here' >> ~/.bashrc

# Verify authentication
wrangler whoami

# Google Cloud CLI
curl https://sdk.cloud.google.com | bash
```

### Redis & Caching Setup
```bash
# Install caching services
sudo apt install redis-server memcached -y
sudo systemctl enable redis-server memcached
```

### Using Package Managers
```bash
# Rust tools
cargo install bat exa fd-find ripgrep lsd zoxide tokei hyperfine

# Node.js tools
npm install -g @cloudflare/wrangler
npm install -g @google-cloud/cli
npm install -g lighthouse pagespeed

# Python tools
pip install yt-dlp speedtest-cli glances
pip install gspread google-analytics-data
pip install scrapy selenium beautifulsoup4
pip install stripe ccxt
```

## 💡 Pro Tips for eCommerce

1. **Automate backups** using cron + mysqldump + rsync to backup to multiple locations
2. **Monitor competitor prices** using curl + jq in scheduled scripts
3. **Use Redis** for WordPress object caching to improve performance
4. **Set up fail2ban** to protect against brute force attacks
5. **Use Cloudflare Wrangler** for edge computing and caching
6. **Implement monitoring** with scripts that check site health every 5 minutes
7. **Use tmux sessions** for long-running scraping tasks
8. **Set up SSL auto-renewal** with certbot for your domains
9. **Use docker** for isolated scraping environments
10. **Monitor server resources** with glances/htop to prevent crashes

## 🚀 Essential Linux Time-Saving Shortcuts & Commands

### Command History & Navigation
```bash
# History shortcuts
!!                                   # Run previous command (great for sudo !!)
!$                                   # Last argument of previous command
!*                                   # All arguments of previous command
!n                                   # Run command number n from history
^old^new^                           # Replace 'old' with 'new' in previous command

# Directory navigation
cd -                                # Switch to previous directory
pushd /path && popd                 # Directory stack navigation
dirs -v                             # Show directory stack with numbers

# Terminal shortcuts
Ctrl+R                              # Reverse search through command history
Ctrl+L                              # Clear screen (faster than typing 'clear')
Ctrl+A                              # Jump to beginning of line
Ctrl+E                              # Jump to end of line
Ctrl+U                              # Delete from cursor to beginning of line
Ctrl+K                              # Delete from cursor to end of line
Ctrl+W                              # Delete word before cursor
Alt+B                               # Move back one word
Alt+F                               # Move forward one word
Alt+D                               # Delete word after cursor
Ctrl+D                              # Exit terminal or end input
Ctrl+Z                              # Suspend current process
fg                                  # Bring suspended process to foreground
bg                                  # Send suspended process to background

# Advanced history features
fc                                  # Edit last command in $EDITOR
history | grep pattern              # Search command history
export HISTCONTROL=ignoreboth       # Ignore duplicates and commands starting with space
export HISTSIZE=10000               # Increase history size
export HISTTIMEFORMAT='%F %T '      # Add timestamps to history
```

### File Operations & Text Processing
```bash
# Quick file operations
ls *                                # List files in all subdirectories (one level)
mv * ..                             # Move all files to parent directory
cp file{,.bak}                      # Quick backup (copies file to file.bak)

# Text processing shortcuts
sort | uniq                         # Sort and remove duplicates
grep -r "pattern" .                 # Recursive search in current directory
find . -name "*.py" | xargs grep "pattern"  # Search pattern in Python files

# Pipe operations for data processing
cat file | grep pattern | sort | uniq -c | sort -nr  # Count occurrences, sort by frequency
```

### Process & System Management
```bash
# Process management
ps aux | grep process_name          # Find process by name
kill -9 $(pgrep process_name)       # Kill process by name
nohup command &                     # Run command in background, immune to hangups
disown                              # Remove job from shell's job table

# System information shortcuts
df -h                               # Disk usage in human-readable format
free -h                             # Memory usage in human-readable format
lscpu                               # CPU information
lsblk                               # List block devices
```

### Aliases & Functions for Productivity
```bash
# Add these to ~/.bashrc or ~/.zshrc
alias c='clear'                     # Quick clear
alias l='ls -la'                    # Detailed file listing
alias ..='cd ..'                    # Go up one directory
alias ...='cd ../..'                # Go up two directories
alias p8='ping 8.8.8.8'            # Quick ping test
alias h='history'                   # Short history command
alias grep='grep --color=auto'     # Colorized grep

# Useful functions
cdls() { cd "$1" && ls; }           # Change directory and list contents
mkcd() { mkdir -p "$1" && cd "$1"; } # Create directory and enter it
extract() {                         # Universal extract function
  if [ -f $1 ] ; then
    case $1 in
      *.tar.bz2)   tar xjf $1     ;;
      *.tar.gz)    tar xzf $1     ;;
      *.bz2)       bunzip2 $1     ;;
      *.rar)       unrar e $1     ;;
      *.gz)        gunzip $1      ;;
      *.tar)       tar xf $1      ;;
      *.tbz2)      tar xjf $1     ;;
      *.tgz)       tar xzf $1     ;;
      *.zip)       unzip $1       ;;
      *.Z)         uncompress $1  ;;
      *.7z)        7z x $1        ;;
      *)     echo "'$1' cannot be extracted via extract()" ;;
    esac
  else
    echo "'$1' is not a valid file"
  fi
}
```

### Advanced Shell Features
```bash
# Zsh-specific shortcuts (if using zsh)
# Double ESC                        # Add sudo to previous command (zsh)
# Ctrl+X Ctrl+E                     # Edit command in $EDITOR

# Bash-specific features
set -o vi                           # Enable vi mode in bash
bind '"\C-l": clear-screen'         # Bind Ctrl+L to clear screen

# Tab completion enhancements
# Install bash-completion: apt install bash-completion
# Add to ~/.bashrc: source /etc/bash_completion
```

## 🔧 Specific eCommerce Workflows

### Daily Site Health Check
```bash
#!/bin/bash
# Site health monitoring script
curl -s -o /dev/null -w "%{http_code}" https://nilgiristores.in
wp core check-update --path=/var/www/html
mysqldump -u root -p ecommerce_db > backup_$(date +%Y%m%d).sql
```

### Product Data Scraping
```bash
# Use with scrapy for marketplace data
scrapy crawl amazon_products -o products_$(date +%Y%m%d).json
python3 process_products.py
mysql -u root -p ecommerce_db < import_products.sql
```

### Performance Optimization
```bash
# Image optimization workflow
find /var/www/html/wp-content/uploads -name "*.jpg" -exec jpegoptim {} \;
find /var/www/html/wp-content/uploads -name "*.png" -exec optipng {} \;
wp cache flush --path=/var/www/html
```

## 📚 Additional Resources

- [Modern Unix Tools](https://github.com/ibraheemdev/modern-unix) - Comprehensive list of modern CLI alternatives
- [Terminal Trove](https://terminaltrove.com/) - Discover new CLI tools
- [Command Line Interface Guidelines](https://clig.dev/) - Best practices for CLI design

---

**Note:** Some tools may require additional setup or API keys for full functionality. Always verify installation instructions from official sources.

> 💡 **For eCommerce owners:** Focus on automation tools (rsync, rclone, watch), monitoring (htop, glances, speedtest-cli), and API integrations (Google services, WordPress CLI) to streamline your operations.