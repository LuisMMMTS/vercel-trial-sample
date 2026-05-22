# vercel-trial-sample

A single-page static site used to exercise Vercel deployments end to end against a public GitHub repo.

No build step, no framework. Just `index.html` + `vercel.json`. Useful as a known-good payload for testing Vercel project creation, linking, environment variables, auth/SSO settings, or rollback flows without dragging a real application along.

## Deploy

Either:

- Import this repo at https://vercel.com/new — Vercel auto-detects it as a static project; first push to `main` deploys.
- Or run `vercel` locally from this directory.

If you want the deployed URL gated to logged-in Vercel users (not anonymously reachable), enable **Vercel Authentication** on the project:

```
PATCH https://api.vercel.com/v9/projects/{idOrName}?teamId={team}
{ "ssoProtection": { "deploymentType": "all" } }
```

That gates the deployed URL to logged-in members of whichever Vercel team imports it. On Hobby plans only `deploymentType=preview` is available, which gates preview deploys but not the production URL.
