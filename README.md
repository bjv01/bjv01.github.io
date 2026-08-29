# Bernardo Villegas Moreno - Personal Academic Website

This repository contains the source code for my personal academic website, hosted at [bjv01.github.io](https://bjv01.github.io/).

> **2026 redesign:** the homepage is now a custom single-page site rendered via `layouts/index.html` (with `content/_index.md` neutralized). See [`REDESIGN.md`](REDESIGN.md) for how it is built, how to edit/redeploy, and how to roll back. The previous Hugo Blox site is preserved on the `previous-site` branch.

## About

I'm a PhD candidate at the Center for Human-Inspired Artificial Intelligence (CHIA), University of Cambridge. My research investigates the externalities of human-AI interaction—what happens when AI-assisted work flows to colleagues, patients, or decision-makers who weren't present.

The site features a minimalist design with underscore-prefixed navigation:

- **_me**: Extended biography and background
- **_research**: Current projects and research focus
- **_publications**: Links to Google Scholar profile
- **_cv**: Downloadable CV
- **_contact**: Direct email contact

## Technical Stack

- **Static Site Generator**: [Hugo](https://gohugo.io/) (v0.152.2+extended)
- **Theme**: [Hugo Blox Builder](https://hugoblox.com/) (Academic Resume template)
- **Hosting**: GitHub Pages
- **Deployment**: Automatic deployment via GitHub Actions

## Project Structure

```
bjv/
├── assets/           # Custom CSS and other assets
├── content/          # Site content (markdown files)
│   ├── _index.md     # Homepage (biography block)
│   ├── me.md         # About page
│   ├── research.md   # Research page
│   ├── authors/      # Author profiles
│   └── publications/ # Publication entries
├── config/          # Hugo configuration
│   └── _default/    # Default configuration files
├── static/          # Static files (images, CV)
└── resources/       # Generated resources
```

## Local Development

### Prerequisites

- Hugo Extended (v0.152.2 or higher)
- Git

### Installation

1. Clone the repository:
```bash
git clone https://github.com/bjv01/bjv01.github.io.git
cd bjv01.github.io
```

2. Install Hugo modules:
```bash
hugo mod get -u
```

### Running Locally

Start the Hugo development server:

```bash
hugo server -D
```

The site will be available at `http://localhost:1313/`

The server supports hot-reloading, so changes to content files will automatically refresh in your browser.

### Building for Production

To build the static site:

```bash
hugo
```

The generated files will be in the `public/` directory.

## Customization

### Design

The site uses a minimalist zinc color scheme with a clean, academic aesthetic. The logo displays as `_bjv` in the navbar.

### Content

- **Homepage**: Edit `content/_index.md` (biography block configuration)
- **About page**: Edit `content/me.md`
- **Research page**: Edit `content/research.md`
- **Profile data**: Update `content/authors/admin/_index.md` (education, work, skills, awards)
- **Navigation**: Modify `config/_default/menus.yaml`

### Site Configuration

Main configuration files:
- `config/_default/hugo.yaml` - General Hugo settings
- `config/_default/params.yaml` - Theme parameters, SEO, and navbar logo
- `config/_default/menus.yaml` - Navigation menu

## Deployment

The site is automatically deployed to GitHub Pages when changes are pushed to the `main` branch. GitHub Actions handles the build and deployment process.

## License

Content: © Bernardo Villegas Moreno. All rights reserved.

Website template: Licensed under Hugo Blox Builder's license terms.

## Contact

For questions or suggestions about this website, please contact me through the information provided on the [live site](https://bjv01.github.io/).
