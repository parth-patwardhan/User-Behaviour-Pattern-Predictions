# Git Setup and Push Instructions

## Prerequisites

1. Install Git: https://git-scm.com/downloads
2. Create a GitHub account: https://github.com
3. Configure Git with your credentials:

```bash
git config --global user.name "Your Name"
git config --global user.email "your.email@example.com"
```

## Step-by-Step Git Setup

### Step 1: Initialize Git Repository

```bash
# Navigate to your project directory
cd /Users/parthpatwardhan/Downloads/User-Behaviour-Pattern-Prediction-main

# Initialize git repository
git init
```

### Step 2: Add All Files

```bash
# Add all files to staging (respects .gitignore)
git add .

# Check what will be committed
git status
```

### Step 3: Create Initial Commit

```bash
# Create your first commit
git commit -m "Initial commit: User Behaviour Pattern Prediction with GNNs

- Implemented GAT (Graph Attention Networks) for user behavior prediction
- Added TGN (Temporal Graph Networks) implementation
- Included JODIE baseline for comparison
- Added comprehensive experiments on Wikipedia, Reddit datasets
- Hyperparameter optimization with grid search
- Detailed README with badges and documentation
- Setup guide and requirements for easy reproduction"
```

### Step 4: Create GitHub Repository

1. Go to https://github.com/new
2. Repository name: `User-Behaviour-Pattern-Prediction`
3. Description: "Deep Learning project using Graph Neural Networks (GAT, TGN) for predicting user behaviour patterns in temporal interaction networks"
4. Choose Public (to make it visible and stand out)
5. **DO NOT** initialize with README, .gitignore, or license (we already have them)
6. Click "Create repository"

### Step 5: Connect Local Repository to GitHub

```bash
# Replace 'your-username' with your actual GitHub username
git remote add origin https://github.com/your-username/User-Behaviour-Pattern-Prediction.git

# Verify the remote was added
git remote -v
```

### Step 6: Push to GitHub

```bash
# Push your code to GitHub (main branch)
git push -u origin main

# If you get an error about 'master' vs 'main', use:
# git branch -M main
# git push -u origin main
```

### Alternative: Using SSH (Recommended for Security)

If you prefer SSH over HTTPS:

```bash
# Generate SSH key (if you don't have one)
ssh-keygen -t ed25519 -C "your.email@example.com"

# Add SSH key to ssh-agent
eval "$(ssh-agent -s)"
ssh-add ~/.ssh/id_ed25519

# Copy your public key
cat ~/.ssh/id_ed25519.pub
# Copy the output and add it to GitHub: Settings > SSH and GPG keys > New SSH key

# Use SSH remote instead
git remote remove origin
git remote add origin git@github.com:your-username/User-Behaviour-Pattern-Prediction.git
git push -u origin main
```

## Making Your Repository Stand Out

### Add GitHub Topics

After pushing, go to your repository on GitHub and click "Add topics":

```
deep-learning
graph-neural-networks
pytorch
gnn
temporal-networks
user-behavior-prediction
attention-mechanism
link-prediction
pytorch-geometric
machine-learning
```

### Create a Nice Repository Description

Set repository description to:
```
Graph Neural Networks (GAT, TGN) for user behaviour pattern prediction | PyTorch | Temporal interaction networks | Link prediction
```

### Add Repository Social Preview

1. Go to repository Settings
2. Scroll to "Social preview"
3. Upload an image (you could create a simple diagram of your architecture)

### Enable GitHub Pages (Optional)

If you want to host documentation:

1. Go to Settings > Pages
2. Source: Deploy from a branch
3. Branch: main / docs
4. This makes your documentation accessible at `https://your-username.github.io/User-Behaviour-Pattern-Prediction/`

## Future Updates

### Making Changes and Pushing Updates

```bash
# After making changes to files
git add .
git commit -m "Description of changes"
git push
```

### Creating Branches for New Features

```bash
# Create and switch to a new branch
git checkout -b feature/new-experiment

# Make changes, commit
git add .
git commit -m "Add new experiment"

# Push the branch
git push -u origin feature/new-experiment

# Create a Pull Request on GitHub to merge into main
```

### Useful Git Commands

```bash
# View commit history
git log --oneline --graph --all

# See what files changed
git status

# See detailed changes
git diff

# Undo last commit (keep changes)
git reset --soft HEAD~1

# Pull latest changes from GitHub
git pull

# Clone your repository on another machine
git clone https://github.com/your-username/User-Behaviour-Pattern-Prediction.git
```

## Quick Reference: All Commands in Order

```bash
# 1. Initialize
git init

# 2. Configure (first time only)
git config --global user.name "Your Name"
git config --global user.email "your.email@example.com"

# 3. Add files
git add .

# 4. Commit
git commit -m "Initial commit: User Behaviour Pattern Prediction with GNNs"

# 5. Add remote (replace your-username)
git remote add origin https://github.com/your-username/User-Behaviour-Pattern-Prediction.git

# 6. Rename branch to main (if needed)
git branch -M main

# 7. Push
git push -u origin main
```

## Troubleshooting

### Issue: "repository not found"
- Check the repository URL
- Ensure the repository exists on GitHub
- Verify you have access rights

### Issue: Authentication failed
- For HTTPS: Use GitHub Personal Access Token instead of password
  - Go to Settings > Developer settings > Personal access tokens
  - Generate new token with 'repo' scope
  - Use token as password when prompted

### Issue: "failed to push some refs"
```bash
# Pull first, then push
git pull origin main --allow-unrelated-histories
git push -u origin main
```

### Issue: Large files error
```bash
# If you accidentally tried to commit large datasets
git rm --cached data/*.csv
git commit --amend
git push -u origin main
```

## Making It Even Better

### Add GitHub Actions for CI/CD

Create `.github/workflows/test.yml`:

```yaml
name: Test Models
on: [push, pull_request]
jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v2
      - uses: actions/setup-python@v2
        with:
          python-version: 3.8
      - name: Install dependencies
        run: pip install -r requirements.txt
      - name: Run tests
        run: pytest tests/  # if you add tests
```

### Add Issue Templates

Create `.github/ISSUE_TEMPLATE/bug_report.md` for better issue tracking

### Add CONTRIBUTING.md

Guidelines for others who want to contribute

## Success Checklist

- [ ] Git initialized
- [ ] All files committed
- [ ] GitHub repository created
- [ ] Remote added
- [ ] Code pushed successfully
- [ ] Repository is public
- [ ] Topics added
- [ ] Description set
- [ ] README looks good on GitHub
- [ ] License file present
- [ ] .gitignore working (no large data files pushed)

## Your Repository URL

After setup, your repository will be at:
```
https://github.com/your-username/User-Behaviour-Pattern-Prediction
```

Share this link to showcase your work!
