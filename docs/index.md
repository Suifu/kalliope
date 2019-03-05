# Benvenuti nella documentazione di Kalliope

Kalliope è un framework  che ti aiuterà a creare il tuo assistente personale.

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

Se vuoi un'idea di ciò che puoi fare con Kalliope, premi l'immagine di seguito
<p align="center">
[![ENGLISH DEMO](https://img.youtube.com/vi/PcLzo4H18S4/0.jpg)](https://www.youtube.com/watch?v=PcLzo4H18S4)
</p>
