# Prerequisiti di Kalliope per Raspbian

Kalliope puo essere installato:

- [Via immagine pre-compilata](#installa-tramite-limmagine-del-disco-pre-compilata)
- [Via script](#installa-tramite-script)
- [Manualmente](#installa-manualmente)


## Installa tramite l'immagine del disco pre-compilata

Scarica l'ultima immagine [dalla pagina di rilascio](https://github.com/kalliope-project/kalliope/releases) di Kalliope e caricala come al solito su una scheda SD.

- **Login:** pi
- **Password:** raspberry

Una volta avviato, usare il comando `raspi-config` per espandere il file system e riempire lo spazio disponibile sulla scheda SD.
Il server SSH è abilitato di default. Ottieni l'IP con il comando `ip a` e quindi connettiti tramite il tuo client SSH preferito.

Troverai alcune cartelle denominate "starter_kit_<language>" situate in `/home/pi`. Queste cartelle sono la configurazione di base che ti aiuterà a iniziare con Kalliope.


## Installa tramite script

Basta eseguire il seguente comando bash per installare Kalliope su un Raspberry Pi:
```
bash -c "$(curl -sL https://raw.githubusercontent.com/kalliope-project/kalliope/master/install/rpi_install_kalliope.sh)"
```

## Installa manualmente

> **Nota:** Si raccomanda di utilizzare un'installazione **lite** di Raspbian senza alcuna interfaccia grafica per un'esperienza migliore.

> **Nota:** Il primo Raspberry Pi non è ufficialmente supportato. L'installazione funzionerà ma un singolo core con soli 700Mhz questo potrebbe produrre latenza.

### Pacchetti necessari in Debian

Installa le librerie di sistema e i softwares necessari:

```bash
sudo apt-get update
sudo apt-get install git python-dev libsmpeg0 libttspico-utils libsmpeg0 flac libffi-dev libffi-dev libssl-dev portaudio19-dev build-essential libssl-dev libffi-dev sox libatlas3-base mplayer libyaml-dev libpython2.7-dev libav-tools libjpeg-dev
```

Installare python-pip:
```bash
wget https://bootstrap.pypa.io/get-pip.py
sudo python get-pip.py
```

{!installation/manual_installation_common.md!}

## Configurazione Raspberry Pi

Questa sezione tratta della configurazione necessaria per far funzionare kalliope su un RPi.

### Configurazione del microfono

Ottieni info sull'output con:
```bash
aplay -l
```

Esempio di output con una cuffia USB collegata:
```bash
**** List of PLAYBACK Hardware Devices ****
card 0: ALSA [bcm2835 ALSA], device 0: bcm2835 ALSA [bcm2835 ALSA]
  Subdevices: 7/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 0: ALSA [bcm2835 ALSA], device 1: bcm2835 ALSA [bcm2835 IEC958/HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Headset [Logitech USB Headset], device 0: USB Audio [USB Audio]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
```

Qui vediamo che:

- l'audio analogico (dove è collegato il jack) è su card 0 e device 1
- l'audio USB è su card 1 e device 1


Ottenere info sull'input (microfono):
```bash
arecord -l
```

Esempio di output con una cuffia USB collegata:
```bash
**** List of CAPTURE Hardware Devices ****
card 1: Headset [Logitech USB Headset], device 0: USB Audio [USB Audio]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
```

Qui vediamo vede una periferica su card 1 e device 0

Creiamo quindi un file di configurazione che applichi la seguente configurazione:

- uscita audio (voce di Kalliope) sull'audio analogico (tramite altoparlanti collegati al jack)
- input audio (ciò che viene detto a Kalliope) sul microfono USB

Creiamo un file in `/home/pi/.asoundrc` con il contenuto sottostante
```
pcm.!default {
   type asym
   playback.pcm {
     type plug
     slave.pcm "hw:0,0"
   }
   capture.pcm {
     type plug
     slave.pcm "hw:1,0"
   }
}
```

Dove `playback.pcm` è l'audio in uscita e `capture.pcm` è l'audio in ingresso.

Riavvia ALSA per applicare le modifiche:
```bash
sudo /etc/init.d/alsa-utils restart
```

Regola la sensibilità del microfono eseguendo alsamixer:
```bash
alsamixer
```

Seleziona il microfono premendo F6 e regola il livello di sensibilità del `mic`:
![logo](../images/alsamixer_mic_level.png)

### HDMI / Audio analogico

Per impostazione predefinita, se qualcosa è collegato a questa porta, il flusso audio utilizzerà HDMI.
Controlla la [documentazione ufficiale](https://www.raspberrypi.org/documentation/configuration/audio-config.md) per passare da HDMI ad analogico.

```bash
sudo raspi-config
```

### Configura le tue impostazioni locales (lingua)

Le impostazioni locales definiscono impostazioni specifiche per lingua e paese per i tuoi programmi e la sessione di shell. 
Per impostare le impostazioni internazionali del sistema è necessario utilizzare la variabile di shell. Ad esempio, la variabile LANG può essere utilizzata per impostare la lingua it_IT (italiano). 

Controlla le impostazioni locales in uso:
```
locale
```

Per aggiornare le impostazioni internazionali, digitare il comando seguente:
```
sudo dpkg-reconfigure locales
```

Seleziona nell'elenco il locales del tuo paese, selezionando il codice con UTF8, esempio:

- de_DE.utf8
- it_IT.utf8
- en_GB.utf8
- fr_FR.utf8
- es_ES.utf8

Quindi, aggiorna il tuo file `/home/pi/.bashrc` esportando la lingua. Esempio:
```
export LC_ALL="en_US.UTF-8"
export LANG="en_US.UTF-8"
export LANGUAGE="en_US.UTF-8"
```

Esegui source per applicare le modifiche
```
source /home/pi/.bashrc
```

{!installation/check_env.md!}
