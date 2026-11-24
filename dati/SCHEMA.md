# Scheda dati del Programma Segnale

## Entità

### Evento

Ogni evento descrive un appuntamento del festival.

| Campo | Tipo | Esempio |
|---|---|---|
| `id` | numero intero | `1` |
| `titolo` | testo | `"Lettere in movimento"` |
| `data` | data in formato `AAAA-MM-GG` | `"2026-06-12"` |
| `orario` | testo in formato `HH:MM` | `"10:00"` |
| `categoria` | testo | `"Incontro"` |
| `descrizione` | testo | `"Come cambia un messaggio quando cambiano le lettere?"` |
| `immagine` | percorso di un file, testo | `"assets/lettere-in-movimento.svg"` |
| `immagine_alt` | testo alternativo | `"Lettere geometriche disposte su una griglia"` |
| `sede_id` | numero intero | `1` |

### Sede

Ogni sede descrive un luogo associato agli eventi.

| Campo | Tipo | Esempio |
|---|---|---|
| `id` | numero intero | `1` |
| `nome` | testo | `"Officina Nord — Sede centrale"` |
| `indirizzo` | testo | `"Corso Duca degli Abruzzi 24, Torino"` |

## Chiavi e relazione

`Evento.id` è la chiave primaria degli eventi; `Sede.id` è la chiave primaria delle sedi. Entrambe sono numeriche, univoche nella rispettiva entità e stabili.

Una sede può ospitare più eventi; ogni evento si svolge in una sede. Il campo `Evento.sede_id` fa riferimento a `Sede.id`.

## Quantità

Il programma contiene sei eventi e tre sedi.

## Aggiornamento dei dati

Chi gestisce il sito aggiorna i dati modificando `dati/eventi.json` e `dati/sedi.json` nella repository. Dopo il controllo delle modifiche, pubblica la versione aggiornata del sito.

## Che cosa mostra la pagina

La pagina Programma legge i due file JSON e mostra per ogni evento immagine, data, orario, categoria, titolo, descrizione e nome della sede. Se la sede collegata non è presente, mostra «Sede da definire».

## Schema Evento–Sede

```mermaid
erDiagram
    SEDE ||--o{ EVENTO : ospita
    SEDE {
        int id PK
        string nome
        string indirizzo
    }
    EVENTO {
        int id PK
        string titolo
        string data
        string orario
        string categoria
        string descrizione
        string immagine
        string immagine\_alt
        int sede\_id FK
    }