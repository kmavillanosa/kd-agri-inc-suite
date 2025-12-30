# Setting Up GitHub Pages for Documentation

## Step 1: Enable GitHub Pages

1. Go to your repository on GitHub
2. Click on **Settings** (top menu)
3. Scroll down to **Pages** in the left sidebar
4. Under **Source**, select:
   - **Source**: `GitHub Actions`
5. Click **Save**

## Step 2: Verify Workflow File Location

The workflow file should be at:
```
.github/workflows/deploy-docs.yml
```

**Important**: GitHub Actions only recognizes workflows in `.github/workflows/` at the **root** of your repository, not in subdirectories.

## Step 3: Check Your Branch Name

The workflow is configured to trigger on:
- `main` branch
- `master` branch

If your default branch has a different name, you can:
1. Update the workflow file to include your branch name, OR
2. Rename your branch to `main` or `master`

## Step 4: Trigger the Workflow

After setting up GitHub Pages:

1. **Option A**: Push any change to the `pos/` directory
   ```bash
   git add .
   git commit -m "Trigger documentation deployment"
   git push
   ```

2. **Option B**: Manually trigger via GitHub UI
   - Go to **Actions** tab
   - Select **Deploy MkDocs to GitHub Pages**
   - Click **Run workflow**

## Step 5: Verify Deployment

1. Wait 1-2 minutes for the workflow to complete
2. Check the **Actions** tab to see if the workflow ran successfully
3. Go to **Settings → Pages** to see the deployment status
4. Your documentation will be available at:
   ```
   https://kd-agri-inc-suite.github.io/kd-agri-inc-suite/
   ```

## Troubleshooting

### Workflow Not Appearing

- Ensure the workflow file is at `.github/workflows/deploy-docs.yml` (root level)
- Check that the file has a `.yml` extension (not `.yaml`)
- Verify the YAML syntax is correct

### Workflow Not Triggering

- Check that you're pushing to the `main` or `master` branch
- Verify the workflow file is committed and pushed
- Check the **Actions** tab for any error messages

### Build Failures

- Check the workflow logs in the **Actions** tab
- Verify all dependencies are listed correctly
- Ensure `mkdocs.yml` is in the `pos/` directory

### Pages Not Updating

- Wait a few minutes (GitHub Pages can take up to 10 minutes to update)
- Check the deployment status in **Settings → Pages**
- Verify the workflow completed successfully

## Custom Domain (Optional)

If you want to use a custom domain:

1. Add a `CNAME` file in `pos/docs/` with your domain name
2. Update `site_url` in `pos/mkdocs.yml`
3. Configure DNS settings for your domain

