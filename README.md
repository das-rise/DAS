# Dependable Autonomous Systems - Research Team Website

A research team website built with [Zola](https://www.getzola.org/) using the [Peritus](https://github.com/jskaza/peritus) theme.

## Quick Start

```bash
# Navigate to site directory
cd DAS

# Start development server
zola serve

# The site will be available at http://127.0.0.1:1111

# Build for production
zola build
```

## Project Structure

```
DAS/
├── config.toml           # Main site configuration
├── content/              # Content pages
│   ├── _index.md         # Homepage (team description)
│   ├── team/            # Team member pages (one directory per member)
│   │   ├── _index.md
│   │   └── <member-slug>/
│   │       ├── index.md
│   │       └── photo.jpg (optional profile photo)
│   ├── projects/         # Project pages (one file per project)
│   ├── software/         # Software page
│   └── publications/     # Publications section
├── data/                 # Data files (TOML format)
│   └── software.toml     # Software tools configuration
├── templates/            # Custom templates
│   ├── base.html         # Base template
│   ├── index.html        # Homepage template
│   ├── projects.html      # Projects page (ongoing/completed)
│   ├── team.html         # Team listing page
│   ├── page.html         # Individual page template (team members, projects)
│   └── software.html      # Software page template
├── static/               # Static assets
└── themes/peritus/       # Theme files
```

## Content Pages

### Homepage
- Team overview and mission statement
- Links to Team, Projects, and Software pages
- ResearchGate and Google Scholar links

### Team Pages (`content/team/`)
Each team member has their own page with:
- Name, position, and email
- Research bio
- Social links: Google Scholar, LinkedIn, ORCID
- List of projects they're involved in
- Profile photo (optional)

**Team Members:** 13
1. Åsa Ollson
2. Anders Thorsén
3. Aria Mirzai
4. Bastian Havers-zulka
5. Behrooz Sangchoolie
6. Fredrik Warg
7. Mateen Malik
8. Mazen Mohamad
9. Martin Skoglund
10. Ramana Avula
11. Peter Folkesson
12. Pierre Kleberger
13. Karl Lundgren

### Projects Page (`content/projects/`)

Projects are divided into two sections:
- **Ongoing Projects:** Active projects (without `year_end` field)
- **Completed Projects:** Past projects (with `year_end` field)

Each project includes:
- Title and description
- Year range (start - end or start - Present)
- External links: Website, Source code, Video
- People involved (array of team member slugs)

**Projects:** 14
- Ongoing: Synergies, Headstart, Lashfire, Recap, Precise, HIVEMIND, ScenarioDB, Agrarsense, WayWiseR, Drones, Cyrec, Cyrev
- Completed: Valu3s

### Software Page (`data/software.toml` + `templates/software.html`)

Software tools developed by the team displayed as a list with:
- Software name and description
- Links to Website, Source code (GitHub), and Documentation

**Software Tools:** 12
- Synergies Framework
- Valu3s Toolkit
- SUNRISE Platform
- HIVEMIND Interface
- Precise Control Library
- Agrarsense Sensor Suite
- ScenarioDB Explorer
- WayWiseR Navigation
- Drones Control System
- CyRec Security Module
- CyRev Resilience Framework

## Editing Content

### Adding a Team Member

Create a directory `content/team/<member-slug>/` and an `index.md` file inside:

```markdown
+++
title = "Full Name"

[extra]
title = "Research Position"
email = "firstname.lastname@ri.se"
image = "photo.jpg" # Or external URL like "https://..."
google_scholar = "https://scholar.google.com/..."
linkedin = "https://linkedin.com/in/..."
orcid = "https://orcid.org/..."
+++

Research bio and interests go here.
```

To add a profile photo, place the image file (e.g., `photo.jpg`) inside the member's directory (`content/team/<member-slug>/photo.jpg`) and set `image = "photo.jpg"` in `index.md`. External URLs (`https://...`) are also supported.

### Adding a Project

Create a new file in `content/projects/`:

```markdown
+++
title = "Project Name"

[extra]
year_start = 2024
year_end = ""  # Leave empty for ongoing projects
description = "Brief project description."
url = "https://project-website.com/"
code = "https://github.com/username/repo"
video = "https://youtube.com/watch?v=..."
people = ["member-slug-1", "member-slug-2"]  # Team members involved
+++

Detailed project description goes here.
```

### Adding Software

Add to `data/software.toml`:

```toml
[[software]]
name = "Software Name"
description = "Brief description of the software."
website = "https://software-website.com/"
github = "https://github.com/username/repo"
documentation = "https://github.com/username/docs"
```

## Site Configuration

Edit `config.toml` to customize:

```toml
# Site Information
base_url = "https://ashfaqfarooqui.me"
title = "Dependable Autonomous Systems"
description = "Research team focusing on verification, validation, and supervisory control of automated systems"

[extra]
# Team Info
name = "Dependable Autonomous Systems"
role = "Research Unit"
organization = "Research Institute of Sweden"
location = "Gothenburg, Sweden"

# Social Links
researchgate_url = "https://www.researchgate.net/lab/Dependable-Autonomous-Systems"
google_scholar_url = ""

# Bio
bio = """
The Dependable Autonomous Systems research unit at the Research Institute of Sweden focuses on model-driven development, supervisory control, and formal analysis. We develop tools and techniques to support verifiably safe control of automated systems.
"""

# Navigation Menu
[[extra.menu]]
name = "Team"
url = "/team/"
weight = 1

[[extra.menu]]
name = "Projects"
url = "/projects/"
weight = 2

[[extra.menu]]
name = "Software"
url = "/software/"
weight = 3
```

## Customization

### Colors

Edit `[extra.colors]` in `config.toml`:

```toml
[extra.colors]
# Light mode (default)
primary_color = "#003660"
secondary_color = "#FEBC11"
accent_color = "#09847A"
text_color = "#2C2F33"
background_color = "#F8F9FA"
card_background = "#FFFFFF"
border_color = "#D0D3D4"

# Dark mode (toggled)
dark_primary_color = "#4A9EFF"
dark_secondary_color = "#FEBC11"
dark_accent_color = "#2DD4BF"
dark_text_color = "#E4E4E7"
dark_background_color = "#0F0F0F"
dark_card_background = "#1A1A1A"
dark_border_color = "#2A2A2A"
```

## Deployment

### Manual Deployment

```bash
# Build the site
zola build

# The public/ folder contains the static HTML/CSS/JS
# Deploy to your web server or hosting service
```

### GitHub Pages

1. Create a new repository on GitHub
2. Push the `public/` directory to your repository
3. Enable GitHub Pages in repository settings

## Features

- Responsive design with dark mode support
- Team member pages with social links and project listings
- Projects divided into ongoing and completed sections
- Software tools showcase with documentation links
- Individual project pages with full descriptions and team member links
- Clean navigation menu with configurable sections

## Theme Customization

The Peritus theme provides:
- Clean, minimal design
- FontAwesome icons (v6.5.1)
- Academicons for academic links
- Custom color scheme support
- Dark mode toggle

## Troubleshooting

### "Template not found" error
- Ensure theme is properly installed in `themes/peritus/`
- Check template files exist in `themes/peritus/templates/`

### Changes not appearing
- Run `zola build` after editing content
- Clear browser cache if needed
- Check TOML syntax in data files (must use `"""` for multi-line strings)

### Images not loading
- Verify file paths in markdown frontmatter
- Ensure images exist in `static/img/` or are properly hosted
- Use absolute URLs for external images

## License

Theme: MIT License (Peritus by Jonathan Skaza)
Content: All Rights Reserved
