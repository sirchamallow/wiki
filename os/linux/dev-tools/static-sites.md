# 🏠 Static Sites

## Jekyll

```bash
sudo dnf install ruby-devel	# Installation
gem install jekyll		# Installation gem jekyll
jekyll new my-site 		# Create new site
cd my-site			# Navigate to new site
jekyll serve			# Launch server (http://localhost:4000)
```

Source : [https://developer.fedoraproject.org/start/sw/web-app/jekyll.html](https://developer.fedoraproject.org/start/sw/web-app/jekyll.html)

## Hugo

### Installation

```bash
sudo dnf install hugo		# Installation
hugo new site my-site		# Creating a new website
cd my-site			# Navigate to new site
git init			# Add a theme (ex: themes/ananke)
git submodule add https://github.com/budparr/gohugo-theme-ananke.git
hugo server			# Launch server
```

Sourcce : [https://developer.fedoraproject.org/start/sw/web-app/hugo.html](https://developer.fedoraproject.org/start/sw/web-app/hugo.html)

### Thèmes

Stack : [https://github.com/CaiJimmy/hugo-theme-stack/](https://github.com/CaiJimmy/hugo-theme-stack/)
