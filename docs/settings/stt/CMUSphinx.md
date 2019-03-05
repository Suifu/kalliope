Questo modulo è una soluzione STT auto-ospitata (offline) basata sull'[engine CMUSPhinx](http://cmusphinx.sourceforge.net/wiki/).
Di base, è disponibile solo la lingua inglese. È possibile scaricare [altre lingue](https://sourceforge.net/projects/cmusphinx/files/Acoustic%20and%20Language%20Models/) dal repository principale e installarle seguendo [la documentazione ufficiale](http://cmusphinx.sourceforge.net/wiki/tutoriallm).

## Installazione

Installa i pacchetti
```bash
sudo apt-get install swig libpulse-dev
```

Quindi installa la lib per python
```bash
sudo pip install pocketsphinx
```

## Parametri d'input

| Parametro       |Necessario|  Tipo   | Default |Valori possibili| Commento                                                                                                                                      |
| --------------- | -------- | ------- | ------- |----------------| --------------------------------------------------------------------------------------------------------------------------------------------- |
| language        | no       | stringa | en-US   |                | [Installare altre lingue](https://github.com/Uberi/speech_recognition/blob/master/reference/pocketsphinx.rst#installing-other-languages)      |
| keyword_entries | no       | elenco  |         |                | Elenco di tuple nella forma (keyword, sensitivity), dove keyword è una frase e sensitivity è la sensibilità al riconoscimento di questa frase |
| grammar_file    | no       | stringa |         |                | Percorso file grammaticali FSG o JSGF. Nota: se vengono passati `keyword_entries`, `grammar_file` verrà ignorato                              |


## Esempio d'impostazioni

```yaml
default_speech_to_text: "cmusphinx"

speech_to_text:
  - cmusphinx:
      language: "en-US"
```

## Usare le parole chiave

Sphinx di solito opera in 'transcription mode' e restituirà tutte le parole che riconosce.
L'aggiunta di `keyword_entries` alle impostazioni restringe il suo spazio di ricerca ed è più accurata della semplice ricerca di quelle stesse parole chiave nelle trascrizioni non basate su parole chiave, perché Sphinx sa esattamente quali suoni cercare.
Il parametro `keyword_entries` prevede un elenco di tuple composto da una frase e un livello di sensibilità che definiscono la sensibilità di questa frase al riconoscitore, su una scala da 0 (molto insensibile, più falsi negativi) a 1 (molto sensibile, più falsi positivi).
```yaml
default_speech_to_text: "cmusphinx"

speech_to_text:
  - cmusphinx:
      language: "en-US"
      keyword_entries:
        - ["hello", 0.8]
        - ["stop the music", 0.6]
```
