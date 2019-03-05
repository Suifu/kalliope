Questo lettore è basato sull'[engines sounddevice e soundfile](https://pypi.python.org/pypi/sounddevice)

## Parametri d'input

| Parametro      |Necessario| Default |Valori possibili| Commento                                                  |
|----------------|----------|---------|----------------|-----------------------------------------------------------|
| convert_to_wav | no       | TRUE    | True, False    | Converti il ​​file generato dal TTS in wav prima di leggere |


## Esempio d'impostazioni

```yaml
default_player: "sounddeviceplayer"

players:
  - sounddeviceplayer:
     convert_to_wav: True
```

## Note

>**Nota:** Questo lettore non gestisce il formato mp3, è richiesta la conversione da mp3 in wav.

