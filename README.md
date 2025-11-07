# Bernardo Villegas Moreno - Personal Academic Website

This repository contains the source code for my personal academic website, hosted at [bjv01.github.io](https://bjv01.github.io/).

## About

This website showcases my academic profile, research, and professional experience as a PhD student in Human-Inspired AI at the University of Cambridge. The site features:

- Professional biography and research focus
- Publications and academic work
- Education and experience timeline
- Skills, awards, and languages
- Custom warm earthy color palette

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
│   ├── _index.md    # Homepage
│   ├── authors/     # Author profiles
│   └── publications/ # Publications
├── config/          # Hugo configuration
│   └── _default/    # Default configuration files
├── static/          # Static files (images, etc.)
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

### Color Palette

The site uses a custom warm earthy color palette defined in `assets/css/custom.css`. The primary color is set to orange in `config/_default/params.yaml`.

### Content

- **Homepage**: Edit `content/_index.md` to modify sections
- **Biography**: Update `content/authors/admin/_index.md`
- **Publications**: Add new publications in `content/publications/`
- **Menu**: Modify navigation in `config/_default/menus.yaml`

### Site Configuration

Main configuration files:
- `config/_default/hugo.yaml` - General Hugo settings
- `config/_default/params.yaml` - Theme parameters and SEO
- `config/_default/menus.yaml` - Navigation menu

## Deployment

The site is automatically deployed to GitHub Pages when changes are pushed to the `main` branch. GitHub Actions handles the build and deployment process.

## License

Content: © Bernardo Villegas Moreno. All rights reserved.

Website template: Licensed under Hugo Blox Builder's license terms.

## Contact

For questions or suggestions about this website, please contact me through the information provided on the [live site](https://bjv01.github.io/).
