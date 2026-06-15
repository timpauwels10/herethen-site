# herethen-site

Source for the [herethen.net](https://herethen.net) holding page.

Single static `index.html`, served by Cloudflare Pages (project: `herethen`). Auto-deploys from `main`.

## Visibility guarantee

The page must render fully visible even when CSS animations don't run (e.g. animations blocked, browser quirk, page loaded in a sandbox that strips them). The default state of every element is the *final* state (`opacity: 1`, no transform); entrance animations are layered as enhancement via `@media (prefers-reduced-motion: no-preference)` only. A reduced-motion user — or any environment where animations fail to start — gets the same fully-visible page.

When editing, do not move animation declarations back out into the default rules without restoring this guarantee.

## Deploy

Pushing to `main` triggers Cloudflare Pages auto-deploy. No build step (output dir = `/`, build command empty).

To verify after deploy:

```bash
curl -sS https://herethen.net | grep -i herethen
```

Should return the wordmark markup and the meta description, not empty.
