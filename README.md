# Athlete Intelligence — onboarding

De visuele gids met de zes stappen die **jouw** handen nodig hadden — allemaal klaar.
Live op Cloudflare:

**https://athlete-onboarding.aq-bd6.workers.dev**

## Wat erin staat

Per stap: **wat je doet**, **waarom het nodig is**, **hoe je weet dat het gelukt is**, en
**wat je aan mij doorgeeft**. Plus de valkuilen die iedereen overkomt.

| # | Stap | Status | Blokkeert |
|---|---|---|---|
| 1 | Cloudflare | klaar | Fase 0 |
| 2 | intervals.icu + Huawei | klaar | Fase 1 |
| 3 | Telegram-bot | klaar | Fase 7 |
| 4 | Hevy + AQ-log | klaar | Fase 6 |
| 5 | GitHub + app | klaar | Fase 5 |
| 6 | Model-API | klaar | Fase 5 |

De weegschaal lees je nu rechtstreeks uit via **Web Bluetooth** in de PWA (Chrome op
Android); de eerdere Tuya-route is daarmee vervallen.

## Deployen

Cloudflare heeft Pages onder Workers geschoven; dit project gebruikt de
Workers-met-assets vorm.

```bash
export CLOUDFLARE_API_TOKEN="$(cat ~/.config/opencode/secrets/cloudflare-token)"
export CLOUDFLARE_ACCOUNT_ID=<jouw-account-id>
npx wrangler deploy
```

De config staat in `wrangler.jsonc`; de bestanden in `public/`.

## Structuur

```
athlete-onboarding/
├── public/
│   └── index.html      ← de hele gids, zelfstandig (geen externe CSS)
├── wrangler.jsonc      ← Workers met assets
└── README.md
```

Eén zelfstandig HTML-bestand: geen build stap, geen dependencies, lettertypes met een
systeem-fallback zodat het ook zonder internet leesbaar blijft.

## Verwante stukken

- **Voorstel & onderbouwing** — https://rm-bcn.github.io/athlete-os/
- **Bouwplan met acceptatiecriteria** — `PLAN.md` in die repo
- **Workboard** — negen kaarten onder het project *Athlete Intelligence*
