# TAAS GitHub Pages Site

Static GitHub Pages site for TAAS, a high-throughput transformation platform for Kafka Connect pipelines.

## What This Repo Contains

- `index.html` - landing page content and structure
- `style.css` - site styling and responsive layout
- `script.js` - lightweight progressive enhancement
- `assets/` - placeholder for logo, favicon, or product visuals
- `.github/workflows/deploy-pages.yml` - GitHub Pages deployment workflow

## Publish On GitHub Pages

This setup is designed for a public repository and GitHub Actions-based Pages deployment. For GitHub Free and most organization Pages setups, keep the repository public.

1. Create or use a public repository.
2. Push these files to the `main` branch.
3. In GitHub, open `Settings -> Pages`.
4. If needed, confirm that the source is GitHub Actions.
5. Push to `main` and check the `Actions` tab for the Pages deployment run.
6. After the site is live, enforce HTTPS in the Pages settings.

## Notes

- The workflow uses the standard GitHub Pages actions flow.
- No build system, package manager, or framework is required.
- The site is fully static and can be edited with plain HTML, CSS, and JavaScript.

## Checklist

- [ ] Replace placeholder links in the site
- [ ] Add a logo or favicon if desired
- [ ] Set the repository description
- [ ] Set the website URL in the repository settings
- [ ] Add GitHub topics
- [ ] Enforce HTTPS in GitHub Pages settings
