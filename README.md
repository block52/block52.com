# block52.com

The Block52 landing page: plain HTML and CSS, no build step.

- `index.html`: the page (styles inline; Google Fonts: Fraunces, Inter, Caveat)
- `404.html`: not-found page
- `logo.svg`, `favicon.svg`, `logo512.png`: brand assets, copied from `block52/ui/public`
- `.do/app.yaml`: DigitalOcean App Platform spec (a static site that deploys on every push to `main`)

## Preview locally

```bash
python3 -m http.server 8080
# open http://localhost:8080
```

## Deploy

The site is a DigitalOcean App Platform static site in the **b52** project. Every push to `main` redeploys it.

The first time only:

```bash
doctl projects list                       # find the b52 project id
doctl apps create --spec .do/app.yaml --project-id <b52-project-id>
```

The site is served at `block52.xyz` and `www.block52.xyz`, declared in the spec with `zone: block52.xyz`. That zone's DNS is in DigitalOcean, so App Platform creates the records and the TLS certificate itself. Any old apex or `www` records must be removed first; they pointed at Vercel.

`block52.com` can be added the same way once it's redeemed and its nameservers point at DigitalOcean.

Links on the page point to the app at `https://app.block52.xyz`.
