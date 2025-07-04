# Minha primeira experiência com Azure Speech Service 🎙️☁️

> Relato pessoal por [@igorgoncalves](https://github.com/igorgoncalves)

---

## 🧭 Introdução

Minha jornada com o **Azure Speech Service** começou por curiosidade e pela necessidade de explorar soluções de transcrição de voz precisas e escaláveis. Já tinha ouvido falar sobre a API em projetos anteriores, mas nunca havia usado de fato.

---

## 🚀 Primeiros passos

### 🔑 Criação do recurso no portal Azure

O primeiro contato foi direto no [portal.azure.com](https://portal.azure.com). Criei um recurso do tipo "Speech" selecionando a região e o nível de preço gratuito (F0). Logo recebi duas informações importantes:

- **Chave da API**
- **Endpoint regional**

Esses dados seriam essenciais para autenticar as chamadas no serviço.

---

## 🧪 Primeiros testes

### 🔧 Ferramentas usadas

Para testar o Speech-to-Text, segui os exemplos da própria [documentação oficial](https://learn.microsoft.com/azure/cognitive-services/speech-service/) e usei:

- Python (via SDK do Azure)
- VSCode com extensão Azure
- Arquivos `.wav` curtos para os testes

### 🧑‍💻 Código base (Python)

```python
import azure.cognitiveservices.speech as speechsdk

speech_config = speechsdk.SpeechConfig(subscription="SUA_CHAVE", region="sua_regiao")
audio_config = speechsdk.AudioConfig(filename="audio.wav")

speech_recognizer = speechsdk.SpeechRecognizer(speech_config=speech_config, audio_config=audio_config)
result = speech_recognizer.recognize_once()

print("Transcrição:", result.text)
