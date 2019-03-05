# Prerequisiti di Kalliope per Debian Jessie/Stretch

## Pacchetti necessari in Debian

Aprire `/etc/apt/sources.list` e controllare di avere `contrib` e `non-free` abilitati:

In Debian Jessie:
```bash
deb http://httpredir.debian.org/debian jessie main contrib non-free
deb-src http://httpredir.debian.org/debian jessie main contrib non-free
```

In Debian Stretch:
```bash
deb http://httpredir.debian.org/debian stretch main contrib non-free
deb-src http://httpredir.debian.org/debian stretch main contrib non-free
```

Installa le librerie di sistema e i softwares necessari:

```bash
sudo apt-get update
sudo apt-get install git python-dev libsmpeg0 libttspico-utils libsmpeg0 flac libffi-dev libffi-dev libssl-dev portaudio19-dev build-essential libssl-dev libffi-dev sox libatlas3-base mplayer libav-tools libjpeg-dev
```

Andiamo a installare l'ultima versone di python-pip
```bash
wget https://bootstrap.pypa.io/get-pip.py
sudo python get-pip.py
```

Ora, con pip, l'ultima release di setuptools
```bash
sudo pip install -U setuptools
```
## Installare Kalliope

{!installation/manual_installation_common.md!}

{!installation/check_env.md!}
