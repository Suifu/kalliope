L'STT Bing è basato sull'[API Microsoft Recognition Voice di Bing](https://www.microsoft.com/cognitive-services/en-us/speech-api)

## Parametri d'input

| Parametro |Necessario| Default | Valori possibili                                                      | Commento            |
|-----------|----------|---------|-----------------------------------------------------------------------|---------------------|
| key       | SI       | None    |                                                                       | Informazioni utente |
| language  | No       | en-US   | [lang](https://www.microsoft.com/cognitive-services/en-us/speech-api) | 7 languages         |

## Esempio d'impostazioni

```yaml
default_speech_to_text: "bing"

speech_to_text:
  - bing:
      key: "9e48ddaf75904838bedc11aea6b36fb0"
      language: "en-US"
```
