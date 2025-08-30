# Project Structure

This Jekyll website has been reorganized for better maintainability and easier navigation.

## Directory Structure

```
my_home/
├── config/                    # Configuration files
│   ├── _config.yml            # Jekyll configuration
│   ├── Gemfile               # Ruby dependencies
│   ├── Gemfile.lock          # Locked dependency versions
│   └── staticman.yml         # Staticman configuration
├── content/                   # All content files
│   ├── pages/                 # Static pages
│   │   ├── aboutme.md
│   │   ├── blog.md
│   │   ├── curriculum.md
│   │   ├── publications.md
│   │   └── index.html
│   ├── posts/                 # Blog posts (formerly _posts/)
│   └── publications/          # Publication files (formerly _publications/)
├── docs/                      # Documentation and guides
│   ├── README.md
│   ├── BLOG_GUIDE.md
│   ├── CHANGELOG.md
│   ├── PROJECT_STRUCTURE.md   # This file
│   └── templates/
│       └── new-post-template.md
├── theme/                     # Theme and layout files
│   ├── _layouts/
│   ├── _includes/
│   ├── _data/
│   └── assets/
├── utility/                   # Utility and system files
│   ├── 404.html
│   ├── feed.xml
│   ├── robots.txt
│   ├── tags.html
│   └── .htaccess
└── [Root symlinks for Jekyll compatibility]
    ├── _config.yml -> config/_config.yml
    ├── _posts -> content/posts
    ├── _publications -> content/publications
    ├── _layouts -> theme/_layouts
    ├── _includes -> theme/_includes
    ├── _data -> theme/_data
    ├── assets -> theme/assets
    └── [page symlinks]
```

## Frequently Accessed Files

### Content Creation
- **New blog posts**: `content/posts/`
- **Page editing**: `content/pages/`
- **Publications**: `content/publications/`
- **Post template**: `docs/templates/new-post-template.md`

### Styling and Layout
- **CSS files**: `theme/assets/css/`
- **Images**: `theme/assets/img/`
- **Layouts**: `theme/_layouts/`
- **Includes**: `theme/_includes/`

### Configuration
- **Jekyll config**: `config/_config.yml`
- **Dependencies**: `config/Gemfile`

### Documentation
- **Project docs**: `docs/`
- **Blog writing guide**: `docs/BLOG_GUIDE.md`

## Workflow

### Adding a New Blog Post
1. Navigate to `content/posts/`
2. Copy template from `docs/templates/new-post-template.md`
3. Create new file with format: `YYYY-MM-DD-title.md`
4. Write content and commit

### Updating Styles
1. Navigate to `theme/assets/css/`
2. Edit `custom-modern.css` for custom styles
3. Test with `bundle exec jekyll serve`

### Adding Images
1. Add images to `theme/assets/img/`
2. Reference in content with `/assets/img/filename.ext`

## Benefits of This Structure

1. **Clear separation of concerns**: Content, theme, config, and docs are separated
2. **Easier navigation**: Related files are grouped together
3. **Better maintainability**: Changes are isolated to specific areas
4. **Cleaner root directory**: Less clutter in the main folder
5. **Preserved Jekyll compatibility**: Symlinks maintain Jekyll's expected structure

## Notes

- All symlinks in the root directory are necessary for Jekyll to function properly
- The `exclude` list in `_config.yml` prevents Jekyll from processing the organized directories
- When editing files, always work in the organized directories (not the symlinks)
