# vercel-trial-sample

A single-page static site used to exercise Vercel deployments as part of the [PE-1257](https://kevel-team.atlassian.net/browse/PE-1257) internal-apps trial.

Public repo (so the Vercel import flow doesn't need any special permissions), no build step, no framework. Just `index.html` + `vercel.json`.

## Deploy

Either:

- Import this repo at https://vercel.com/new — Vercel auto-detects it as a static project; first push to `main` deploys.
- Or run `vercel` locally from this directory.

Whichever path, **enable Vercel Authentication on the project** before the first deploy so it's not anonymously reachable. See [the skill](https://github.com/adzerk/kevel-internal-apps/blob/main/trials/vercel/skill/SKILL.md) for the patch:

```
PATCH https://api.vercel.com/v9/projects/{idOrName}?teamId={team}
{ "ssoProtection": { "deploymentType": "all" } }
```

That gates the deployed URL to logged-in members of whichever Vercel team imports it.
