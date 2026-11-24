# Publishing Guide

This guide explains how to publish and maintain the Kilinochchi Rainwater Harvesting Simulator using GitHub Pages.

## 1. Prepare the Repository

- Ensure the repository is public.
- Ensure `index.html` is located at the repository root.
- Include all required JavaScript, CSS, notebook and documentation files.
- Verify that all relative file paths are correct.

## 2. Deploy Using GitHub Pages

1. Open the GitHub repository.
2. Navigate to **Settings → Pages**.
3. Under **Build and deployment**, select **Deploy from a branch**.
4. Select the `main` branch.
5. Select `/ (root)` as the publishing source.
6. Click **Save**.
7. Wait for the deployment to complete.

The root-level `index.html` serves as the website homepage.

**Live demo:**

https://ja390.github.io/kilinochchi-rainwater-harvesting-simulator/

## 3. Verify the Deployment

- Open the live demo in a browser.
- Test all adjustable parameters and simulation controls.
- Confirm that charts and numerical outputs update correctly.
- Run the reference verification check.
- Confirm that the website is accessible without authentication.

## 4. Update Repository Information

Ensure the README contains the correct live demo URL, Open in Colab link and documentation links.

Set the repository description to:

> A stochastic simulation exploring how tank capacity, roof area, household demand and collection efficiency affect daily rainwater availability in Kilinochchi, Sri Lanka.

## 5. Review Before Release

- Verify notebook execution and reproducibility.
- Check documentation, references and data credits.
- Remove sensitive information, credentials and outdated links.
- Maintain meaningful development commits.
- Confirm that the licence is included.

## 6. Create the Final Release

After completing all verification and documentation checks, create and publish the final version tag:

```bash
git tag -a v1.0 -m "Version 1.0 - Initial stable release"
git push origin v1.0
```

Record the final commit hash:

```bash
git rev-list -n 1 v1.0
```

The project is ready for public release once all deployment and verification checks pass.
