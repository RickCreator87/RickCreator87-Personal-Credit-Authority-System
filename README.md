

# Create base directory structure
create_base_structure() {
    log_info "Creating base directory structure..."
    
    mkdir -p "$BASE_DIR"
    cd "$BASE_DIR"
    
    # Create README for base directory
    cat > README.md << 'EOF'
# RickCreator87 Personal Credit Authority System
## Tax-First, Dual-Founder Governance Architecture

## SYSTEM OVERVIEW
This directory contains the complete RickCreator87 Credit Authority ecosystem,
enforcing tax-first principles and dual-founder governance.

## REPOSITORY STRUCTURE
1. `rickcreator87-credit-authority/` - Core governance & orchestration
2. `rickcreator87-loaner-ledger/` - Dual ledger system with tax separation
3. `rickcreator87-loaner-agreements/` - Tax-first agreement templates
4. `rickcreator87-tax-blocks/` - Federal & state tax compliance engine
5. `rickcreator87-credit-tools/` - Development & utility tools
6. `rickcreator87-loan-disbursement/` - Tax-gated payment distribution
7. `rickcreator87-governance/` - Dual-founder authority framework

## SECURITY CLASSIFICATION
- LEVEL 1 (GOVERNANCE): Founder-only access
- LEVEL 2 (FINANCIAL/LEGAL): Founders + Compliance Officer
- LEVEL 3 (TAX): Founder-only access
- LEVEL 4 (UTILITY): Public with contributor guidelines

## SETUP INSTRUCTIONS
1. Run setup-system.sh to initialize all repos
2. Configure access controls based on sensitivity
3. Initialize tax-first workflow engine
4. Set up dual-founder approval mechanisms

## EMERGENCY CONTACT
RickCreator87 - Primary Founder & Tax Authority
EOF
    
    log_success "Base directory structure created"
}

# Initialize Git repository
init_repo() {
    local repo_name="$1"
    local sensitivity="${SENSITIVITY[$repo_name]}"
    
    log_info "Initializing $repo_name ($sensitivity)..."
    
    mkdir -p "$repo_name"
    cd "$repo_name"
    
    # Initialize Git repo
    git init
    
    # Create .gitattributes for sensitive files
    create_gitattributes "$sensitivity"
    
    # Create .gitignore
    create_gitignore "$repo_name"
    
    # Create README
    create_readme "$repo_name" "$sensitivity"
    
    # Create LICENSE
    create_license "$repo_name"
    
    # Create initial commit
    git add .
    git commit -m "Initial commit: $repo_name - $sensitivity classification"
    
    cd ..
    log_success "Repository $repo_name initialized"
}

# Create .gitattributes based on sensitivity
create_gitattributes() {
    local sensitivity="$1"
    
    cat > .gitattributes << EOF
# Git Attributes for $sensitivity Classification
# Auto-configured by RickCreator87 Setup Script

# Text files
*.md text
*.txt text
*.json text
*.yml text
*.yaml text
*.xml text

# Binary files
*.pdf binary
*.doc binary
*.docx binary
*.xls binary
*.xlsx binary
*.png binary
*.jpg binary

# Encryption for sensitive files
*.$sensitivity filter=crypt diff=crypt
*.secret filter=crypt diff=crypt

# Line endings
*.md text eol=lf
*.txt text eol=lf
*.json text eol=lf
*.sh text eol=lf
*.py text eol=lf

# Export-ignore for archives
/.github export-ignore
/.gitignore export-ignore
/.gitattributes export-ignore

# Git LFS for large files
*.pdf filter=lfs diff=lfs merge=lfs -text
*.mp4 filter=lfs diff=lfs merge=lfs -text
*.zip filter=lfs diff=lfs merge=lfs -text
EOF
}

# Create .gitignore based on repo type
create_gitignore() {
    local repo_name="$1"
    
    cat > .gitignore << EOF
# RickCreator87 Credit Authority - $repo_name
# Auto-generated Git Ignore File

# System files
.DS_Store
Thumbs.db
desktop.ini

# IDE files
.vscode/
.idea/
*.swp
*.swo

# Python
__pycache__/
*.py[cod]
*$py.class
*.so
.Python
env/
venv/
ENV/
env.bak/
venv.bak/

# Node.js
node_modules/
npm-debug.log*
yarn-debug.log*
yarn-error.log*

# Secrets and sensitive data
*.env
*.secret
*.key
*.pem
*.crt
*.p12
*.pfx

# Temporary files
*.tmp
*.temp
*.log
*.cache

# Backup files
*.bak
*.backup
*.old

# OS generated files
ehthumbs.db
Icon?
._*

# Project specific ignores
/temp/
/tmp/
/scratch/
/backup/
EOF
}



# RickCreator87-Personal-Credit-Authority-System
