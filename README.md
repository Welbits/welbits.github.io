# welbits.com

Static site for [welbits.com](https://welbits.com), served by GitHub Pages from
the `master` branch of this repository (Settings → Pages → Deploy from branch,
`master`, `/`). Every push to `master` deploys automatically; there is no build
step.

Replaces the old `welbits-web` repository, which was served by an nginx
container on an AWS EC2 instance (`welbits-server-gateway`) that no longer
exists.

## Contents

- `index.html` – landing page listing the apps.
- `privacy-policies/` – privacy policies linked from the store listings.
- `app-ads.txt` / `ads.txt` – AdMob authorized sellers. Must stay at the root.
- `CNAME` – custom domain (`welbits.com`). Do not delete it or GitHub Pages
  drops the domain.
- `images/*.webp`, `static_stops.json`, `all_stops_20200209.json`,
  `apps/madrid/schedules/lines.json` – static data loaded at runtime by the
  busmadrid.welbits.com / transit.welbits.com web app (hard-coded
  `https://welbits.github.io/...` URLs in its bundle). Never delete or rename
  them; the web app breaks without them.

## DNS (Gandi)

Zone records required for the custom domain:

| Name | Type  | Value                |
|------|-------|----------------------|
| @    | A     | 185.199.108.153      |
| @    | A     | 185.199.109.153      |
| @    | A     | 185.199.110.153      |
| @    | A     | 185.199.111.153      |
| www  | CNAME | welbits.github.io.   |

Leave the MX and TXT records untouched. After changing DNS, in Settings →
Pages set the custom domain to `welbits.com`, wait for the DNS check, then
enable "Enforce HTTPS".

## app-ads.txt

AdMob crawls `https://<developer website>/app-ads.txt`, where the developer
website is the URL set in each store listing: Google Play Console → Store
settings → Store listing contact details → Website; App Store Connect → app →
Marketing URL. Both must be `https://welbits.com`. AdMob re-crawls within
about 24 hours.
