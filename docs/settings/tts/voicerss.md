Questo TTS è basato sull'[engine VoiceRSS](http://www.voicerss.org/). [Documentazione Ufficiale qui](http://www.voicerss.org/api/documentation.aspx)

## Parametri d'input

| Parametro    |Necessario| Default              | Valori possibili                                                                | Commento                                                 |
| ------------ | -------- | -------------------- | ------------------------------------------------------------------------------- | -------------------------------------------------------- |
| language     | SI       |                      | [26 llingue](http://www.voicerss.org/api/documentation.aspx), esempio : "fr-fr" | Le lingue sono identificate dalla stringa LCID           |
| key          | SI       |                      |                                                                                 | registrati nel sito web ufficiale per ottenere la key API|
| rate         | NO       | 0                    | qualunque intero "int"                                                          | Frequenza audio                                          |
| codec        | NO       | 'MP3'                | 'MP3', 'WAV', 'AAC', 'OGG', 'CAF'                                               | Codec audio                                              |
| audio_format | NO       | '44khz_16bit_stereo' | [51 scelte](http://www.voicerss.org/api/documentation.aspx), '8khz_8bit_mono'   | Formati audio                                            |
| ssml         | NO       | False                | True / False                                                                    | True se si desidera usare ssml (solo a pagamento)        |
| base64       | NO       | False                | True / False                                                                    | True se si desidera usare  base64                        |
| ssl          | NO       | False                | True / False                                                                    | True se si desidera usare  ssl                           |
| cache        | NO       | True                 | True / False                                                                    | True se si desidera utilizzare la cache con questo TTS   |

## Esempio d'impostazioni

```yaml
default_text_to_speech: "voicerss"

text_to_speech:
    - voicerss:
        language: "fr-fr"
        key: "API_Key"
```

## Note

limitazioni: 100 KB per richiesta

L'edizione gratuita è limitata a 350 richieste giornaliere.
Possibilità di [aggiornare il piano](http://www.voicerss.org/personel/upgrade.aspx).
