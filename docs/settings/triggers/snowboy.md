## Parametri

Puoi creare la tua hotword collegandoti a [Snowboy](https://snowboy.kitt.ai/) e poi scaricare il file generato che fungerà da modello.

Una volta scaricato, posiziona il file nella tua cartella config personale e [imposta snowboy](../settings.md) con la seguente tabella

| Parametro   |Necessario|  Tipo  | Default | Valori possibili| Commento                                                                                                                         |
|-------------|----------|--------|---------|-----------------|----------------------------------------------------------------------------------------------------------------------------------|
| pmdl_file   | TRUE     | stringa|         |                 | Percorso del file del modello Snowboy. Il percorso può essere assoluto o relativo al file brain                                  |
| sensitivity | FALSE    | stringa| 0.5     |    tra 0 e 1    | Aumentando il valore di sensibilità si ottiene una migliore velocità di rilevamento, ma anche un più alto tasso di falsi allarmi |

## Impostazioni d'esempio

```yaml
# Questo è il trigger che catturerà la tua hotword per svegliare Kalliope. Solo Snowboy è disponibile finora
default_trigger: "snowboy"

# Caricare la configurazione del trigger
triggers:
  - snowboy:
      pmdl_file: "trigger/snowboy/resources/kalliope-FR-40samples.pmdl"
```

## Modelli Snowboy disponibili

Se vuoi mantenere "Kalliope" come nome del tuo bot, ti consigliamo di __migliorare il modello Snowboy esistente per la tua lingua__.

Aggiorneremo il seguente elenco con tutti i modelli che la comunità ha creato per Kalliope. Se il modello non esiste, crearne uno con la seguente sintassi:
```
kalliope-<language_code>
```

Es
```
kalliope-FR
kalliope-EN
kalliope-RU
kalliope-DE
kalliope-IT
```
Quindi, apri una "issue" o crea una "pull request" per aggiungere il modello all'elenco seguente.

> **Nota importante:** Non migliorare un modello nella lingua sbagliata. Controlla la pronuncia prima di registrare la tua voce!

| Nome                                                 |  lingua  |  Pronuncia   |
|------------------------------------------------------|----------|--------------|
| [kalliope-FR](https://snowboy.kitt.ai/hotword/1363)  | Francese | Ka-lio-pé    |
| [kalliope-EN](https://snowboy.kitt.ai/hotword/2540)  | Inglese  | kə-LIE-ə-pee |
| [kalliope-RU](https://snowboy.kitt.ai/hotword/2964)  | Russo    | каллиопа     |
| [kalliope-DE](https://snowboy.kitt.ai/hotword/4324)  | Tedesco  | Ka-lio-pe    |
| [kalliope-IT](https://snowboy.kitt.ai/hotword/10650) | Italiano | Ka-lljo-pe   |
