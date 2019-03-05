
Questo Player è basato sull'[engine alsa](https://larsimmisch.github.io/pyalsaaudio/libalsaaudio.html)

## Parametri d'input

| Parametro      |Necessario| Default   |Valori possibili| Commento                                                  |
|----------------|----------|-----------|----------------|-----------------------------------------------------------|
| device         | no       | "default" |                | Seleziona il dispositivo da usare per alsa                |
| convert_to_wav | no       | TRUE      | True, False    | Converti il ​​file generato dal TTS in wav prima di leggere |

## Esempio d'impostazioni

Ecco un esempio di configurazione che useresti se il tuo TTS fosse acapela. Poiché questo TTS genera un file MP3, quest'ultimo deve essere convertito in wav.
```yaml
default_player: "pyalsaaudio"

players:
  - pyalsaaudio:
     device: "default"
     convert_to_wav: True
```

## Note

>**Nota:** Definire la scheda predefinita da utilizzare nel parametro device.
Ad esempio, su un Raspberry Pi, la scheda predefinita può essere `sysdefault:CARD=ALSA`

>**Nota:** Questo lettore non gestisce il formato mp3, la conversione da mp3 in wav è necessaria se il engine TTS selezionato genera file mp3.

