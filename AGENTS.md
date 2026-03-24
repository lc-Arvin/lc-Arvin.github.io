# Agent Guidelines for lc-Arvin.github.io

This document provides guidelines for AI agents working on this repository. It includes build commands, development workflows, and code style conventions.

## Project Overview

This is a Jekyll-based static blog hosted on GitHub Pages. The site uses the Minima theme and contains technical blog posts primarily in Chinese with some English.

Key components:
- **Jekyll**: Static site generator (Ruby)
- **GitHub Pages**: Hosting platform
- **Markdown**: Content format for posts and pages
- **YAML**: Configuration and front matter

## Build Commands

### Prerequisites
- Ruby (version specified in Gemfile)
- Bundler gem installed (`gem install bundler`)

### Installation
```bash
bundle install
```
Installs all Ruby gem dependencies defined in `Gemfile`.

### Development Server
```bash
bundle exec jekyll serve
```
Starts a local development server at `http://localhost:4000`. The server auto-reloads when files change.

### Development with Correct Image Paths
For posts using `{{site.url}}` in image paths (recommended for GitHub Pages compatibility), use the development configuration:

```bash
bundle exec jekyll serve --config _config.yml,_config_dev.yml --host localhost --port 4000
```

This ensures `{{site.url}}` resolves to `http://localhost:4000` locally, matching the development server.

### Build Site
```bash
bundle exec jekyll build
```
Generates the static site in the `_site` directory (excluded from git).

### Clean Build Artifacts
```bash
bundle exec jekyll clean
```
Removes generated site and cache directories.

### Alternative: Serve with LiveReload
```bash
bundle exec jekyll serve --livereload
```
Enables LiveReload for automatic browser refreshing.

## Development Workflow

### Adding New Posts
1. Create a new Markdown file in `_posts/` with filename format: `YYYY-MM-DD-title.md`
2. Include front matter (optional but recommended) at the top:
   ```markdown
   ---
   layout: post
   title: "Your Title"
   date: YYYY-MM-DD HH:MM:SS +0800
   categories: [category1, category2]
   ---
   ```
3. Write content in Markdown
4. Commit and push to GitHub; GitHub Pages will automatically rebuild

### Adding Pages
1. Create a new Markdown or HTML file in root directory (e.g., `about.markdown`)
2. Include front matter specifying layout and permalink:
   ```markdown
   ---
   layout: page
   title: About
   permalink: /about/
   ---
   ```
3. Add content

### Testing Locally
Run `bundle exec jekyll serve` and open `http://localhost:4000` to verify changes before committing.

## Linting and Testing

This repository currently has no formal linting or testing setup. However, consider the following:

### Markdown Validation
- Ensure proper Markdown syntax
- Check for broken links
- Validate YAML front matter syntax

### Jekyll Health Check
```bash
bundle exec jekyll doctor
```
Checks for common configuration issues.

### Future Considerations
If adding JavaScript/CSS, consider:
- ESLint for JavaScript
- Stylelint for CSS
- Prettier for code formatting
- Adding a CI pipeline (GitHub Actions) for automated checks

## Code Style Guidelines

### Markdown
- Use standard Markdown syntax (CommonMark)
- Headers: Use `#` for H1, `##` for H2, etc.
- Code blocks: Use triple backticks with language specifier when appropriate
- Lists: Use hyphen `-` for unordered lists, numbers for ordered lists
- Links: `[text](url)` format
- Images: `![alt text](path/to/image)`
- Line length: Keep lines under 100 characters where possible for readability

### YAML
- Use two-space indentation (no tabs)
- Strings without special characters don't need quotes
- Multiline strings: Use `|-` for literal blocks or `>` for folded style
- Collections: Use hyphen `-` for list items

### Front Matter
- Place at the top of Markdown files between `---` delimiters
- Required keys for pages: `layout`, `title`, `permalink`
- Optional keys for posts: `date`, `categories`, `tags`
- Date format: `YYYY-MM-DD HH:MM:SS +ZZZZ` (timezone offset)

### Naming Conventions
- **Files**: Lowercase with hyphens (kebab-case)
- **Posts**: `YYYY-MM-DD-descriptive-title.md`
- **Images**: Place in `images/` directory, use descriptive names
- **Directories**: Lowercase with hyphens

### Language and Content
- Primary language: Chinese (Simplified)
- Secondary language: English for code snippets and technical terms
- Mix languages naturally based on context
- Use proper punctuation for both languages

### Ruby/Jekyll
- Follow Ruby community style guide (2-space indentation)
- Gemfile: List gems in alphabetical groups
- `_config.yml`: Keep configuration organized with comments

### Git Practices
- Commit messages: Use present tense, imperative mood ("Add post about X", "Fix typo in about page")
- Branch naming: `feature/short-description` or `fix/issue-description`
- Keep commits focused and atomic

## Cursor/Copilot Rules

No repository-specific Cursor rules (`.cursor/rules/`) or Copilot instructions (`.github/copilot-instructions.md`) were found. When creating new rules:

### Suggested Cursor Rules
1. **Language Preference**: Prefer Chinese for documentation and blog content, English for code and technical terms
2. **Front Matter**: Ensure new posts include appropriate front matter
3. **Image Handling**: Place images in `images/` directory and reference with relative paths
4. **Date Format**: Use `YYYY-MM-DD` for post filenames and front matter dates

### Copilot Suggestions
- Use consistent Markdown formatting
- Include alt text for images
- Add comments to complex code snippets

## Common Tasks for Agents

### Adding a New Blog Post
1. Create file in `_posts/` with proper date prefix
2. Add front matter with title and date
3. Write content in Markdown
4. Add relevant images to `images/` and reference them
5. Test locally with `bundle exec jekyll serve`
6. Commit with descriptive message

### Updating Site Configuration
1. Edit `_config.yml`
2. Restart Jekyll server to see changes (config changes require server restart)
3. Test that site still builds correctly

### Fixing Broken Links
1. Use `bundle exec jekyll build` to generate site
2. Check `_site` directory for missing resources
3. Update links to use correct paths (relative to root)

### Adding Features
- New layouts: Create in `_layouts/` directory
- Includes: Create in `_includes/` directory
- Sass/CSS: Add to `_sass/` directory (Minima theme overrides)
- JavaScript: Add to `assets/js/` directory

## Troubleshooting

### Jekyll Server Issues
- **Port in use**: Use `bundle exec jekyll serve --port 4001`
- **Missing dependencies**: Run `bundle install`
- **Configuration errors**: Check `_config.yml` syntax with online YAML validator

### Build Failures
- **Front matter errors**: Ensure proper YAML syntax between `---` delimiters
- **Missing files**: Verify all referenced files exist
- **Permission issues**: Check file permissions in `_site` directory

### GitHub Pages Deployment
- The site auto-deploys on push to main branch
- Check GitHub Actions tab for build logs
- Allow up to 10 minutes for changes to propagate

## Additional Resources

- [Jekyll Documentation](https://jekyllrb.com/docs/)
- [GitHub Pages Documentation](https://docs.github.com/en/pages)
- [Markdown Guide](https://www.markdownguide.org/)
- [Minima Theme](https://github.com/jekyll/minima)

---

*This document is maintained for AI agents working on this repository. Update as the project evolves.*