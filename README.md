# davelee.uk

![GitHub Actions Workflow Status](https://img.shields.io/github/actions/workflow/status/thelovebug/davelee.uk/hugo.yml)
![GitHub repo size](https://img.shields.io/github/repo-size/thelovebug/davelee.uk)
![GitHub contributors](https://img.shields.io/github/contributors/thelovebug/davelee.uk)
![GitHub stars](https://img.shields.io/github/stars/thelovebug/davelee.uk)
![GitHub forks](https://img.shields.io/github/forks/thelovebug/davelee.uk)
![Twitter Follow](https://img.shields.io/twitter/follow/thelovebug?style=social)
![Coffee status](https://img.shields.io/badge/coffee-strong_and_hot-red?logo=coffeescript)

This repo holds the files of my blog [davelee.uk](https://davelee.uk).

This blog is built with [Hugo](https://gohugo.io/), one of the most popular and fast open-source static site generators.

## Set up the blog for local development

### Requirements

[Hugo](https://gohugo.io/) and [Git](https://git-scm.com/) must be installed and configured.

### Cloning

```bash
# Clone the repo
git clone git@github.com:thelovebug/davelee.uk.git

# Pull the theme files (Git submodule)
git submodule update --init --recursive
```

### Updating

```bash
# Update the repo
git pull

# Update the theme files (Git submodule)
git submodule update --remote --merge
```

### Testing

```bash
# Start Hugo locally
hugo server -D --disableFastRender --bind 0.0.0.0 --baseURL http://<LAN_IP>:1313
# This will serve the blog to all LAN addresses, so tests can be made from multiple devices.
```
