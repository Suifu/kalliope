Questo lettore è basato sull'[engine pyaudio](https://people.csail.mit.edu/hubert/pyaudio/)

## Parametri d'input

| Parametro      |Necessario| Default |Valori possibili| Commento                                                  |
|----------------|----------|---------|----------------|-----------------------------------------------------------|
| convert_to_wav | no       | TRUE    | True, False    | Converti il ​​file generato dal TTS in wav prima di leggere |


## Esempio d'impostazioni

```yaml
default_player: "pyaudioplayer"

players:
  - pyaudioplayer:
     convert_to_wav: True
```


#### Note

>**Nota:** Questo lettore non gestisce il formato mp3, è richiesta la conversione da mp3 in wav.
