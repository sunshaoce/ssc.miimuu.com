+++
title = 'Build Hugo on Github Pages'
date = 2026-01-05T21:32:11+08:00
draft = false
+++

# Build Hugo on Github Pages

## Install Hugo

Best to install the latest hugo_extended version, or you may easily run into problems.

```bash
# MacOS
brew install hugo

# Ubuntu
# https://github.com/gohugoio/hugo/releases
# Download the latest hugo_extended version, for example: hugo_extended_0.154.2_linux-amd64.deb
# Don't use apt-get to install hugo, as the version is usually outdated.
sudo dpkg -i hugo_extended_0.154.2_linux-amd64.deb
```

## Create a new Hugo site

```bash
hugo new site YOUR_SITE_NAME
cd YOUR_SITE_NAME
```

## Initialize git repository

```bash
git init
git add .
git commit -m "Initial commit"
```

## Add a theme
Choose a theme from [Hugo Themes](https://themes.gohugo.io/) and follow the instructions to add it to your site.
For example, to add the Ananke theme:

```bash
git submodule add https://github.com/theNewDynamic/gohugo-theme-ananke.git themes/ananke
echo "theme = 'ananke'" >> hugo.toml
git add .
git commit -m "Add Ananke theme"
```

## Create a new post

```bash
hugo new content content/posts/my-first-post.md
vim content/posts/my-first-post.md
git add .
git commit -m "Add my first post"
```

## New Github repository

Create a new repository on Github, for example: `YOUR_SITE_NAME`.

Then continue to add the remote repository in the local `YOUR_SITE_NAME` directory.

```bash
git remote add origin https://github.com/YOUR_USERNAME/YOUR_SITE_NAME.git
git branch -M main
git push -u origin main
```

## Create Github Actions workflow

Click `Settings` -> `Pages` -> `Build and deployment` -> `Source` -> Select `GitHub Actions` -> Select Hugo

Then revise the `HUGO_VERSION:` to the latest version, for example `HUGO_VERSION: 0.154.2`

Finally, click `commit these changes`.

## Visit your site

After CI/CD is done, visit `https://YOUR_USERNAME.github.io/YOUR_SITE_NAME/` to see your new Hugo site!
