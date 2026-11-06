# Bodymo temporary website

Small Vue + Vite SPA, intentionally limited to a landing page and an interactive
browser smoke test at `/setup`. The setup component lives in `setup/`. No backend,
tracker connection, firmware flashing, credentials, or persistence is implemented.

## Local development

```sh
cd web
npm ci
npm run dev
```

`npm run build` produces `dist/`; `npm run preview` serves that build locally.
Cloudflare Pages serves the SPA entry point for direct navigation to `/setup`.

## Deployment — native Cloudflare Git integration

Cloudflare Pages project **bodymo-web** is connected directly to
`maoawa/bodymo-tracker` through Cloudflare's GitHub App. No GitHub Actions workflow,
Cloudflare API key, or GitHub repository secret is needed.

Push changes under `web/` to `main` to trigger a production build and deployment.
Cloudflare reports deployment status on the GitHub commit. Preview-branch builds
are disabled; unrelated firmware changes do not trigger website builds.

### Cloudflare build settings

| Setting | Value |
| --- | --- |
| Production branch | `main` |
| Root directory | `web` |
| Build command | `npm run build` |
| Output directory | `dist` |
| Environment variable | `NODE_VERSION=24` |
| Included build paths | `web/*` (Cloudflare wildcard includes nested paths) |

Dependencies are installed from `package-lock.json` during the Pages build.
Check builds in Cloudflare → Workers & Pages → bodymo-web → Deployments.

### Hosting and domain migration

- Git-connected project: `https://bodymo-web.pages.dev`
- Setup test: `https://bodymo-web.pages.dev/setup`
- Intended custom domain: `bodymo.maao.cc`
- Target DNS record: `CNAME bodymo → bodymo-web.pages.dev`

The original Direct Upload project `bodymo` is retained as a fallback at
`https://bodymo.pages.dev`. The new Git-connected project has passed its first
Cloudflare build. Its custom-domain target is `bodymo.maao.cc`; the DNS CNAME
must point to `bodymo-web.pages.dev` rather than the old `bodymo.pages.dev`.

### Optional manual deployment

For an emergency manual deployment, local Wrangler OAuth login still works:

```sh
cd web
npx wrangler login
npm run deploy
```

Normal deployments use Git integration; there is no token setup step.
