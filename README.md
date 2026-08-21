# Murdoku Player

Single-page app (un solo file `index.html`, senza build né dipendenze esterne)
per giocare le mappe create con il [Murdoku Editor](https://numapompilio.github.io/murdoku-studio/).

Estrae ed esegue solo la logica del "Player" dell'Editor originale: griglia,
muri/finestre/porte, oggetti, piazzamento sospetti/vittima, appunti, indizi,
validazione della soluzione.

## Come si gioca

All'avvio compare un popup con l'elenco delle mappe disponibili nella cartella
[`Mappe/`](Mappe/) di questo repository. Scegli una mappa e premi **"Gioca
questa mappa"**. In alternativa puoi incollare direttamente il testo di un
file `.md` esportato dall'Editor (scheda "Incolla mappa").

Regole e comandi (click = appunto, doppio click = piazza, ecc.) sono spiegati
nel pulsante **"Regole del gioco"** in alto.

## Struttura del repository

```
index.html              ← l'intera app (HTML+CSS+JS, un solo file)
Mappe/                   ← file .md delle mappe giocabili
  index.json             ← elenco mappe mostrato nel popup iniziale
  Masseria_Hard.md        ← mappa di esempio
assets/objects/           ← immagini degli oggetti (arredi, ostacoli, ecc.)
  manifest.json            ← catalogo oggetti (id, etichetta, calpestabile/ostacolo)
  <id>.png                 ← un'immagine per ciascun oggetto (opzionale: se manca,
                              viene mostrato un segnaposto colorato automatico)
```

Per aggiungere una nuova mappa: esporta il `.md` dall'Editor, copialo in
`Mappe/`, aggiungi una riga in `Mappe/index.json`. Se la mappa usa un oggetto
non ancora catalogato, aggiungi la voce in `assets/objects/manifest.json` e
(quando disponibile) l'immagine `assets/objects/<id>.png` — vedi
[`assets/objects/README.md`](assets/objects/README.md).

## Sviluppo/test in locale

Il Player usa `fetch()` per leggere `Mappe/index.json`, i file mappa e
`assets/objects/manifest.json`: **non funziona aprendo `index.html` a doppio
click** (protocollo `file://`, bloccato dal browser). Serve un piccolo server
statico locale, ad esempio:

```bash
python3 -m http.server 8420
```

poi apri `http://localhost:8420/`.

## Pubblicazione su GitHub Pages

1. Fai il push di questo repository su `main` di
   `github.com/NumaPompilio/Murdoku-Player`.
2. Su GitHub: **Settings → Pages → Source → Deploy from a branch**, branch
   `main`, cartella `/ (root)` → Save.
3. Dopo qualche minuto il Player sarà giocabile su
   `https://numapompilio.github.io/Murdoku-Player/`.

Non serve alcuna build: essendo `index.html` autosufficiente, GitHub Pages lo
serve così com'è.
