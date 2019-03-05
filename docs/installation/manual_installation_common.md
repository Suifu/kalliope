
### Metodo 1 - Installare usando il package per PIP 

Tu puoi installare kalliope nel tuo sistema usando PIP:
```bash
sudo pip install kalliope
```

### Metodd 2 - Installazione manuale usando i sorgenti

Clonare il progetto:
```bash
git clone https://github.com/kalliope-project/kalliope.git
cd kalliope
```

Installare il progetto:
```bash
sudo python setup.py install
```

### Metodo 3 - Per sviluppatori, Installazione usando Virtualenv

Installare il pacchetto `python-virtualenv`:
```bash
sudo apt-get install python-virtualenv
```

Clonare il progetto:
```bash
git clone https://github.com/kalliope-project/kalliope.git
cd kalliope
```

Generare un environment locale per python :
```bash
virtualenv venv
```

Installare il progetto usando l'environment appena creato:
```bash
venv/bin/pip install --editable .
```

Attivare l'environment locale:
```bash
source venv/bin/activate
```

### Metodo 4 - Per sviluppatori, installare solo le dipendenze

Clonare il progetto:
```bash
git clone https://github.com/kalliope-project/kalliope.git
cd kalliope
```

Installare direttamente le dependenze python:
```bash
sudo pip install -r install/files/python_requirements.txt
```
