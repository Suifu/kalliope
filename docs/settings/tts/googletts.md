
Questo TTS è basato sul [Google translate engine](http://translate.google.com/)

## Parametri d'input

| Parametro  |Necessario| Default | Valori possibili                                                              | Commento                                                                                                        |
| ---------- | -------- | ------- | ----------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------- |
| language   | YES      |         | [103 lingue](http://translate.google.com/about/intl/en_ALL/languages.html)    | Le lingue sono identificate con i loro codici ISO_639-1 (https://en.wikipedia.org/wiki/List_of_ISO_639-1_codes) |
| cache      | No       | TRUE    | True / False                                                                  | True se si desidera utilizzare la cache con questo TTS                                                          |

## Esempio d'impostazioni

```yaml
default_text_to_speech: "googletts"

text_to_speech:
    - googletts:
        language: "fr"
```
