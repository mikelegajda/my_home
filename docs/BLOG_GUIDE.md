# 📝 Blog Management Guide

This guide explains how to easily add new blog articles to your Jekyll website.

## 📁 File Structure

```
_posts/
├── 2025-01-15-welcome-to-my-blog.md
├── 2025-01-10-linear-programming-guide.md
└── [your-new-posts].md
```

## ✍️ Creating a New Blog Post

### 1. File Naming Convention

Create a new file in the `_posts/` directory with the format:
```
YYYY-MM-DD-title-with-hyphens.md
```

**Examples:**
- `2025-01-20-optimization-algorithms.md`
- `2025-02-01-conference-experience.md`
- `2025-02-15-python-tips-for-researchers.md`

### 2. Front Matter Template

Every blog post must start with YAML front matter. Copy and customize this template:

```yaml
---
layout: post
title: "Your Article Title"
subtitle: "A compelling subtitle that describes your post"
date: 2025-01-20 10:00:00 +0100
author: "Mikele Gajda"
cover-img: "/assets/img/your-image.jpg"  # Optional: Large header image
thumbnail-img: "/assets/img/thumb.jpg"   # Optional: Small preview image
tags: [tag1, tag2, tag3, research]       # Tags for categorization
readtime: 7                              # Estimated reading time in minutes
description: "SEO-friendly description of your post content for search engines and social media previews."
---
```

### 3. Content Structure

After the front matter, write your content using Markdown:

```markdown
# Your content starts here

## Introduction

Write your engaging introduction here...

## Main Section

### Subsection

Your content with **bold text**, *italic text*, and [links](https://example.com).

## Code Examples

```python
def hello_world():
    print("Hello, World!")
```

## Mathematical Formulas

You can include math using LaTeX syntax:
- Inline: $E = mc^2$
- Block: $$\sum_{i=1}^{n} x_i = total$$

## Images

![Alt text](/assets/img/your-image.jpg)

## Lists

1. First item
2. Second item
3. Third item

- Bullet point
- Another point

## Conclusion

Wrap up your article...

---

*Call to action or closing note*
```

## 🖼️ Adding Images

### 1. Image Location
Place images in `/assets/img/` directory.

### 2. Image Types
- **Cover Image**: Large header image for the post (recommended: 1200x600px)
- **Thumbnail**: Small preview image for blog cards (recommended: 400x300px)
- **Content Images**: Images within the article content

### 3. Image Syntax
```markdown
![Description of image](/assets/img/filename.jpg)
```

## 🔧 Advanced Features

### Code Syntax Highlighting

Supported languages include:
```python
# Python code
def function():
    return True
```

```javascript
// JavaScript code
function example() {
    return true;
}
```

```bash
# Bash commands
git commit -m "Update blog post"
```

### Blockquotes

```markdown
> This is a blockquote for emphasizing important information
> or including quotes from other sources.
```

### Tables

```markdown
| Column 1 | Column 2 | Column 3 |
|----------|----------|----------|
| Data 1   | Data 2   | Data 3   |
| Data 4   | Data 5   | Data 6   |
```

### Call-out Boxes

```markdown
> **💡 Pro Tip:** Use blockquotes with emojis to create attention-grabbing callout boxes!

> **⚠️ Warning:** Important information that readers should pay attention to.

> **📚 Further Reading:** Links to additional resources.
```

## 🏷️ Tag Guidelines

Use descriptive, consistent tags:

**Research Topics:**
- `operations-research`
- `optimization`
- `linear-programming`
- `machine-learning`
- `sustainability`

**Content Types:**
- `tutorial`
- `case-study`
- `conference`
- `book-review`
- `tools`

**Academic:**
- `phd-life`
- `research-tips`
- `academia`
- `publication`

## 📅 Publishing Workflow

1. **Create** your markdown file in `_posts/`
2. **Write** your content using the template above
3. **Add images** to `/assets/img/` if needed
4. **Test locally**: Run `bundle exec jekyll serve` to preview
5. **Commit** your changes: `git add . && git commit -m "Add new blog post"`
6. **Push** to GitHub: `git push origin main`
7. **Deploy**: GitHub Pages will automatically build and deploy

## 📱 Responsive Design

Your blog posts will automatically be:
- Mobile-friendly
- Optimized for readability
- SEO-friendly
- Social media ready

## 💡 Content Ideas

**Research & Academic:**
- Algorithm explanations with code
- Conference experiences and insights
- Paper summaries and reviews
- Research methodology tips
- PhD journey stories

**Technical Tutorials:**
- Programming tutorials
- Tool reviews and comparisons
- Data analysis walkthroughs
- Visualization techniques

**Industry Applications:**
- Case studies from real projects
- Industry trends and insights
- Career advice for researchers
- Networking and collaboration tips

## 🔍 SEO Best Practices

1. **Use descriptive titles** (50-60 characters)
2. **Write compelling meta descriptions** (150-160 characters)
3. **Include relevant keywords** naturally in content
4. **Use proper heading structure** (H1, H2, H3)
5. **Add alt text** to all images
6. **Internal linking** to other posts/pages
7. **Include social sharing** buttons (automatically added)

## 🚀 Quick Start Checklist

- [ ] Choose a compelling title
- [ ] Write front matter with all required fields
- [ ] Structure content with clear headings
- [ ] Add relevant images with alt text
- [ ] Include code examples if applicable
- [ ] Add appropriate tags
- [ ] Test locally before publishing
- [ ] Check mobile responsiveness
- [ ] Verify all links work

---

Happy blogging! 🎉 If you have questions about any of these features, feel free to reach out.
