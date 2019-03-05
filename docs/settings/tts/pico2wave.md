Questo TTS è basato sull'engine SVOX picoTTS

## Parametri d'input

| Parametro  |Necessario| Default            |Valori possibili| Commento                                                                                                                                                        |
| ---------- | -------- | ------------------ | -------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| language   | si       |                    | 6 lingue       | Elenco delle lingue supportate nella sezione Note                                                                                                               |
| cache      | no       | TRUE               | True,  False   | True se si desidera utilizzare la cache con questo TTS                                                                                                          |
| samplerate | no       |                    | int            | Pico2wave crea file da 16 khz ma non tutti i dispositivi USB supportano questo. Impostare un valore da convertire in un samplerate specifico. Ad esempio: 44100 |
| path       | no       | /usr/bin/pico2wave |                | Percorso di Pico2wave. Se non impostato, Kalliope proverà a caricarlo dall'environment                                                                          |

## Esempio d'impostazioni

```yaml
default_text_to_speech: "pico2wave"

text_to_speech:
    - pico2wave:
        language: "fr-FR"
        cache: True
```

## Note

Lingue supportate:

- Inglese en-US
- Inglese en-GB
- Francese fr-FR
- Spagnolo es-ES
- Tedesco de-DE
- Italiano it-IT
