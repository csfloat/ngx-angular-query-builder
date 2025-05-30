# Publishing to npm Registry

This guide explains how to publish the `@csfloat/ngx-angular-query-builder` library to the npm registry.

## Prerequisites

1. **npm Account**: Create an account at [npmjs.com](https://www.npmjs.com/)
2. **npm Access Token**: Create an automation token from your npm account settings
3. **GitHub Repository**: Ensure your code is pushed to a GitHub repository
4. **Organization Access**: Ensure you have publish permissions for the `@csfloat` organization on npm

## Setup Steps

### 1. Configure npm Token for GitHub Actions

1. **Create npm Access Token:**
   - Go to [npmjs.com](https://www.npmjs.com/) → Account Settings → Access Tokens
   - Click "Generate New Token" → "Automation"
   - Copy the token

2. **Add token to GitHub Secrets:**
   - Go to your GitHub repository → Settings → Secrets and variables → Actions
   - Click "New repository secret"
   - Name: `NPM_TOKEN`
   - Value: Your npm access token

### 2. Local Publishing (Manual)

If you want to publish manually:

1. **Build the library:**
   ```bash
   npm run build-package
   ```

2. **Navigate to the dist folder:**
   ```bash
   cd dist/ngx-angular-query-builder
   ```

3. **Login to npm:**
   ```bash
   npm login
   ```
   - Username: Your npm username
   - Password: Your npm password
   - Email: Your npm email
   - One-time password: If you have 2FA enabled

4. **Publish:**
   ```bash
   npm publish
   ```

### 3. Automated Publishing (Recommended)

The project is configured for automated publishing via GitHub Actions.

#### Publishing Process:

1. **Update version number:**
   ```bash
   # Update version in projects/ngx-angular-query-builder/package.json
   # For example, change "19.0.0" to "19.0.1"
   ```

2. **Create a new release:**
   - Go to your GitHub repository
   - Click "Releases" → "Create a new release"
   - Tag version: `v19.0.1` (match your package version)
   - Release title: `Release v19.0.1`
   - Describe the changes
   - Click "Publish release"

3. **GitHub Actions will automatically:**
   - Install dependencies
   - Build the library
   - Run tests
   - Publish to npm

#### Manual Trigger:
You can also manually trigger the workflow:
- Go to Actions tab in your GitHub repository
- Select "Publish to npm" workflow
- Click "Run workflow"

## Version Management

Before publishing a new version:

1. **Update the library package.json:**
   ```json
   // projects/ngx-angular-query-builder/package.json
   {
     "version": "19.0.1"  // Update this
   }
   ```

2. **Commit and tag:**
   ```bash
   git add .
   git commit -m "Release v19.0.1"
   git tag v19.0.1
   git push origin main --tags
   ```

## Installation for Users

Once published, users can install your package easily:

```bash
npm install @csfloat/ngx-angular-query-builder
```

No authentication required! 🎉

## Troubleshooting

### Common Issues:

1. **Authentication Error:**
   - Ensure your npm token is valid and has publish permissions
   - Check that the NPM_TOKEN secret is correctly set in GitHub
   - Verify you have access to publish under the `@csfloat` organization

2. **Organization Access:**
   - You must be a member of the `@csfloat` organization on npm
   - The organization must exist on npm
   - Your npm token must have permission to publish to the organization

3. **Version Already Published:**
   - You cannot publish the same version twice
   - Increment the version number in package.json

4. **Build Errors:**
   - Run `npm run build-package` locally to check for issues
   - Ensure all dependencies are correctly specified

### Useful Commands:

```bash
# Check what will be published
cd dist/ngx-angular-query-builder
npm pack --dry-run

# View package info
npm view @csfloat/ngx-angular-query-builder

# List published versions
npm view @csfloat/ngx-angular-query-builder versions --json

# Check if organization exists
npm org ls @csfloat
```

## Security Notes

- Never commit npm tokens to your repository
- Use GitHub secrets for sensitive information
- Regularly rotate your npm access tokens
- Consider enabling 2FA on your npm account

## Organization Setup

If the `@csfloat` organization doesn't exist on npm yet:

1. **Create the organization:**
   - Go to [npmjs.com](https://www.npmjs.com/)
   - Click your profile → "Add Organization"
   - Name: `csfloat`
   - Choose organization type (free for public packages)

2. **Add team members:**
   - Invite other CSFloat team members to the organization
   - Set appropriate permissions for each member

3. **Configure organization settings:**
   - Set up organization profile and description
   - Configure package access policies if needed
