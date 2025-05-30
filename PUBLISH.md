# Publishing to GitHub Package Registry

This guide explains how to publish the `ngx-angular-query-builder` library to GitHub Package Registry.

## Prerequisites

1. **GitHub Repository**: Ensure your code is pushed to a GitHub repository
2. **GitHub Personal Access Token**: Create a token with `write:packages` scope
3. **Updated Configuration**: Make sure all configuration files are properly set up

## Local Publishing (Manual)

If you want to publish manually:

1. **Build the library:**
   ```bash
   npm run build-package
   ```

2. **Navigate to the dist folder:**
   ```bash
   cd dist/ngx-angular-query-builder
   ```

3. **Login to GitHub Package Registry:**
   ```bash
   npm login --registry=https://npm.pkg.github.com
   ```
   - Username: Your GitHub username (lowercase)
   - Password: Your GitHub Personal Access Token (classic)

4. **Publish:**
   ```bash
   npm publish
   ```

## Installation for Users

Once published, users can install your package by:

1. **Creating `.npmrc` in their project:**
   ```
   @YOUR_GITHUB_USERNAME:registry=https://npm.pkg.github.com
   //npm.pkg.github.com/:_authToken=THEIR_GITHUB_TOKEN
   ```

2. **Installing the package:**
   ```bash
   npm install @YOUR_GITHUB_USERNAME/ngx-angular-query-builder
   ```

## Troubleshooting

### Common Issues:

1. **Authentication Error:**
   - Ensure you are using a GitHub classic access token with `write:packages` scope
   - Verify the token is not expired

2. **Package Not Found:**
   - Check the package name includes the @csfloat scope
   - Ensure the repository is public and you have access to it

4. **Workflow Failures:**
   - Check the Actions tab for detailed error logs
   - Ensure GITHUB_TOKEN has sufficient permissions
