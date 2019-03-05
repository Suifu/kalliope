MaryTTS è una piattaforma open-source di sintesi vocale multilingue scritta in Java.

## Parametri d'input

| Parametro  |Necessario| Default   | Valori possibili                  | Commento                                                            |
| ---------- | -------- | --------- | --------------------------------- | ------------------------------------------------------------------- |
| voice      | si       | None      | es. bits1, cmu-bdl, enst-camille  | Esegui "./marytts list" per controllare le voci installate          |
| locale     | si       | None      | es. de, en_US, fr                 | Controlla "http://localhost:59125/locales" per le lingue installate |
| host       | no       | localhost |                                   | Indirizzo host del tuo server MaryTTS                               |
| port       | no       | 59125     |                                   | Porta del tuo server MaryTTS                                        |

## Esempio d'impostazioni

Per la voce inglese su localhost aggiungi le seguenti righe nel tuo settings.yml:
```
text_to_speech:
  - marytts:
      voice: "cmu-bdl"
      locale: "en_US"
      cache: True
```

Per voce inglese su host remoto con porta predefinita:
```
text_to_speech:
  - marytts:
      voice: "cmu-bdl"
      locale: "en_US"
      host: 192.168.0.25
      cache: True
```
## Note :

>**Nota:** E' necessario [installare il server Marytts](https://github.com/marytts/marytts-installer).
