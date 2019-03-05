## Test your env

### Controlla il microfono e la configurazione degli speaker

Per assicurarti di poter registrare la tua voce, esegui il seguente comando per catturare l'input audio dal tuo microfono:
```bash
rec test.wav
```

Premi CTRL-C dopo aver catturato un campione della tua voce.

Quindi riproduci il file audio registrato
```bash
mplayer test.wav
```

La tua installazione è ora completa, diamo ora un'occhiata alla [documentazione introduttiva](../getting-started.md) per imparare come usare Kalliope.

### (Optional) Avviare Kalliope automaticamente dopo un riavvio

Se si vuole avviare automaticamente Kalliope all'avvio poni il seguente script in `/etc/systemd/system/kalliope.service`.

Aggiorna il percorso `<my_config_path>` con il percorso in cui hai inserito i file `brain.yml` e `settings.yml`.

Aggiorna `<username>` con il nome di un utente non root. Ad esempio, su Raspbian puoi impostare `pi`.

```bash
[Unit]
Description=Kalliope

[Service]
WorkingDirectory=<my_config_path>

Environment='STDOUT=/var/log/kalliope.log'
Environment='STDERR=/var/log/kalliope.err.log'
ExecStart=/bin/bash -c "/usr/local/bin/kalliope start > ${STDOUT} 2> ${STDERR}"
User=<username>

[Install]
WantedBy=multi-user.target
```

Es
```bash
[Unit]
Description=Kalliope

[Service]
WorkingDirectory=/home/pi/my_kalliope_config

Environment='STDOUT=/var/log/kalliope.log'
Environment='STDERR=/var/log/kalliope.err.log'
ExecStart=/bin/bash -c "/usr/local/bin/kalliope start > ${STDOUT} 2> ${STDERR}"
User=pi

[Install]
WantedBy=multi-user.target
```

Quindi, ricarica systemctl, avvia il servizio creato e abilitalo all'avvio
```bash
sudo systemctl daemon-reload
sudo systemctl start kalliope
sudo systemctl enable kalliope
```
