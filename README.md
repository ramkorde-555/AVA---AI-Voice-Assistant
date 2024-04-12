# AVA---AI-Voice-Assistant
AVA is a voice assistant powered by the open source language models OpenAI Whisper, Qwen Chat and Bark TTS.

### Running the assistant
```python
AVA = VoiceAssistant()
query_id = "test01"
AVA.run(query_id)
```
- query_id: A unqiue alphanumeric ID for each user query

The instance VoiceAssistant() can be intialized with optional 'preload' parameter.
'preload' is a list of models to load on the memory at the time of initializing the instance. Allowed elements of 'preload' are "transcribe" and "response", corresponding respectively to the models OpenAI/Whisper and QwenChat
- ```python AVA = VoiceAssistant(preload=None)``` or ```python AVA = VoiceAssistant()```: Neither of the models are loaded when initializing the instance AVA. Instead, Whisper is loaded when the transcription function 'read_query' is called by AVA.run() and is unloaded from the memory once transcription is done.)
- ```python AVA = VoiceAssistant(preload=["transcribe"])``` or ```python AVA = VoiceAssistant(preload=["response"])``` or ```python AVA = VoiceAssistant(preload=["transcribe", "response"])```: Listed model/s is/are loaded on the memory at the time of initializing AVA. The models stay on the memory as long as the object AVA lives. This allows faster inference at the cost of higher peak memory usage.

Cuda supported models are automatically loaded and run on the GPU if cuda is available.

```python AVA.run(query_id) ``` records a user query and saves to the file {query_id}_Q.wav
The response is saved to the file {query_id}_A.wav
Currently, only WAV files with a sampling rate of 16000 are supported.

Future Updates:
- Optional recording: Currently, all user queries are recorded and then processed. Optional recording will allow any WAV formatted file to be read directly by giving its path
- Streaming without saving: User queries will be recorded and an output will be generated in a 'streaming' style, using some GUI application. This will remove the need to save queries and responses
- Improved Speed: The entire pipeline is to be sped up to become almost real-time for a more realistic experience
