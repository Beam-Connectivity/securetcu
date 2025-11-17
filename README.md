# SecureTCU Project Site

This is the source for the Jekyll-based static website hosted at https://securetcu.io

**IMPORTANT**: This repository is PUBLIC and can be viewed by anyone on GitHub.

## About SecureTCU

SecureTCU is a research and development initiative creating a next-generation Telematics Control Unit (TCU) with integrated Intrusion Detection System (IDS) capabilities for automotive vehicles. The project aims to meet UNECE R155/R156 cybersecurity compliance requirements.

### Consortium Partners

- **Autocrypt** (South Korea) - IDS software stacks and SOTA security
- **Beam Connectivity** (UK) - CVaaS platform implementation
- **KATECH** (South Korea) - Verification and validation
- **Secure Elements** (UK) - Cybersecurity management and CRISKLE tool

## Technology Stack

- **Site Generator**: Jekyll (via GitHub Pages)
- **Theme**: jekyll-theme-slate (customized)
- **Ruby Version**: Compatible with github-pages gem ~> 219
- **Hosting**: GitHub Pages with automated deployment
- **Custom Domain**: securetcu.io

## Developing the Site

This site should be developed on your local machine and tested using the local Ruby webserver. It is easy once the pre-reqs are installed.

### Prerequisites

- **Ruby** (version 2.7+ recommended)
- **Bundler** gem
- **Git**

### Setup Ruby and Jekyll

Follow the steps at https://jekyllrb.com/docs/, which will:
1. Install Ruby via chruby (or your preferred Ruby version manager)
2. Install Jekyll via the gem
3. Install Bundler if not already installed: `gem install bundler`

### Initial Setup

Clone the repository and install dependencies:

```bash
git clone git@github.com:Beam-Connectivity/securetcu.git
cd securetcu
bundle install
```

### Running Locally

Once all pre-reqs are installed, start the development server:

```bash
bundle exec jekyll serve --livereload
```

Then browse to http://localhost:4000

The `--livereload` flag automatically refreshes your browser when you make changes to files.

### Alternative Development Commands

```bash
# Run without livereload
bundle exec jekyll serve

# Run on a different port
bundle exec jekyll serve --port 4001

# Build the site without serving
bundle exec jekyll build
```

## Deployment

This site uses GitHub Pages for automated deployment.

### Deployment Process

1. Create a new branch for your changes
2. Make your edits and test locally
3. Commit your changes with descriptive commit messages
4. Push your branch and open a Pull Request
5. Get approval from SecureTCU team members
6. Merge to `master` branch
7. GitHub Pages will automatically build and deploy to https://securetcu.io (usually within 1-2 minutes)

### Deployment Notes

- All commits to the `master` branch trigger automatic deployment
- GitHub Pages uses its own build environment (github-pages gem ~> 219)
- Build status can be viewed in the repository's Actions tab
- DNS is configured via the `CNAME` file (do not modify unless changing domain)

## Troubleshooting

#### "no acceptor (port is in use or requires root privileges)" [Windows Subsystem for Linux]

Sometimes you may get the following when starting serve: `Error:  no acceptor (port is in use or requires root privileges)`. This means that jekyll process is already running, using the port. Kill it with:

`ps aux | grep jekyll | awk '{print $2}' | xargs kill -9`


#### “The GitHub API credentials you provided aren’t valid.”

When trying to run jekyll serve you may see this error.

This can be due to having 2-factor authentication set up on github, or the credentials not stored otherwise. The easiest fix for this is to generate a unique Personal Access token through github’s website, and store that in the JEKYLL_GITHUB_TOKEN environment variable.

See this post: http://blog.johannesmp.com/2017/02/13/fixing-jekyll-serve-on-windows/

#### Gem Installation Issues

If you encounter issues with gem installation, try:

```bash
# Update bundler
gem install bundler

# Clean and reinstall
bundle clean --force
bundle install
```

## Project Structure

```
securetcu/
├── _config.yml          # Jekyll site configuration
├── _layouts/            # HTML templates
│   └── default.html     # Main layout template
├── assets/              # Static resources
│   ├── css/            # Custom SCSS styling
│   ├── images/         # Logos and graphics
│   └── downloads/      # Whitepapers and PDFs
├── index.md            # Homepage content (Markdown)
├── 404.html            # Custom 404 error page
├── Gemfile             # Ruby dependency specifications
├── Gemfile.lock        # Locked dependency versions
├── CNAME               # Custom domain configuration
├── favicon.png         # Site favicon
└── README.md           # This file
```

## Content Management

### Adding Images

1. Place images in `assets/images/`
2. Reference in markdown: `![Alt text](/assets/images/filename.png)`
3. For partner logos, use consistent naming and include both PNG and SVG formats if available

### Adding Downloads

1. Place files in `assets/downloads/`
2. Link in markdown: `[Link text](/assets/downloads/filename.pdf)`

### Editing Content

- **Homepage**: Edit `index.md`
- **Site Title & Metadata**: Edit `_config.yml`
- **Layout & Structure**: Edit `_layouts/default.html`
- **Styling**: Edit `assets/css/style.scss`

### Custom Styling

The site uses the Slate theme with custom overrides in `assets/css/style.scss`:
- Custom heading color: `#A93A33` (dark red)
- Responsive table styling
- Partner logo formatting

## Security Considerations

- This is a public repository - never commit sensitive data
- Do not include API keys, credentials, or private information
- Review all content before publishing to ensure it's appropriate for public viewing
- Whitepapers and downloadable content should be approved before adding

## Contact

For questions or access requests, contact: hello@securetcu.io

## Repository Information

- **GitHub**: https://github.com/Beam-Connectivity/securetcu
- **Live Site**: https://securetcu.io
- **Branch**: master
- **License**: Not specified

## Common Tasks

### Adding a News Article

1. Edit `index.md`
2. Add entry under the "News and Links" section
3. Include date, title, and link
4. Test locally before committing

### Updating Partner Information

1. Add/update logo in `assets/images/`
2. Edit `_layouts/default.html` to update footer partner section
3. Update `index.md` if changing partner descriptions

### Changing Site Configuration

Edit `_config.yml` for:
- Site title
- Navigation menu items
- Theme settings
- SEO metadata

## Additional Resources

- [Jekyll Documentation](https://jekyllrb.com/docs/)
- [GitHub Pages Documentation](https://docs.github.com/en/pages)
- [Slate Theme Documentation](https://github.com/pages-themes/slate)
- [Markdown Guide](https://www.markdownguide.org/)