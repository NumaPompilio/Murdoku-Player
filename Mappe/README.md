# Mappe

Metti qui i file `.md` esportati dalla sezione "Player" dell'Editor Murdoku
(contengono un commento `<!-- MURDOKU_STATE_B64: ... -->` con lo stato completo
della mappa).

Ogni volta che aggiungi o rimuovi un file, aggiorna anche `index.json` in questa
cartella — è l'elenco che il Player legge per popolare il menu a tendina
all'avvio:

```json
[
  { "file": "Nome_Mappa.md", "title": "Titolo mostrato nel menu" }
]
```

Se dimentichi di aggiornare `index.json` (o il file non è raggiungibile), il
Player prova comunque a elencare le mappe leggendo direttamente la cartella
tramite le API pubbliche di GitHub — ma tenere `index.json` aggiornato è più
veloce e affidabile.
