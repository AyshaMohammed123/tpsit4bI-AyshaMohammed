# Esercizio 6 — Tornare indietro senza perdere lavoro

## Prima situazione: 

#### 1. un file è stato aggiunto all'indice per sbaglio e va tolto dall'indice senza perdere le modifiche

**comandi :**

```
touch file-sbagliato.txt
git add file-sbagliato.txt
git status  # (Vedrai il file in verde: "Changes to be committed")
```

#### IL COMANDO DI RECUPERO:
```
git restore --staged file-sbagliato.txt
git status
```

- **comando usato :** git restore --staged file-sbagliato.txt
- **effetto :** Il file viene tolto dall'area di staging senza perdere le modifiche.
- **indice :** Il file passa dallo stato "staged", ovvero di colore verde pronto per essere salvato nella cronologia tramite commit allo stato "unstaged" colore rosso.
- **area di lavoro :** il nuovo file e le modifiche rimangono intatti e non viene perso codice.
- **storia :** nessun commit viene creato o modificato.

#### 2. un file è stato modificato nell'area di lavoro e la modifica va scartata, tornando all'ultimo commit;

**comandi :**

```
git status
```

#### IL COMANDO DI RECUPERO:
```
git restore README.md
git status 
```

- **comando usato :** git restore README.md
- **effetto :** La modifica non salvata viene eliminata e il file viene riportato all'ultimo commit.
- **indice :** Rimane pulito e non subisce variazioni visto che la modifica non era mai stata aggiunta allo staging.
- **area di lavoro :** La riga inserita nel file viene cancellata e il file torna al suo stato originale.
- **storia :** Rimane del tutto invariata.


#### 3. l'ultimo messaggio di commit contiene un errore di battitura e va corretto senza creare un nuovo commit.

**comandi :**

```
touch test-commit.txt
git add test-commit.txt
git commit -m "Aggiunge un file con un errore di batitura"
```

#### IL COMANDO DI RECUPERO:
```
git commit --amend -m "Aggiunge un file con un errore di battitura corretto"
git log --oneline
```

- **comando usato :** git commit --amend -m "Aggiunge un file con un errore di battitura corretto"
- **effetto :** Il testo dell'ultimo commit viene modificato per correggere l'errore fatto precedentemente senza generare un secondo commit
- **indice :** Rimane invariato, conserva solo lo stato dei file già inclusi in quel commit
- **area di lavoro :** Rimane pulita e non subisce alterazioni.
- **storia :** Il vecchio commit con l'errore di battitura viene rimpiazzato da quello nuovo.
