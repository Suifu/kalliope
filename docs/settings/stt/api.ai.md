L'STT api.ai si basa sull'[API api.ai](https://api.ai/)

## Parametri d'input

| Parametro |Necessario| Default | Valori possibili                           | Commento            |
|-----------|----------|---------|--------------------------------------------|---------------------|
| key       | SI       | None    |                                            | Informazioni utente |
| language  | NO       | en-US   | [lang](https://docs.api.ai/docs/languages) |                     |

## Esempio d'impostazioni

```yaml
default_speech_to_text: "apiai"

speech_to_text:
  - apiai:
      key: "0cbff154af44944a6"
      language: "en"
```
