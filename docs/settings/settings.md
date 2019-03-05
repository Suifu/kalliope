# settings.yml

Questa parte della documentazione spiega la configurazione principale di Kalliope inserita nel file `settings.yml`.

Kalliope cercherà il file delle impostazioni nell'ordine seguente:

- Dalla cartella corrente, ad es. `/home/pi/my_kalliope/settings.yml`
- Da `/etc/kalliope/settings.yml`
- Di default cerca `settings.yml` nella cartella principale del progetto.

## Configurazione dei trigger

### default_trigger

Il trigger è l'engine che ha il compito di rilevare l'hotword che risveglierà Kalliope.
Alcune hotword comuni sono "Alexa" su Amazon Echo, "OK Google" su alcuni dispositivi Android e "Hey Siri" su iPhone.

Specificare il nome del modulo trigger che si desidera utilizzare.
```yaml
default_trigger: "trigger_name"
```

Per esempio
```yaml
default_trigger: "snowboy"
```

### triggers
Il rilevatore di hotword (detto anche wake word o trigger word) è il motore che ha il compito di svegliare Kalliope.

Ogni trigger ha una propria configurazione. Questa configurazione è passata come argomento seguendo la seguente sintassi
```yaml
triggers:
  - trigger_name:
      parameter_name: "value"
```

Ad esempio, la configurazione predefinita di Snowboy è
```yaml
triggers:
  - snowboy:
      pmdl_file: "trigger/snowboy/resources/model.pmdl"
```

### Esempio d'impostazioni

```yaml
default_trigger: "snowboy"
triggers:
  - snowboy:
      pmdl_file: "trigger/snowboy/resources/model.pmdl"
```

### Trigger disponibili

| Doc                            | Note                                                  |
| ------------------------------ | ----------------------------------------------------- |
| [snowboy](triggers/snowboy.md) | Basato sul [software Snowboy](https://snowboy.kitt.ai/) |

## Configurazione dei Players

Il Players è la libreria/software usato per far parlare Kalliope.
In un progetto Kalliope, puoi impostare qualsiasi lettore audio che desideri utilizzare.

### default_player

Specificare il nome del modulo Players che si desidera utilizzare.
```yaml
default_player: "player_name"
```
Es
```yaml
default_player: "mplayer"
```

### players

Ogni players ha la propria configurazione.
Questa configurazione è passata come argomento seguendo la seguente sintassi
```yaml
players:
  - player_name:
      parameter_name: "value"
```

Quando non sono richiesti parametri, imposta un oggetto vuoto:
```yaml
players:
  - mplayer: {}
```

### Esempio d'impostazioni

```yaml
players:
  - mplayer: {}
  - pyalsaaudio:
     device: "default"
     convert_to_wav: True
  - pyaudioplayer:
     convert_to_wav: True
  - sounddeviceplayer:
     convert_to_wav: True
```

>**Nota:** A volte, i parametri saranno necessari per utilizzare un engine.
Fai clic sul link del Player scelto nella sezione `Current CORE Available Players` per sapere quali parametri sono richiesti.

>**Nota:** Un player che non richiede Parametri d'input deve essere dichiarato con un dict vuoto. Es: ```- player_name: {}```

>**Nota:** I player principali sono inclusi nell'installazione di Kalliope e sono pronti all'uso.

>**Nota:** La maggior parte dei TTS basati su cloud genera un file in formato MP3. Alcuni players non sono in grado di leggere questo formato e quindi è necessaria una conversione in wav.

### Players disponibili

I player principali sono già stati confezionati con Kalliope e possono essere utilizzati sin da subito.

| Doc                                               | Note                                                                                          |
| ------------------------------------------------- | --------------------------------------------------------------------------------------------- |
| [mplayer](players/mplayer.md)                     | Basato sul [software mplayer](http://www.mplayerhq.hu/design7/news.html)                      |
| [pyalsaaudio](players/pyalsaaudio.md)             | Basato sula lib di [pyalsaaudio](https://larsimmisch.github.io/pyalsaaudio/libalsaaudio.html) |
| [pyaudioplayer](players/pyaudioplayer.md)         | Basato sula lib di [pyaudio](https://people.csail.mit.edu/hubert/pyaudio/docs/)               |
| [sounddeviceplayer](players/sounddeviceplayer.md) | Basato sula lib di [sounddevice](https://pypi.python.org/pypi/sounddevice)                    |


## Configurazione della Sintesi Vocale

### default_speech_to_text

Uno Speech To Text(STT) è un engine utilizzato per tradurre ciò che dici in un testo che può essere elaborato dal core di Kalliope.
Per impostazione predefinita, Kalliope utilizza il motore Google STT.

La seguente sintassi viene utilizzata per fornire il nome dell'engine:
```yaml
default_speech_to_text: "stt_name"
```

Es
```yaml
default_speech_to_text: "google"
```

### speech_to_text
Ogni STT ha la propria configurazione. Questa configurazione è passata come argomento che viene mostrato di seguito
```yaml
speech_to_text:
  - stt_name:
      parameter_name: "value"
```

Es:
```yaml
speech_to_text:
  - google:
      language: "fr-FR"
  - bing
```

### Esempio d'impostazioni

```yml
default_speech_to_text: "google"
speech_to_text:
  - google:
      language: "fr-FR"
  - wit:
      key: "MYKEYS"
  - bing:
      key: "MYKEYS"
  - apiai:
      key: "MYKEYS"
      language: "fr"
  - houndify:
      key: "MYKEYS"
      client_id: "MYCLIENTID"

```

### STT disponibili

I principali STTs sono già stati inclusi con l'installazione di Kalliope e sono pronti all'uso.

| Nome                          | Tipo                  |
| ----------------------------- | --------------------- |
| [apiai](stt/api.ai.md)        | Basato su cloud       |
| [Bing](stt/bing.md)           | Basato su cloud       |
| [CMUSphinx](stt/CMUSphinx.md) | Self hosted (Offline) |
| [Google](stt/google.md)       | Basato su cloud       |
| [Houndify](stt/houndify.md)   | Basato su cloud       |
| [wit.ai](stt/wit.ai.md)       | Basato su cloud       |

## Configurazione Sintesi Vocale

### default_text_to_speech
Il Text To Speech è utilizzato per tradurre il testo scritto in un flusso audio.
Per impostazione predefinita, Kalliope utilizza l'engine TTS Pico2wave.

La seguente sintassi viene utilizzata per fornire il nome dell'engine TTS
```yaml
default_text_to_speech: "tts_name"
```

Eg
```yml
default_text_to_speech: "pico2wave"
```

### text_to_speech

Ogni TTS ha la propria configurazione. Questa configurazione è passata come argomento seguendo la seguente sintassi
```yaml
text_to_speech:
  - tts_name:
      parameter_name: "value"
```

Es
```yaml
text_to_speech:
  - pico2wave:
      language: "fr-FR"
  - googletts:
      language: "fr"
```

### cache_path

Gli engines TTS funzionano tutti allo stesso modo, gli diamo un testo, restituiscono un file audio e riproducono il file audio. Il file audio generato viene inserito nella cache fino a quando non
viene riprodotto dal lettore audio. Prima di generare un nuovo file audio, Kalliope darà un'occhiata alla cache per caricarla direttamente senza dover chiamare il
motore TSS se il file è gia stato generato in precedenza.

È necessario impostare, nel tag `cache_path`, un percorso in cui la cache verrà salvata. Di default il percorso è /tmp.
```yml
cache_path: "/tmp/kalliope_tts_cache"
```

>**Nota:** Il percorso deve essere valido e l'utente deve averne i permessi di lettura e scrittura.

>**Nota:** Lo spazio occupato aumenta notevolmente a causa della cache. Si consiglia di impostare un neurone che cancelli automaticamente i file audio
generati che non verrano più riprodotti.

### Esempio d'impostazioni

```yaml
default_text_to_speech: "voicerss"

cache_path: "/tmp/kalliope_tts_cache"

text_to_speech:
  - pico2wave:
      language: "fr-FR"
      cache: True
  - acapela:
      language: "sonid15"
      voice: "Manon"
      cache: False
  - googletts:
      language: "fr"
  - voicerss:
      language: "fr-fr"
      cache: True
```

### TTS disponibili

I principali TTS sono già inclusi nell'installazione di Kalliope e possono essere utilizzati immediatamente.

| Name                          | Tipo                  |
| ----------------------------- | --------------------- |
| [espeak](tts/espeak.md)       | Self hosted (Offline) |
| [googletts](tts/googletts.md) | Basato su cloud       |
| [marytts](tts/marytts.md)     | Self hosted (Offline) |
| [pico2wave](tts/pico2wave.md) | Self hosted (Offline) |
| [voicerss](tts/voicerss.md)   | Basato su cloud       |
| [watson](tts/watson.md)       | Basato su cloud       |


## Hooks

L'Hooking consente di associare le azioni agli eventi in base al lifecycle di Kalliope.
Ad esempio, è utile sapere quando Kalliope ha rilevato l'hotword dal trigger engine e farle pronunciare ad alta voce che è pronta ad ascoltare il tuo ordine.

Per utilizzare un hook, collega il nome dell'hook a una sinapsi (o un elenco di sinapsi) esistenti nel tuo brain.

Sintassi:
```yaml
hooks:
  hook_name1: synapse_name
  hook_name2:
    - synapse_name_1
    - synapse_name_2
```

Es.
```yaml
hooks:
  on_start: "on-start-synapse"
```

Elenco degli hook disponibili

| Nome dell'hook         | Descrizione                                                            |
| ---------------------- | ---------------------------------------------------------------------- |
| on_start               | Quando viene avviato kalliope. Questo hook si attiva una sola volta    |
| on_waiting_for_trigger | Quando Kalliope attende il rilevamento di hotword                      |
| on_triggered           | Quando è stata rilevata l'hotword                                      |
| on_start_listening     | Quando il motore di sintesi vocale è in ascolto di un ordine           |
| on_stop_listening      | Quando il motore di sintesi vocale interrompe l'attesa di un ordine    |
| on_order_found         | Quando l'ordine pronunciato è stato trovato nel brain                  |
| on_order_not_found     | Quando l'ordine pronunciato non è stato trovato nel brain              |
| on_processed_synapses  | Quando tutti i neuroni nelle sinapsi sono stati elaborati              |
| on_deaf                | Quando Kalliope passa da non udente a udente                           |
| on_undeaf              | Quando Kalliope passa da udente a non udente                           |
| on_mute                | Quando Kalliope passa da non muto a muto                               |
| on_unmute              | Quando Kalliope passa da muto a non muto                               |
| on_start_speaking      | uando Kalliope inizia a parlare attraverso il motore di sintesi vocale |
| on_stop_speaking       | Quando Kalliope smette di parlare                                      |
| on_stt_error           | Quando avviane un errore durante l'elaborazione dell'STT               |

### Esempio d'impostazioni

Esempio: vuoi sentire una risposta casuale quando è rilevata l'hotword

**settings.yml**
```yaml
hooks:
  on_triggered: "on-triggered-synapse"
```

**brain.yml**
```yaml
- name: "on-triggered-synapse"
  signals: []
  neurons:
    - say:
        message:
          - "yes sir?"
          - "I'm listening"
          - "I'm listening to you"
          - "sir?"
          - "what can i do for you?"
          - "Speaking"
          - "how can i help you?"
```

Esempio: vuoi sapere che il tuo ordine non è stato trovato

**settings.yml**
```yaml
hooks:
  on_order_not_found: "order-not-found-synapse"
```

**brain.yml**
```yaml
- name: "order-not-found-synapse"
    signals: []
    neurons:
      - say:
          message:
            - "I haven't understood"
            - "I don't know this order"
            - "Please renew your order"
            - "Would you please reword your order"
            - "Can ou please reformulate your order"
            - "I don't recognize that order"
```

Esempio: stai usando Kalliope su un Rpi. Hai realizzato uno script che attiva o disattiva un led.
Puoi chiamare questo script ogni volta che kalliope inizia o smette di parlare

**settings.yaml**
```yaml
hooks:
  on_start_speaking: "turn-on-led"
  on_stop_speaking: "turn-off-led"
```

**brain.yml**
```yaml
- name: "turn-on-led"
  signals: []
  neurons:
    - script:
        path: "/path/to/script.sh on"

- name: "turn-off-led"
  signals: []
  neurons:
    - script:
        path: "/path/to/script.sh off"
```

>**Nota:** non è possibile utilizzare un neurotrasmettitore all'interno di una sinapsi chiamata da un hook.
Non puoi usare il neurone "say" all'interno di "on_start_speaking" o "on_stop_speaking" o creerà un loop infinito

## Rest API

È possibile attivare una Rest API per:

- Elencare le sinapsi
- Ottenere i dettagli delle sinapsi
- Eseguire una sinapsi
- Aggiornare le impostazioni
- Aggiornare il brain

Per la lista completa delle API vedi la [documentazione REST API](../rest_api.md)

Esempi di impostazioni:
```yml
rest_api:
  active: True
  port: 5000
  password_protected: True
  login: admin
  password: secret
  allowed_cors_origin: "*"
```

| Parametro           | Tipo     | Commento                                                                                                   |
| ------------------- | -------- | ---------------------------------------------------------------------------------------------------------- |
| active              | booleano | Per abilitare il server rest api                                                                           |
| port                | intero   | La porta in ascolto del server web. Deve essere un numero intero compreso tra 1024-65535                   |
| password_protected  | booleano | Se `True`, l'intera API sarà protetta da password                                                          |
| login               | stringa  | Accesso protetto dall'autenticazione HTTP di base. Deve essere fornito se `password_protected` è `True`    |
| password            | stringa  | Password utilizzata dall'autenticazione HTTP di base. Deve essere fornito se `password_protected` è `True` |
| allowed_cors_origin | stringa  | Consenti richiesta da applicazione esterna. Vedi gli esempi qui sotto                                      |

**Richieste Cors**

Se si desidera consentire le richieste da un'applicazione esterna, è necessario abilitare le impostazioni delle richieste CORS definendo le origini autorizzate.
Per fare ciò, basta indicare l'origine a cui è consentito sfruttare l'API. I valori autorizzati sono:

False per vietare la richiesta CORS.
```yml
allowed_cors_origin: False
```

o anche una stringa o un elenco
```yml
allowed_cors_origin: "*"
```
(in caso di "*", tutte le origini sono accettate).
or
```yml
allowed_cors_origin:
  - 'http://mydomain.com/*'
  - 'http://localhost:4200/*'
```

Ricorda che un'origine è composta dallo schema (http(s)), dalla porta (eg: 80, 4200,…) e dal dominio (mydomain.com, localhost).

## Directory delle risorse

La directory delle risorse è il percorso in cui Kalliope proverà a caricare moduli della community come Neuroni, STT o TTS.
È necessario impostare un percorso valido se si desidera installare dei "community neuron". Il percorso può essere relativo o assoluto.

```yml
resource_directory:
  resource_name: "path"
```

Es
```yml
resource_directory:
  neuron: "resources/neurons"
  stt: "resources/stt"
  tts: "resources/tts"
  trigger: "/full/path/to/trigger"
```

## Variabili globali

I percorsi delle Variabili Globali elencano dove caricare le suddette.
Queste variabili possono essere riutilizzate nei parametri dei neuroni dentro parentesi doppie.

Es
```yml
var_files:
  - variables.yml
  - variables2.yml
```
> **Nota:** Se una variabile è definita in file diversi, l'ultimo file definisce il valore.

Nei file le variabili sono definite da key/value:
```yml
variable: 60
baseURL: "http://blabla.com/"
password: "secret"
```

E cosi si usano nei tuoi neurons:
```yml
  - name: "run-simple-sleep"
    signals:
      - order: "Wait for me "
    neurons:
      - uri:
          url: "{{baseURL}}get/1"
          user: "admin"
          password: "{{password}}"
```

> **Nota:** Poiché il formato YAML non consente doppie parentesi non circondate da virgolette: è necessario utilizzare la variabile tra virgolette.

Una variabile globale può essere un dizionario. Esempio:
```yml
contacts:
  nico: "1234"
  tibo: "5678"
```

E una sinapsi che usa questo dizionario:
```yml
- name: "test-var"
  signals:
    - order: "give me the number of {{ contact_to_search }}"
  neurons:
    - say:
        message:
        - "the number is {{ contacts[contact_to_search] }}"
```

## Opzioni

Opzioni che possono essere definite per Kalliope.

Esempio di configurazione
```yaml
options:
  mute: True
  deaf: False
```

Opzioni disponibili:

| Opzione                         | Descrizione                                                                                          |
| ------------------------------- | ---------------------------------------------------------------------------------------------------- |
| mute                            | Quando è muto, l'STT engine non sarà usato per far parlare Kalliope durante l'esecuzione dei neuroni |
| deaf                            | Quando è sordo, il trigger engine non viene avviato. Kalliope non aspetterà la wake up word          |
| energy_threshold                | [energy_threshold](#energy_threshold)                                                                |
| adjust_for_ambient_noise_second | [adjust_for_ambient_noise_second](#adjust_for_ambient_noise_second)                                  |
| stt_timeout                     | Numero di secondi prima di interrompere automaticamente l'esecuzione dell'STT                        |


### energy_threshold

Rappresenta la soglia del rumore ambientale. Di default è impostato su **4000**.
I valori al di sotto di questa soglia sono considerati silenzio e i valori superiori a questa soglia sono considerati voce.
Questo viene regolato automaticamente se le soglie dinamiche sono abilitate con il parametro `adjust_for_ambient_noise_second`.

Questa soglia è associata al volume percepito del suono, ma è una relazione non lineare.
La soglia di energia effettiva necessaria dipende dalla sensibilità del microfono o dai dati audio
I valori tipici per una stanza silenziosa sono compresi tra 0 e 100 e i valori tipici per la conversazione sono compresi tra 150 e 3500.
Il rumore ambientale (non parlato) ha un impatto significativo su quali valori funzioneranno meglio.

Se hai problemi con il riconoscimento che cerca di riconoscere le parole anche quando non parli, prova a modificarlo con un valore più alto.
Se hai problemi di non riconoscimento delle tue parole mentre parli, prova a modificarlo con un valore più basso.
Ad esempio, un microfono sensibile o un microfono in stanze più rumorose potrebbe avere un livello di energia ambientale maggiore di 4000.
```yml
options:
  energy_threshold: 4000
```

>**Nota:** Il valore predefinito, se non impostato, è 4000

### adjust_for_ambient_noise_second

Se definito, calibra la soglia in modo dinamico acquisendo il rumore ambientale della stanza per la durata in secondi impostata nel parametro.
Quando è impostato, il parametro `energy_threshold` viene sovrascritto dal valore restituito dalla calibrazione del rumore.
Questo valore dovrebbe essere almeno 0,5 per ottenere un campione rappresentativo del rumore ambientale.

```yml
options:
  adjust_for_ambient_noise_second: 1
```

>**Nota:** Il numero di secondi qui rappresenta il tempo tra il risveglio di Kalliope e il momento in cui puoi darle il tuo ordine.


## send_anonymous_usage_stats

Questo flag consente a Kalliope di inviare alcune statistiche per valutare in modo anonimo l'utilizzo globale dell'app Kalliope da parte degli utenti.

Syntax:
```yml
send_anonymous_usage_stats: <boolean>
```

Es:
```yml
send_anonymous_usage_stats: False
```
