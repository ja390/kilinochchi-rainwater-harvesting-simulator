# Publishing guide

This directory is prepared as the root of a public project repository. Before publishing:

1. Review the README links and ensure the Colab notebook link opens the public notebook.
2. In GitHub, add these root-level files and directories, replacing the earlier nested layout when practical.
3. In **Settings → Pages**, choose **Deploy from a branch**, select `main` and `/docs`, then save.
4. After deployment finishes, test `https://ja390.github.io/kilinochchi-rainwater-harvesting-simulator/` and run the reference check; then update the README's live-demo link to that URL.
5. Edit the repository's **About** description to: “A stochastic simulation explores how tank capacity, roof area, household demand and collection efficiency affect daily rainwater availability in Kilinochchi, Sri Lanka.”
6. Review the repository, Pages source, notebook markdown and saved outputs for personal information, affiliations, secrets and stale links.
7. Add meaningful commits as development proceeds and create the `v1.0` tag only after reviewing the final public state.

Changing the Pages source to `/docs` makes `docs/index.html` the site homepage. The older demo path may remain available only while the previous nested files remain in the repository.
