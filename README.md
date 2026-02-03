# wyzurd-hugo

Personal portfolio website for Chris Hackett, a Portland-based Post Specialist and Local 600 Digital Imaging Technician.

## Tech Stack

- **Static Site Generator**: [Hugo](https://gohugo.io/)
- **Theme**: [PaperMod](https://github.com/adityatelange/hugo-PaperMod)
- **Additional Theme**: hugo-shortcode-gallery

## Local Development

### Prerequisites

- [Hugo Extended](https://gohugo.io/installation/) (v0.110.0 or later recommended)

### Running Locally

```bash
# Clone the repository
git clone https://github.com/fenixstarlord/wyzurd-hugo.git
cd wyzurd-hugo

# Start the development server
hugo server -D
```

The site will be available at `http://localhost:1313/`

### Building for Production

```bash
hugo --minify
```

Output will be in the `public/` directory.

## Project Structure

```
wyzurd-hugo/
├── content/
│   ├── home/           # Home page content
│   ├── about/          # About page
│   ├── blog/           # Blog posts
│   ├── resume/         # Resume page
│   └── services/       # Service pages (DIT, Color, etc.)
├── layouts/
│   ├── partials/       # Custom partial templates
│   └── shortcodes/     # Custom shortcodes
├── static/
│   └── profile/        # Profile images
└── hugo.yaml           # Site configuration
```

## Features

- Responsive design
- Dark/light mode support
- Vanta.js animated background on home page
- Custom image gallery shortcode

## Configuration

Site configuration is in `hugo.yaml`. Key settings include:

- **profileMode**: Home page profile display settings
- **socialIcons**: Social media links
- **menus**: Navigation menu items

## License

All rights reserved.
