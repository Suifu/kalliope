Questo TTS è basato sull'[engine IBM Watson](https://www.ibm.com/watson/services/text-to-speech/).

## Installazione

È necessario creare un account e quindi un progetto per ottenere una posizione e un apikey.

Una volta che il progetto è stato creato, dovresti vedere le tue credenziali come le seguenti
```json
{
  "url": "https://stream.watsonplatform.net/text-to-speech/api",
  "apikey": "myRANDOMAPIKEY"
}
```

## Parametri d'input

| Parametro  |Necessario| Default | Valori possibili          | Commento                                                                                                        |
|------------|----------|---------|---------------------------|-----------------------------------------------------------------------------------------------------------------|
| apikey     | si       |         |                           | apikey fornito da [IAM](https://console.bluemix.net/docs/services/watson/getting-started-iam.html)              |
| location   | no       |  LONDON |                           | [destinazione](https://www.ibm.com/watson/developercloud/text-to-speech/api/v1/curl.html?curl#service-endpoint) |
| voice      | si       |         | Vedi la tabella qui sotto | Codice che definisce la voce utilizzata per la sintesi                                                          |

## Voice code

Il Voice code può essere utilizzato nel flag della propria configurazione come di seguito

| Lingua                   | Codice                           | Genere  |
|--------------------------|----------------------------------|---------|
| Tedesco                  | de-DE_BirgitVoice                | Femmina |
| Tedesco                  | de-DE_DieterVoice                | Maschio |
| Inglese UK               | en-GB_KateVoice                  | Femmina |
| Inglese US               | en-US_AllisonVoice               | Femmina |
| Inglese US               | en-US_LisaVoice                  | Femmina |
| Inglese US               | en-US_MichaelVoice (the default) | Maschio |
| Spagnolo Castigliano     | es-ES_EnriqueVoice               | Maschio |
| Spagnolo Castigliano     | es-ES_LauraVoice                 | Femmina |
| Spagnolo LatinoAmericano | es-LA_SofiaVoice                 | Femmina |
| Spagnolo Nord Americano  | es-US_SofiaVoice                 | Femmina |
| Francese                 | fr-FR_ReneeVoice                 | Femmina |
| Italiano                 | it-IT_FrancescaVoice             | Femmina |
| Giapponese               | ja-JP_EmiVoice                   | Femmina |
| Portoghese Brasiliano    | pt-BR_IsabelaVoice               | Femmina |

## Esempio d'impostazioni

```yaml
default_text_to_speech: "watson"

text_to_speech:
  - watson:
      apikey: "MyRANDOMAPIKEY"
      voice: "fr-FR_ReneeVoice"
      location: "https://stream-fra.watsonplatform.net/text-to-speech/api"
```

## Note

Questo motore TTS è gratuito per meno di 10.000 caratteri al mese.
