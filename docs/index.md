# MkDocs Project Setup Guide

## 1. Create New MkDocs Environment
```bash
mkdocs new .
```
## 2. Configure mkdocs.yml
```yaml
site_name: Rui Bo Blog
site_url: https://mydomain.org/mysite
theme:
  name: readthedocs
  highlightjs: true
  hljs_languages:
    - yaml
    - rus
```
## 3. Build and Serve Documentation
```bash
mkdocs serve
```
## 4. Transfer to Github
```bash
git init
git status

# (1) Stage and (2) Confirm
git add .
git add -A
git add docs/index.md README.md
git commit -m "Initial commit"

git remote add origin https://github.com/your-username/PhD-Thoughts.git
git remote remove origin

git push -u origin main
git pull origin main
```