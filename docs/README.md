# Mikele Gajda's Personal Website

A Jekyll-based personal website featuring blog posts, publications, and professional information. Built with the Beautiful Jekyll theme.

## 🚀 Quick Start

### Prerequisites

Make sure you have the following installed:
- Ruby (version 2.7 or higher)
- Bundler gem
- Git

### Installation & Setup

1. **Clone the repository**
   ```bash
   git clone https://github.com/mikelegajda/my_home.git
   cd my_home
   ```

2. **Install dependencies**
   ```bash
   bundle install
   ```

3. **Run the site locally**
   ```bash
   bundle exec jekyll serve
   ```

4. **Open your browser**
   Navigate to `http://localhost:4000` to view the site

### Alternative: Run with live reload
```bash
bundle exec jekyll serve --livereload
```
This will automatically refresh your browser when you make changes to files.

## 📁 Project Structure

```
├── _config.yml          # Site configuration
├── _posts/              # Blog posts
├── _publications/       # Research publications
├── _layouts/            # HTML templates
├── _includes/           # Reusable HTML components
├── assets/              # CSS, JS, images
│   ├── css/
│   ├── js/
│   └── img/
├── aboutme.md           # About page
├── blog.md              # Blog listing page
├── curriculum.md        # CV page
└── publications.md      # Publications page
```

## ✏️ Content Management

### Adding a New Blog Post

1. Create a new file in `_posts/` with the format: `YYYY-MM-DD-title.md`
2. Use this template:
   ```markdown
   ---
   layout: post
   title: "Your Post Title"
   subtitle: "Optional subtitle"
   date: YYYY-MM-DD
   tags: [tag1, tag2]
   ---
   
   Your content here...
   ```

### Adding a New Publication

1. Create a new file in `_publications/` with a descriptive name
2. Use this template:
   ```markdown
   ---
   title: "Paper Title"
   authors: "Author names"
   venue: "Conference/Journal name"
   year: 2025
   pdf_url: "link-to-pdf"
   ---
   
   Abstract or description...
   ```

### Updating Site Configuration

Edit `_config.yml` to modify:
- Site title and description
- Navigation menu items
- Social media links
- Color scheme
- Analytics settings

## 🎨 Customization

### Colors and Styling
- Main styles: `assets/css/custom-modern.css`
- Theme colors are defined in `_config.yml` under the color section

### Adding Custom CSS
1. Add your CSS to `assets/css/custom.css`
2. Reference it in `_config.yml` under `site-css`

### Adding Custom JavaScript
1. Add your JS to `assets/js/`
2. Reference it in `_config.yml` under `site-js`

## 🔧 Development Commands

| Command | Description |
|---------|-------------|
| `bundle exec jekyll serve` | Start development server |
| `bundle exec jekyll serve --livereload` | Start with auto-refresh |
| `bundle exec jekyll build` | Build site for production |
| `bundle exec jekyll clean` | Clean generated files |
| `bundle update` | Update gem dependencies |

## 📦 Deployment

### GitHub Pages (Recommended)
1. Push your changes to the `main` branch
2. Enable GitHub Pages in repository settings
3. Site will be available at `https://mikelegajda.github.io/my_home`

### Custom Domain
1. Add your domain to `CNAME` file
2. Configure DNS settings with your domain provider
3. Update `url` in `_config.yml`

## 🐛 Troubleshooting

### Common Issues

**Port already in use:**
```bash
bundle exec jekyll serve --port 4001
```

**Gem installation issues:**
```bash
bundle install --path vendor/bundle
```

**Permission errors on macOS:**
```bash
sudo bundle install
```

**Clear cache and rebuild:**
```bash
bundle exec jekyll clean
bundle exec jekyll build
```

## 📝 License

This project uses the Beautiful Jekyll theme. See `LICENSE` for details.

---

For more information about Jekyll, visit [jekyllrb.com](https://jekyllrb.com/)