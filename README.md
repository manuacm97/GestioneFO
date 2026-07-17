# FO Manager ⚽

App web (PWA) per gestire la tua Società di **FantaOrgoglio**, il fantacalcio manageriale: rosa, bilancio, mercato, statistiche, palmares e regolamento — tutto in un unico file, tutto offline, tutto tuo.

## Funzionalità

- **Rosa** — giocatori per reparto con badge ruolo, foto stile Football Manager (faccia + maglia nei colori della squadra reale), tag di stato (U21, Grigio, Comproprietà, Prestito, in rosa o fuori), contatori dei limiti regolamentari con avvisi, divise della stagione.
- **Bilancio** — feed dei movimenti, saldo e proiezioni a metà e fine stagione, dettaglio stipendi e rate per giocatore, clausole e bonus, calcolatore plus/minus con ammortamento per stagioni di permanenza.
- **Mercato** — lista provvisoria con proiezione del budget dopo gli acquisti e controlli sui posti in rosa.
- **Stats** — classifica presenze/gol/assist ordinabile e filtrabile per ruolo, modalità ⚡ per inserire P/G/A al volo (clic +1, clic destro −1).
- **Palmares** — piazzamenti stagione per stagione (Campione, Promosso, Ripescato, Retrocesso…) e bacheca trofei con foto.
- **Storico** — stagioni archiviate con registro operazioni, divise e note.
- **Regolamento** — articoli ricercabili, sempre a portata di tap.
- **Logo società** — visibile in ogni pagina e come watermark; PNG con trasparenza supportati.

## Come si usa

**In locale:** apri `index.html` in un browser moderno. Fine.

**Online (GitHub Pages):**
1. Carica questi file in un repository.
2. Settings → Pages → Deploy from branch → `main` / root.
3. Apri l'URL che ti dà GitHub: da lì puoi anche **installarla** come app (Aggiungi a schermata Home / Installa app) e funziona offline grazie al service worker.

## Dati e backup

I dati vivono nel `localStorage` del browser (chiave `foManager_v1`), incluse le immagini (compresse in WebP/PNG al caricamento). Nessun server, nessun account.

- **Esporta backup** (pagina Altro) → scarica un JSON con *tutto*: rosa, movimenti, stagioni, foto, divise, logo e trofei.
- **Importa backup** → ripristina o sposta i dati su un altro dispositivo/browser.

⚠️ Il `localStorage` ha un limite di ~5–10 MB per sito: se carichi molte immagini ad alta risoluzione l'app ti avvisa al salvataggio. Esporta un backup ogni tanto.

## Struttura del progetto

```
index.html            → l'app completa (HTML + CSS + JS in un solo file)
manifest.webmanifest  → manifest PWA
sw.js                 → service worker (cache-first, offline)
icons/                → icone 192/512
```

## Note tecniche

- Nessuna dipendenza, nessuna build: un solo file HTML autosufficiente (font Inter da Google Fonts, con fallback di sistema).
- I colori dei mini-loghi delle squadre (Serie A/B/C) sono in una mappa interna, modificabile cercando `const TEAMS` in `index.html`.
- Regole di calcolo implementate: stipendio = 10% del valore (arrotondato per eccesso a 0,1), 1ª rata = metà per eccesso a passo 0,05, 2ª rata = metà per difetto a passo 0,1.

## Licenza

[MIT](LICENSE)
