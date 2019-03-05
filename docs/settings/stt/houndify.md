Questo STT è basato sull'engine [Houndify](https://www.houndify.com/) .

Questo STT supporta solo l'inglese.

## Parametri d'input

| Parametro |Necessario| Default |Valori possibili| Commento          |
|:---------:|----------|---------|----------------|-------------------|
| key       | Yes      | None    |                |Informazioni utente|
| client_id | Yes      | None    |                |Informazioni utente|

## Esempio d'impostazioni

```yaml
default_speech_to_text: "houndify"

speech_to_text:
  - houndify:
      key: "my_user_key"
      client_id: "my_user_client_id"
```
