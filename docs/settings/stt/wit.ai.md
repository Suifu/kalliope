La wit STT è basata sull'[API Wit.ai](https://wit.ai/)

## Parametri d'input

| Parametro |Necessario| Default |Valori possibili| Commento          |
|:---------:|----------|---------|----------------|-------------------|
| key       | Yes      | None    |                |Informazioni utente|

## Esempio d'impostazioni

```yaml
default_speech_to_text: "wit"

speech_to_text:
  - wit:
      key: "my_user_key"
```
