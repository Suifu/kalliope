**Questa e' solo una traduzione della wiki per il codice aggiornato [fai riferimento all'originale](https://github.com/kalliope-project/kalliope)**

<p align="center">
    <img src="docs/images/Kalliope_logo_large.png">
</p>

# Kalliope
[![Build Status](https://travis-ci.org/kalliope-project/kalliope.svg?branch=master)](https://travis-ci.org/kalliope-project/kalliope)
[![Coverage Status](https://coveralls.io/repos/github/kalliope-project/kalliope/badge.svg)](https://coveralls.io/github/kalliope-project/kalliope)
[![Gitter](https://badges.gitter.im/gitterHQ/gitter.svg)](https://gitter.im/kalliope-project/Lobby)
[![PyPI version](https://badge.fury.io/py/kalliope.svg)](https://badge.fury.io/py/kalliope)
[![PyPI](https://img.shields.io/pypi/pyversions/kalliope.svg)](https://pypi.python.org/pypi/kalliope/)
[![Beerpay](https://beerpay.io/kalliope-project/kalliope/badge.svg?style=flat)](https://beerpay.io/kalliope-project/kalliope)

Kalliope è un framework che ti aiuterà a creare il tuo assistente personale.

Il concetto è quello di creare il [cervello](brain/brain.md) del tuo assistente collegando un **signal** di input (ordine vocale, evento programmato, messaggio MQTT, evento GPIO, etc..) a una o più azioni chiamate **neurons**.

Puoi creare il tuo bot Kalliope, semplicemente scegliendo e componendo con i [neuroni esistenti](https://kalliope-project.github.io/neurons_marketplace.html) senza scrivere alcun codice. Ma se hai bisogno di un modulo particolare, puoi scriverlo da solo, aggiungerlo al tuo progetto e proporlo alla comunità.

Kalliope può funzionare su tutte le distribuzioni Linux basate su Debian incluso Raspberry Pi ed è multi-lingua. L'unica cosa di cui hai bisogno è un microfono.

Kalliope è facile da usare, guarda quest'hello world

```yaml
  - name: "Hello-world"
    signals:
      - order: "say hello"
    neurons:
      - say:
          message: "Hello world!"
```

Se vuoi un'idea di ciò che puoi fare con Kalliope, premi l'immagine di seguito in inglese
[![ENGLISH DEMO](https://img.youtube.com/vi/PcLzo4H18S4/0.jpg)](https://www.youtube.com/watch?v=PcLzo4H18S4)

## Links

- [Documentazione](https://kalliope-project.github.io/kalliope/)
- [Website di Kalliope](https://kalliope-project.github.io/)
- [Android app](https://play.google.com/store/apps/details?id=kalliope.project)
- [Chat](https://gitter.im/kalliope-project/Lobby)

<p align="center">
    <img src="docs/images/kalliope_app.png">
</p>

## Credits

> **Significato di Kalliope** Kalliope significa "voce bella" dal Greco καλλος (kallos) "bella" and οψ (ops) "voce".
Nella mitologia greca era una delle nove Muse, dea della poesia epica e dell'eloquenza.

- kə-LIE-ə-pee    (English)
- Ka-li-o-pé      (French)
- каллиопа        (Russian)

## License

Copyright (c) 2018. All rights reserved.

Kalliope is covered by the  GNU GENERAL PUBLIC LICENSE v3.0.
Permissions of this strong copyleft license are conditioned on making available complete source code of licensed works and modifications,
which include larger works using a licensed work, under the same license. Copyright and license notices must be preserved.
Contributors provide an express grant of patent rights.
For the full license text see the [LICENSE.md](LICENSE.md) file.
