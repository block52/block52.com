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

`block52.com` and `www.block52.com` are declared in the spec with `zone: block52.com`. If the domain's DNS is hosted in DigitalOcean (nameservers `ns1/ns2/ns3.digitalocean.com`), App Platform creates the records and the TLS certificate itself.

Links on the page point to the app at `https://app.block52.xyz`.
