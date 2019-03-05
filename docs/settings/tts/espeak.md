Questo TTS è basato sull'[engine eSpeak](http://espeak.sourceforge.net/).

## Parametri d'input

| Parametro  |Necessario| Default         | Valori possibili         | Commento                                                           |
| ---------- | -------- | --------------- | ------------------------ | ------------------------------------------------------------------ |
| voice      | si       |                 | tutte le voci installate | guarda l'elenco completo con il comando "espeak --voices=LANGUAGE" |
| variant    | no       |                 |tutte le lingue installate| guarda l'elenco completo con il comando "espeak --voices=variant"  |
| speed      | no       | 160             | 80 to 450                | Velocità in parole per minuto                                      |
| amplitude  | no       | 100             |  0 to 200                | Ampiezza                                                           |
| pitch      | no       | 50              |  0 to  99                | Regolazione del pitc                                               |
| path       | no       | /usr/bin/espeak |  0 to  99                | Percorso di espeak                                                 |
| cache      | no       | TRUE            |                          | True se si desidera utilizzare la cache con questo TTS             |

## Installazione

Espeak deve essere installato con:
```bash
sudo apt-get install espeak
```

Per vedere l'elenco completo di lingue e voci:
```bash
espeak --voices
```

Per vedere l'elenco completo delle voci:
```bash
espeak --voices=LANGUAGE
```

Esempio:
```
espeak --voices=fr
Pty Language Age/Gender VoiceName          File          Other Languages
 5  fr-fr          M  french               fr            (fr 5)
 7  fr             M  french-mbrola-1      mb/mb-fr1
 7  fr             F  french-mbrola-4      mb/mb-fr4
 5  fr-be          M  french-Belgium       europe/fr-be  (fr 8)
```

Configurazione per "7  fr             M  french-mbrola-1      mb/mb-fr1"
```yaml
voice: "mb-fr1"
```

Per vedere l'elenco completo delle varianti:
```bash
espeak --voices=variant
```

Esempio:
```
espeak --voices=variant
Pty Language Age/Gender VoiceName          File          Other Languages
 5  variant        F  female2              !v/f2
 5  variant        F  female3              !v/f3
 5  variant        F  female4              !v/f4
 5  variant        F  female5              !v/f5
 5  variant        F  female_whisper       !v/whisperf
 5  variant        -  klatt                !v/klatt
 5  variant        -  klatt2               !v/klatt2
 [...]
```

Configurazione per "5  variant        F  female3              !v/f3".
```yaml
voice: "fr"
variant: "f3"
```

## Esempio d'impostazioni

```yaml
default_text_to_speech: "espeak"

text_to_speech:
    - espeak:
        voice: "fr"
        variant: "f3"
```

