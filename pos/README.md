# POS & Inventory Management System Documentation

This repository contains the documentation for the POS and Inventory Management System for KD Agri Inc Suite.

## Documentation Site

The documentation is built using [MkDocs](https://www.mkdocs.org/) with the [Material theme](https://squidfunk.github.io/mkdocs-material/).

### Viewing the Documentation

The documentation is automatically deployed to GitHub Pages and can be accessed at:
**https://kd-agri-inc-suite.github.io/pos/**

### Local Development

To view the documentation locally:

1. Install MkDocs and required plugins:
```bash
pip install mkdocs-material
pip install mkdocs-git-revision-date-localized-plugin
```

2. Serve the documentation locally:
```bash
mkdocs serve
```

3. Open your browser to `http://127.0.0.1:8000`

### Building the Documentation

To build the static site:

```bash
mkdocs build
```

The built site will be in the `site/` directory.

## Project Structure

```
pos/
├── docs/
│   ├── index.md                    # Homepage
│   └── functional-requirements.md  # Complete functional requirements
├── .github/
│   └── workflows/
│       └── ci.yml                  # GitHub Actions workflow for deployment
├── mkdocs.yml                      # MkDocs configuration
└── README.md                       # This file
```

## Deployment

The documentation is automatically deployed to GitHub Pages when changes are pushed to the `main` branch via GitHub Actions.

## Contributing

To update the documentation:

1. Edit the markdown files in the `docs/` directory
2. Test locally using `mkdocs serve`
3. Commit and push changes to the `main` branch
4. GitHub Actions will automatically deploy the updated documentation

## Requirements

- Python 3.x
- MkDocs
- MkDocs Material theme
- mkdocs-git-revision-date-localized-plugin

