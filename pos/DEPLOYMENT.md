# Deployment Guide for MkDocs Documentation

## GitHub Pages Deployment

This documentation is configured to automatically deploy to GitHub Pages when changes are pushed to the `main` branch.

### Automatic Deployment

1. **Push to main branch**: The GitHub Actions workflow will automatically:
   - Install dependencies
   - Build the MkDocs site
   - Deploy to GitHub Pages

2. **Access the site**: After deployment (usually takes 1-2 minutes), the documentation will be available at:
   ```
   https://kd-agri-inc-suite.github.io/pos/
   ```

### Manual Deployment (if needed)

If you need to deploy manually:

1. Build the site locally:
   ```bash
   mkdocs build
   ```

2. Deploy using GitHub Actions:
   - Go to the "Actions" tab in your GitHub repository
   - Select "Deploy MkDocs to GitHub Pages"
   - Click "Run workflow"

### Setting Up GitHub Pages (First Time)

If this is the first time setting up GitHub Pages:

1. Go to your repository settings
2. Navigate to "Pages" in the left sidebar
3. Under "Source", select:
   - Source: `GitHub Actions`
   - (The workflow will handle the deployment)

### Local Testing

Before pushing changes, test locally:

```bash
# Install dependencies
pip install mkdocs-material
pip install mkdocs-git-revision-date-localized-plugin

# Serve locally
mkdocs serve

# Build to check for errors
mkdocs build
```

### Troubleshooting

**Issue: Site not updating**
- Check GitHub Actions workflow status
- Ensure the workflow completed successfully
- Wait a few minutes for GitHub Pages to update (can take up to 10 minutes)

**Issue: Build errors**
- Check the Actions tab for error messages
- Verify all dependencies are listed in the workflow
- Test locally with `mkdocs build` to catch errors early

**Issue: 404 on GitHub Pages**
- Verify the `site_url` in `mkdocs.yml` matches your repository structure
- Check that GitHub Pages is enabled in repository settings
- Ensure the workflow has write permissions

## Custom Domain (Optional)

If you want to use a custom domain:

1. Add a `CNAME` file in the `docs/` directory with your domain
2. Update the `site_url` in `mkdocs.yml` to match your domain
3. Configure DNS settings for your domain

