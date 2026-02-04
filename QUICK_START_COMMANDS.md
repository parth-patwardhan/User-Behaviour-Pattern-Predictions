# Quick Start Commands - Copy & Paste Ready!

## 🚀 Essential Git Commands (Copy these in order)

### 1. First-Time Git Configuration (Skip if already done)
```bash
git config --global user.name "Your Name"
git config --global user.email "your.email@example.com"
```

### 2. Initialize and Commit (Run in project directory)
```bash
# Initialize repository
git init

# Add all files
git add .

# Create initial commit
git commit -m "Initial commit: GNN-based User Behaviour Pattern Prediction

Features:
- Graph Attention Networks (GAT) implementation
- Temporal Graph Networks (TGN) implementation
- JODIE baseline comparison
- Experiments on Wikipedia, Reddit, Last.fm datasets
- Hyperparameter optimization via grid search
- Comprehensive evaluation metrics (Recall@K, MRR, AUC)
- Complete documentation with setup guides"
```

### 3. Create GitHub Repository
**Go to:** https://github.com/new

**Settings:**
- Repository name: `User-Behaviour-Pattern-Prediction`
- Description: `Deep Learning with Graph Neural Networks (GAT, TGN) for user behaviour prediction in temporal interaction networks`
- Visibility: ✅ Public
- ❌ **Do NOT check** "Add README file"
- ❌ **Do NOT check** "Add .gitignore"
- ❌ **Do NOT check** "Choose a license"

Click **"Create repository"**

### 4. Connect and Push to GitHub
```bash
# Replace 'YOUR-GITHUB-USERNAME' with your actual username!
git remote add origin https://github.com/YOUR-GITHUB-USERNAME/User-Behaviour-Pattern-Prediction.git

# Rename branch to main
git branch -M main

# Push to GitHub
git push -u origin main
```

## 🎯 After Pushing - Make It Stand Out!

### Add Topics on GitHub
Go to your repository page and click "⚙️ Add topics", then add:
```
deep-learning, graph-neural-networks, pytorch, gnn, temporal-networks,
user-behavior-prediction, attention-mechanism, link-prediction,
pytorch-geometric, machine-learning, graph-attention-networks
```

### Pin Repository
- Go to your GitHub profile
- Click "Customize your pins"
- Select this repository to feature it prominently

### Add Description Badge in Repository
The README already has these badges:
- Python version
- PyTorch
- MIT License
- Deep Learning/GNN indicator

## 📦 Complete Command Sequence

**Copy and paste this entire block** (remember to replace YOUR-GITHUB-USERNAME):

```bash
# Navigate to project directory
cd /Users/parthpatwardhan/Downloads/User-Behaviour-Pattern-Prediction-main

# Initialize Git
git init

# Add all files
git add .

# Commit with detailed message
git commit -m "Initial commit: GNN-based User Behaviour Pattern Prediction

Features:
- Graph Attention Networks (GAT) implementation
- Temporal Graph Networks (TGN) implementation
- JODIE baseline comparison
- Experiments on Wikipedia, Reddit, Last.fm datasets
- Hyperparameter optimization via grid search
- Comprehensive evaluation metrics (Recall@K, MRR, AUC)
- Complete documentation with setup guides"

# Add remote (REPLACE YOUR-GITHUB-USERNAME!)
git remote add origin https://github.com/YOUR-GITHUB-USERNAME/User-Behaviour-Pattern-Prediction.git

# Set main branch
git branch -M main

# Push to GitHub
git push -u origin main
```

## 🔧 If You Encounter Issues

### Authentication Error (Password not working)
GitHub no longer accepts passwords. Use a Personal Access Token:

1. Go to: https://github.com/settings/tokens
2. Click "Generate new token (classic)"
3. Select scopes: `repo` (full control)
4. Generate and copy the token
5. Use this token as your password when Git asks

### Repository Already Exists
```bash
# Remove the remote and re-add
git remote remove origin
git remote add origin https://github.com/YOUR-GITHUB-USERNAME/User-Behaviour-Pattern-Prediction.git
git push -u origin main
```

### "Updates were rejected"
```bash
# Force push (only for first push)
git push -u origin main --force
```

## 📝 Future Updates

After making changes:
```bash
git add .
git commit -m "Description of your changes"
git push
```

## ✅ Success Checklist

After running the commands:
- [ ] Repository visible at `github.com/YOUR-USERNAME/User-Behaviour-Pattern-Prediction`
- [ ] README displays correctly with badges
- [ ] All files pushed (check on GitHub)
- [ ] No large data files uploaded (should be in .gitignore)
- [ ] Topics added
- [ ] Repository description set
- [ ] Repository pinned on your profile (optional but recommended)

## 🌟 Share Your Work

Your project will be at:
```
https://github.com/YOUR-GITHUB-USERNAME/User-Behaviour-Pattern-Prediction
```

Add this to:
- Your resume/CV
- LinkedIn projects section
- Portfolio website
- Research papers (if applicable)

## 📊 What's Included in Your Repository

✅ **Code & Notebooks:**
- GAT_Implementation.ipynb (Graph Attention Networks)
- LASTFM_Datset_Test_1.ipynb (Reddit experiments)
- Test_2.ipynb (Temporal GCN-GRU)
- Temporal Graph Network implementation
- JODIE baseline implementation

✅ **Documentation:**
- Comprehensive README with badges
- Setup guide
- Git instructions
- Requirements files
- License (MIT)

✅ **Research Materials:**
- AI Lab Report PDF (1.2 MB)
- Presentation PDF (577 KB)

✅ **Configuration:**
- .gitignore (prevents large files)
- requirements.txt (all dependencies)
- Project structure documentation

## 🎓 Pro Tips

1. **Star your own repository** - Adds credibility
2. **Write a good repository description** - Helps in GitHub search
3. **Add topics** - Makes it discoverable
4. **Keep README updated** - As you add features
5. **Add release tags** - For major milestones
   ```bash
   git tag -a v1.0 -m "First stable release"
   git push origin v1.0
   ```

## 📈 Track Your Impact

After pushing, you can see:
- Repository views (Insights > Traffic)
- Clones and forks (Insights > Traffic)
- Stars and watchers (Main page)

---

**You're all set! Your Deep Learning project is now ready to impress! 🚀**
