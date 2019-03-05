# Iniziare con Kalliope

Kalliope ha bisogno di due file per funzionare, un settings.yml e un brain.yml. Poiché i file sono scritti con sintassi YAML, ti consigliamo vivamente di utilizzare un editor (IDE) come  [VS Code](https://code.visualstudio.com/) o [Atom](https://atom.io/).

Se stai usando kalliope da un Rpi, l'idea sarebbe quella di configurare il tuo assistente dal tuo computer con un IDE e poi inviare la configurazione al tuo RPI.

Quando avvii kalliope usando la CLI (`kalliope start`), il programma proverà a caricare settings.yml e brain.yml nel seguente ordine:

- Dalla tua cartella corrente, Es `/home/pi/my_kalliope/`
- Da `/etc/kalliope/`
- Dal `settings.yml` e `brain.yml` di default che si trovano nel root del progetto Kalliope.

Questo è l'albero di default della cartella di configurazione di Kalliope:
```
kalliope_config/
├── brains
│   └── included_brain.yml
├── brain.yml
├── files
│   └── kalliope-EN-13samples.pmdl
└── settings.yml
```

Abbiamo creato uno starter kits che deve solo essere clonato, inserito nell'RPI e lanciato. Troverai l'intero elenco di start kits disponibili sul [sito web di Kalliope](https://kalliope-project.github.io/starter_kit.html).
Questi repository forniscono una struttura per iniziare a imparare le basi di Kalliope.
Scarica il kit di partenza a tua scelta e apri la cartella con il tuo IDE.

Tutti i file sono espressi in formato YAML (vedi [Sintassi YAML](https://learnxinyminutes.com/docs/yaml/)) e hanno un minimo di sintassi, che tenta intenzionalmente di non essere un linguaggio o uno script di programmazione,
ma piuttosto un modello di una configurazione o di un processo.

Apriamo il file principale dello starter kit Italiano. Vedrai che ci sono alcuni file di sub brains inclusi.
```yaml
- includes:
    - brains/say.yml
```

Se apri il file `say.yml` dalla cartella brains, vedrai una **synapse** di base che usa il [neuron](brain/brain.md#neurons) "[Say](brain/neurons/say)" e fa parlare Kalliope ad alta voce "Ciao signore" quando dici "hello".
```yaml
- name: "say-hello-en"
  signals:
    - order: "Hello"
  neurons:
    - say:
        message: "Hello sir"
```

Dividiamo il tutto in sezioni in modo che possiamo capire come viene costruito il file e cosa significa ogni parte.

I pezzi che iniziano con ```-``` sono considerati come elementi di questo elenco. I pezzi hanno il formato ```key: value``` il cui il valore può essere una semplice stringa o una sequenza di altri sotto elementi.

Al livello più alto abbiamo un tag "name". Questo è **l'identificatore univoco** della sinapsi. Deve essere univoca e accetta unicamente i caratteri alfanumerici e trattino. ([a - zA - Z0 - 9\-])
```yaml
- name: "Say-hello"
```

La prima parte, denominata **signals** è una lista di azioni di input.
Puoi aggiungere quante azioni vuoi nella sezione "signals". Se uno di questi viene attivato, la lista dei neuroni verrà eseguita.
```yaml
signals:
  - order: "say-hello"
```

Nell'esempio seguente, usiamo solo una azione, un "order", ma può anche essere:

- **an order:** Qualcosa che è stato pronunciato ad alta voce dall'utente.
- **an event:** Una data o una azione ripetuta (EG: ripetere ogni mattina alle 8:30)
- **a mqtt message** Un messaggio ricevuto su un argomento MQTT
- **a geolocation** Dalla posizione del tuo smartphone
- **a community signal** Es: Usando una GPIO consente di attivare azioni da un pulsante
- **No signal**. La sinapsi può essere chiamata solo da un'altra sinapsi o dall'API

Vediamo ora le dichiarazioni dei **neurons**. I neuroni sono moduli che verranno eseguiti quando l'azione di input(signal) viene attivata. È possibile definire quanti neuroni si desidera per la stessa azione di input (ad esempio: dire qualcosa, quindi fare qualcosa ecc ...). Questa contiene un elenco (perché inizia con un "-") di neurons
```yaml
neurons:
  - neuron_1_name
  - neuron_2_name
  - another_neuron
```

L'ordine di esecuzione dei neuroni è definito dall'ordine in cui sono elencati nella dichiarazione dei neurons.

Alcuni neuroni hanno bisogno di parametri che possono essere passati come argomenti seguendo la seguente sintassi:
```yaml
neurons:
  - neuron_name:
      parameter1: "value1"
      parameter2: "value2"
```
Nota che i parametri necessitano di una tabulazione sotto il nome del neurone (requisito di sintassi YAML).

In questo esempio, il neurone chiamato "say" farà sì che Kalliope pronunci ad alta voce la frase nel parametro **message**.

I neuroni possono essere Core (installati di default) o community based (devono essere installati).

È ora di avviare Kalliope. Spostati nella cartella e avvia Kalliope:
```bash
cd /path/to/the/starter_kit
kalliope start
```
> **Nota:** Non avviare Kalliope come utente root o con sudo

Kalliope caricherà le settings e il brain, l'output dovrebbe apparire come segue
```bash
Starting event manager
Events loaded
Starting Kalliope
Press Ctrl+C for stopping
Starting REST API Listening port: 5000
Waiting for trigger detection
```

Ora pronuncia l'hotwork ad alta voce e vedrai che Kalliope (con la pronuncia corretta a seconda del tuo starter kit. "Kalliopé" in Francese, "Kalliopee" in Inglese, etc..).
Se pronunciato correttamente, vedrai "say something" nella console.
```bash
Say something!
```

Quindi potrai dire "hello" e ascoltare la risposta di Kalliope.
```bash
Say something!
Google Speech Recognition thinks you said hello
Order matched in the brain. Running synapse "say-hello"
Waiting for trigger detection
```

Questo è tutto! Sei pronto per personalizzare il tuo assistente!
