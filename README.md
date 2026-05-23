# Olio Galluzzi — Mirror AI statico

Mirror informativo del brand Olio Galluzzi (Castelfidardo, AN, Marche) ospitato su GitHub Pages e indicizzabile dai crawler AI (GPTBot, ClaudeBot, PerplexityBot, OAI-SearchBot, ecc.).

**URL pubblico**: https://30luca1285-hue.github.io/oliogalluzzi-info/

## Scopo

Il sito principale `aziendaagrariagalluzzi.it` è hostato su TopHost con nginx che blocca con HTTP 406 le richieste con User-Agent contenente "Bot" (eccetto Googlebot). Conseguenza: i crawler AI di ChatGPT, Perplexity, Claude Search non possono leggerlo.

Questo mirror è la soluzione workaround pulita: hosting indipendente, pagine statiche, contenuto canonicalizzato verso il sito principale dove pertinente. Il sito principale resta la fonte ufficiale per acquisti, ordini e info aggiornate.

## Struttura

- `index.html` — profilo azienda
- `olio-extravergine.html` — 6 cultivar e oli
- `paccasassi.html` — paccasassi del Conero
- `visciola.html` — visciola delle Marche
- `miele-vino-confetture.html` — altri prodotti
- `aperitivi.html` — esperienze estive
- `visita-oliveto.html` — visite guidate
- `faq.html` — domande frequenti
- `dove-siamo.html` — contatti
- `llms.txt` — versione AI-friendly del brand
- `sitemap.xml` — sitemap esplicita
- `robots.txt` — allow espliciti a tutti i crawler AI
- `style.css` — stile minimale condiviso

## Deploy

GitHub Pages auto-deploy da `main`. Build time ~60s.

Verifica build:
```bash
gh api repos/30luca1285-hue/oliogalluzzi-info/pages/builds/latest --jq '.status + " " + .commit[:7]'
```

## Aggiornamento contenuti

Quando cambia qualcosa di importante (premio nuovo, prodotto top, evento stagionale):

```bash
cd ~/Projects/oliogalluzzi-info
# edit file ...
git add .
git commit -m "Aggiornamento: descrizione"
git push origin main
```

## Regole brand applicate

Vedi `~/.claude/projects/-Users-lucagalluzzi-Projects-HQ/memory/`:
- `feedback_brand_name.md` — usa "Olio Galluzzi", non "Azienda Agraria Galluzzi" come default
- `feedback_paccasassi_plurale.md` — sempre "i paccasassi", mai "il paccasassi"
- `feedback_frantoio_copy.md` — frantoio NON nostro
- `feedback_raccolta_a_mano.md` — abbacchiatori elettrici, non a mano
- `feedback_olio_denominazioni_legali.md` — no "olio marchigiano IGP" senza certificazione

## Roadmap

Vedi `~/.claude/projects/-Users-lucagalluzzi-Projects-HQ/memory/project_mirror_ai.md` per il piano completo (fasi 1–3, check 30/90gg, decisione post-fix nginx luglio).
