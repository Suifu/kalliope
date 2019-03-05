L'STT di Google è basato sull'[API Google Speech Recognition](https://cloud.google.com/speech/).
Questo STT è gratuito per meno di 60 minuti di utilizzo al mese. Dopo ciò hai bisogno di un abbonamento.

## Parametri d'input

| Parametro |Necessario| Default |Valori possibili                                                               | Commento   |
|-----------|----------|---------|-------------------------------------------------------------------------------|------------|
| key       | No       | None    |                                                                               |            |
| language  | No       | en-US   | [lang](https://en.wikipedia.org/wiki/Google_Voice_Search#Supported_languages) |stringa LCID|


## Esempio d'impostazioni

Utilizzo gratuito
```yaml
default_speech_to_text: "google"

speech_to_text:
  - google:
      language: "fr-FR"
```

Per gli utenti paganti
```yaml
default_speech_to_text: "google"

speech_to_text:
  - google:
      language: "fr-FR"
      key: "my_google_stt_key"
```
