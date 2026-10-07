# Athlete Intelligence — onboarding

De visuele gids met de acht dingen die **jouw** handen nodig hebben voordat ik kan bouwen.
Live op Cloudflare:

**https://athlete-onboarding.aq-bd6.workers.dev**

## Wat erin staat

Per stap: **wat je doet**, **waarom het nodig is**, **hoe je weet dat het gelukt is**, en
**wat je aan mij doorgeeft**. Plus de valkuilen die iedereen overkomt.

| # | Stap | Tijd | Blokkeert |
|---|---|---|---|
| 1 | Cloudflare | klaar | Fase 0 |
| 2 | intervals.icu + Huawei | 15 min | Fase 1 |
| 3 | Health Connect aanzetten | 2 min | vangnet |
| 4 | Tuya IoT + weegschaal | 15 min | Fase 1 |
| 5 | Telegram-bot | 5 min | Fase 7 |
| 6 | Hevy + Health Connect | 2 min | Fase 6 |
| 7 | GitHub-vault | 3 min | Fase 5 |
| 8 | Model-API | 3 min | Fase 5 |

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
