# eurocedibe-grafiche

Solo le **grafiche dei post Instagram**, una cartella per mese (`AAAA-MM`).

Questo repo è **pubblico** per un motivo tecnico preciso: Instagram non accetta
un file caricato, pretende un indirizzo che i server di Meta possano scaricare
da soli. Google Drive non va bene, i link di Canva nemmeno, e un repo privato
richiederebbe un token che Meta non ha. **Facebook invece accetta il file
direttamente: per Facebook questo repo non serve**, e infatti qui non ci finisce
nulla dei post che escono solo su Facebook.

Gli indirizzi hanno questa forma, e finiscono nella coda di pubblicazione:

    https://raw.githubusercontent.com/SaraIlaria/eurocedibe-grafiche/main/2026-10/02-eurocedibe.jpg

## Il peso: perché le immagini qui sono più leggere dell'originale

Le grafiche su Drive pesano in media **1,2 MB**, alcune superano i 10 MB — oltre
il limite di 8 MB di Instagram. Caricarle così com'erano avrebbe gonfiato questo
repo di circa **580 MB l'anno**, e in Git **cancellare un file non libera spazio**:
la copia resta nella storia per sempre.

Perciò il Gestionale Marketing **non carica l'originale**. Prima di mandarla qui
la ridimensiona a **1080 px di lato lungo** (Instagram non ne usa di più) e la
ricomprime in **JPEG**. Si passa da ~1,2 MB a ~200 KB: circa **100 MB l'anno**,
non 580. La grafica originale resta intatta su Drive: qui c'è solo la copia da
dare a Instagram.

## Fare pulizia quando serve

Una grafica serve **solo nel momento in cui il post esce**: dopo, quell'indirizzo
non lo guarda più nessuno. Le cartelle dei mesi passati si possono cancellare
senza pensarci.

Per liberare davvero lo spazio, però, non basta cancellare i file: va azzerata
la storia. Si fa in un minuto, e si può fare una volta l'anno:

    git checkout --orphan pulito
    git add -A
    git commit -m "Riparto da qui"
    git branch -D main
    git branch -m main
    git push -f origin main

Gli indirizzi delle grafiche ancora presenti **non cambiano**: puntano al
contenuto del branch, non al commit.

## Cosa NON va messo qui

Le immagini qui dentro **le può vedere chiunque abbia il link**. Sono grafiche
destinate a uscire sui social, quindi va bene — ma solo quelle.

Niente copy, niente listini, niente file di lavoro, niente PDF interni, niente
report, niente nomi di persone o dati di clienti. Se un file non è una grafica
che uscirà pubblicamente su un social, non va in questo repo.

## Requisiti di Instagram

- **JPEG** (PNG e WEBP non sempre passano) — la conversione la fa il gestionale
- proporzioni fra 4:5 e 1.91:1 — i 4:5 che escono da Canva vanno bene
- massimo 8 MB
