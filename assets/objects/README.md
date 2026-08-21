# Immagini oggetti

Per ogni oggetto che compare nelle mappe, metti qui un file `<id>.png` con sfondo
trasparente. Il nome del file deve coincidere esattamente con l'`id` dell'oggetto
usato nel campo `object` delle celle della mappa (es. `albero_ulivo.png`).

Finché il file non esiste, il Player mostra automaticamente un segnaposto colorato
con una sigla — non è necessario cambiare nulla nel codice: appena il PNG viene
aggiunto con il nome giusto, viene usato al posto del segnaposto.

Le immagini vengono disegnate sulla mappa ingrandite al **120% del lato della
cella** (possono quindi sconfinare leggermente sulle celle vicine, effetto
voluto per un look più "tridimensionale").

## Catalogo (`manifest.json`)

Ogni oggetto usato in una mappa deve avere una voce in `manifest.json`:

```json
{ "id": "albero_ulivo", "label": "Albero ulivo", "walkable": false }
```

- `id` — deve combaciare col nome del file immagine (senza estensione) e col
  valore `object` nella mappa.
- `label` — nome mostrato al giocatore (legenda, etichetta sotto l'oggetto).
- `walkable` — `true` se il giocatore può piazzare un personaggio su quella
  cella (es. tappeto, sedia), `false` se è un ostacolo (es. tavolo, albero).

Quando crei una nuova mappa nell'Editor con un oggetto non ancora presente qui,
aggiungi la sua voce a `manifest.json` e il relativo file `<id>.png`.

## ⚠️ Da verificare: `walkable` degli oggetti aggiunti in blocco

Il 21/08/2026 sono state caricate 111 immagini (l'intero catalogo oggetti). Gli
8 oggetti usati dalla mappa di esempio (`albero_ulivo`, `tavolo`, `letto`,
`vaso_di_piante`, `sedia`, `tappeto`, `lavandino`, `muro_a_secco`) hanno un
flag `walkable` confermato. Per gli altri ~103 il flag è stato impostato con
una regola automatica (calpestabile solo per sedute/superfici basse: divano,
poltrona, pouf, sgabello, panchina, lettino, materassino, telo da mare,
buccia di banana, luminarie; ostacolo per tutto il resto) — **non è garantito
che coincida con quanto assume l'Editor**. Se una mappa dell'Editor risulta
irrisolvibile nel Player (una cella "corretta" appare bloccata), controlla per
primo il flag `walkable` dell'oggetto in quella cella.

## Oggetti attualmente censiti (estratto; elenco completo in `manifest.json`)

| id | etichetta | tipo |
|---|---|---|
| albero_ulivo | Albero ulivo | ostacolo |
| tavolo | Tavolo | ostacolo |
| letto | Letto | calpestabile |
| vaso_di_piante | Vaso di piante | ostacolo |
| sedia | Sedia | calpestabile |
| tappeto | Tappeto | calpestabile |
| lavandino | Lavandino | ostacolo |
| muro_a_secco | Muro a secco | ostacolo |
