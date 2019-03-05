# Prerequisiti di Kalliope per Ubuntu

## Prerequisiti

### Ubuntu 14.04

Installa le librerie di sistema e i softwares necessari:

```bash
sudo apt-get update
sudo apt-get install git python-dev libsmpeg0 libttspico-utils libsmpeg0 flac libffi-dev libffi-dev libssl-dev libjack0 libjack-dev portaudio19-dev build-essential libssl-dev libffi-dev sox libatlas3-base mplayer libav-tools libjpeg-dev
```

Installa la versione di GCC necessaria
```bash
sudo add-apt-repository ppa:ubuntu-toolchain-r/test -y
sudo apt-get update -q
sudo apt-get install gcc-4.9
```

### Ubuntu 16.04

Installa le librerie di sistema e i softwares necessari:

```bash
sudo apt-get update
sudo apt-get install git python-dev libsmpeg0 libttspico-utils libsmpeg0 flac libffi-dev libffi-dev libssl-dev portaudio19-dev build-essential libssl-dev libffi-dev sox libatlas3-base mplayer libav-tools
```

### Ubuntu 18.04

Installa le librerie di sistema e i softwares necessari:

```bash
sudo apt update
sudo apt install git python-dev libsmpeg0 libttspico-utils libsmpeg0 flac dialog libffi-dev libssl-dev portaudio19-dev build-essential libssl-dev sox libatlas3-base mplayer
```

Nota, installare python 3,
```
sudo apt install python3-dev python3-dialog
```

## Installare il python package manager

Installare python-pip
```bash
wget https://bootstrap.pypa.io/get-pip.py
sudo python get-pip.py
```

## Installare Kalliope

{!installation/manual_installation_common.md!}

{!installation/check_env.md!}
