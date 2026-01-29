# Personal Academic Website

A clean, responsive Jekyll-based academic website built with the al-folio theme.

## Quick Start

### Local Development

1. **Install dependencies:**
   ```bash
   bundle install
   ```

2. **Run the site locally:**
   ```bash
   bundle exec jekyll serve
   ```

3. **View your site:**
   Open your browser to `http://localhost:4000`

### Making Changes

After making changes, the site will automatically rebuild. Refresh your browser to see updates.

## Site Structure & Customization Guide

### Essential Files Overview

```
├── _config.yml              # Main site configuration
├── _data/                   # Data files for CV, social links, etc.
├── _pages/                  # Main pages (about, CV, publications, etc.)
├── _posts/                  # Blog posts
├── _projects/               # Project showcase entries
├── _news/                   # News/announcements
├── _books/                  # Book reviews
├── _teachings/              # Course listings
├── _bibliography/           # Publications (BibTeX)
├── _includes/               # Reusable template components
├── _layouts/                # Page layout templates
├── _sass/                   # Stylesheets (SCSS)
├── _scripts/                # JavaScript files
├── assets/                  # Images, PDFs, and other static files
├── Gemfile                  # Ruby dependencies
└── robots.txt              # Search engine directives
```

## Customization Guide

### 1. Basic Site Information

Edit `_config.yml` to customize:

```yaml
title: Your Site Title
first_name: Your
middle_name: Middle
last_name: Name
email: your.email@example.com
description: >
  Your site description here
url: https://yourusername.github.io  # Your GitHub Pages URL
baseurl: /your-repo-name              # Leave blank for user site
```

**Important:** For a personal GitHub Pages site (username.github.io), leave `baseurl` empty. For a project site, set it to `/repo-name`.

### 2. Navigation Bar

The navigation bar is configured in `_config.yml` under the `pages` section:

```yaml
pages:
  - name: about
    permalink: /
  - name: blog
    permalink: /blog/
  - name: projects
    permalink: /projects/
  - name: publications
    permalink: /publications/
  - name: cv
    permalink: /cv/
```

**To add/remove pages:**
- Add or remove entries in this list
- Create corresponding markdown files in `_pages/` directory
- Set the `permalink` to match the navigation entry

**Dropdown menus:**
See the `dropdown.md` example in `_pages/` for creating multi-level navigation.

### 3. Social Media Links

Edit `_data/socials.yml` to add/remove social media links:

```yaml
email: your.email@example.com
github_username: yourusername
twitter_username: yourusername
linkedin_username: yourname
orcid_id: 0000-0000-0000-0000
scholar_userid: yourscholarid
```

Available options include email, GitHub, Twitter, LinkedIn, ORCID, Google Scholar, and many more. See the file for all available options.

### 4. Profile Picture & Images

**Profile picture:**
- Place your image in `assets/img/`
- Update `_config.yml`:
  ```yaml
  profile:
    image: prof_pic.jpg  # Filename in assets/img/
    image_circular: false  # Crops to circle if true
  ```

**Other images:**
- Store in `assets/img/`
- Reference in markdown: `![Description](/assets/img/your-image.jpg)`
- Or use the figure include: `{% include figure.liquid path="assets/img/your-image.jpg" %}`

**Publication preview images:**
- Store in `assets/img/publication_preview/`

**Project images:**
- Store in `assets/img/`
- Reference in project frontmatter: `img: /assets/img/project-image.jpg`

### 5. Adding Pages

**Create a new page:**

1. Create a new file in `_pages/` (e.g., `mypage.md`)
2. Add frontmatter:
   ```yaml
   ---
   layout: page
   title: My Page
   permalink: /mypage/
   description: Optional description
   ---
   ```
3. Add your content in Markdown
4. Add to navigation in `_config.yml` (see Navigation Bar section)

**Page layouts available:**
- `page` - Standard page
- `post` - Blog post
- `distill` - Distill-style article
- `about` - Homepage/about page
- `cv` - CV page
- `bib` - Bibliography page

### 6. Blog Posts

**Create a new post:**

1. Create a file in `_posts/` with format: `YYYY-MM-DD-title.md`
   - Example: `2024-01-15-my-first-post.md`

2. Add frontmatter:
   ```yaml
   ---
   layout: post
   title: My Blog Post Title
   date: 2024-01-15
   description: Brief description
   categories: research
   tags: jekyll academia
   ---
   ```

3. Write your content in Markdown

**Features in posts:**
- Math equations: Use `$inline$` or `$$display$$`
- Code blocks: Use triple backticks with language
- Images: Use the figure include for responsive images
- Citations: Reference your BibTeX entries

See `_posts/2015-03-15-formatting-and-links.md` for examples.

### 7. Projects

**Add a project:**

1. Create a file in `_projects/` (e.g., `my-project.md`)
2. Add frontmatter:
   ```yaml
   ---
   layout: page
   title: Project Name
   description: Brief project description
   img: /assets/img/project-thumbnail.jpg
   importance: 1  # Lower numbers appear first
   category: work  # or 'fun'
   ---
   ```
3. Add project details in Markdown

Projects are automatically displayed on the `/projects/` page, sorted by importance.

### 8. Publications (Bibliography)

**Add publications:**

Edit `_bibliography/papers.bib` in BibTeX format:

```bibtex
@article{einstein1905,
  title={On the electrodynamics of moving bodies},
  author={Einstein, Albert},
  journal={Annalen der physik},
  volume={17},
  pages={891--921},
  year={1905},
  publisher={Wiley Online Library},
  
  # Optional al-folio specific fields:
  pdf={einstein1905.pdf},           # Place PDF in assets/pdf/
  preview={einstein1905.jpg},        # Preview image
  selected={true},                   # Show on homepage
  abstract={Your abstract here}
}
```

**Display options:**
- Publications automatically appear on `/publications/` page
- Selected publications (with `selected={true}`) appear on homepage
- Place PDF files in `assets/pdf/`

### 9. CV

**Edit your CV:**

The CV is configured in `_data/cv.yml` using the RenderCV format.

Structure:
```yaml
cv:
  name: Your Name
  label: Your Title
  email: your@email.com
  sections:
    education:
      - institution: University Name
        degree: PhD in Field
        start_date: 2020
        end_date: 2024
    experience:
      - company: Company Name
        position: Your Position
        start_date: 2024
        end_date: present
```

The CV is displayed on the `/cv/` page.

### 10. News & Announcements

**Add news items:**

1. Create a file in `_news/` (e.g., `announcement_2.md`)
2. Add frontmatter:
   ```yaml
   ---
   layout: post
   date: 2024-01-15
   inline: true  # Short announcement (one line)
   ---
   ```
3. Add your announcement text

News items appear on the homepage in reverse chronological order.

### 11. Teaching/Courses

**Add a course:**

1. Create a file in `_teachings/` (e.g., `machine-learning.md`)
2. Add frontmatter:
   ```yaml
   ---
   layout: page
   title: Course Title
   description: Course description
   img: /assets/img/course-image.jpg
   importance: 1
   category: current  # or 'past'
   ---
   ```
3. Add course details

Courses appear on the `/teaching/` page.

### 12. Book Reviews

**Add a book review:**

1. Create a file in `_books/` (e.g., `book-title.md`)
2. Add frontmatter:
   ```yaml
   ---
   layout: book-review
   title: Book Title
   author: Author Name
   year: 2024
   rating: 9/10
   img: /assets/img/book-cover.jpg
   ---
   ```
3. Write your review

## Styling & Theme

### Colors & Appearance

Edit `_sass/_variables.scss` to customize:
- Color scheme
- Font sizes
- Spacing
- Dark mode colors

### Dark Mode

Dark mode is automatically enabled. Users can toggle between light and dark themes.

## Advanced Features

### Mathematical Equations

Use MathJax/KaTeX for equations:
- Inline: `$E = mc^2$`
- Display: `$$\int_0^1 f(x) dx$$`

### Code Highlighting

Use fenced code blocks with language specification:

````markdown
```python
def hello_world():
    print("Hello, world!")
```
````

### Citations

Reference bibliography entries in posts:
```liquid
{% cite einstein1905 %}
```

### Includes

Use reusable components:
```liquid
{% include figure.liquid path="assets/img/image.jpg" %}
{% include video.liquid path="assets/video/video.mp4" %}
{% include audio.liquid path="assets/audio/audio.mp3" %}
```

## Configuration Files

### Essential Configuration

- **_config.yml** - Main site configuration (title, URL, navigation, features)
- **Gemfile** - Ruby dependencies for Jekyll
- **package.json** - Node.js dependencies (for Prettier formatting)
- **robots.txt** - Search engine crawling rules

### Formatting

This site uses Prettier for consistent formatting:
```bash
npx prettier --write .
```

## Building for Production

### GitHub Pages Deployment

Push to your repository, and GitHub Pages will automatically build and deploy your site.

### Local Production Build

```bash
JEKYLL_ENV=production bundle exec jekyll build
```

Output will be in `_site/` directory.

## Troubleshooting

### Site not building?
1. Check `_config.yml` syntax (YAML is whitespace-sensitive)
2. Run `bundle exec jekyll build` to see detailed error messages
3. Ensure all required frontmatter fields are present in content files

### Images not loading?
- Verify file paths start with `/assets/`
- Check that image files exist in the correct location
- Clear browser cache

### Navigation not working?
- Verify `permalink` in `_config.yml` matches page files
- Check that page files in `_pages/` have matching permalinks

### Styling issues?
- Clear browser cache
- Check that `url` and `baseurl` are correct in `_config.yml`

## Resources

- [Jekyll Documentation](https://jekyllrb.com/docs/)
- [Liquid Template Documentation](https://shopify.github.io/liquid/)
- [Markdown Guide](https://www.markdownguide.org/)
- [al-folio Theme](https://github.com/alshedivat/al-folio)

## License

This template is available under the MIT License. See LICENSE file for details.
