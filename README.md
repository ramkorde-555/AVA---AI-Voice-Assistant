# AVA---AI-Voice-Assistant
AVA is a voice assistant powered by the open source language models OpenAI Whisper, Qwen Chat and Bark TTS.

### Running the assistant
```python
AVA = VoiceAssistant() <br>
query_id = "test01" <br>
AVA.run(query_id) <br>
```
- query_id: A unqiue alphanumeric ID for each user query

The instance VoiceAssistant() can be intialized with optional 'preload' parameter.
'preload' is a list of models to load on the memory at the time of initializing the instance. Allowed elements of 'preload' are "transcribe" and "response", corresponding respectively to the models OpenAI/Whisper and QwenChat
- AVA = VoiceAssistant(preload=None) or AVA = VoiceAssistant(): Neither of the models are loaded when initializing the instance AVA. Instead, Whisper is loaded when the transcription function 'read_query' is called by AVA.run() and is unloaded from the memory once transcription is done.)
- AVA = VoiceAssistant(preload=["transcribe"]) or AVA = VoiceAssistant(preload=["response"] or AVA = VoiceAssistant(preload=["transcribe", "response"]): Listed model/s is/are loaded on the memory at the time of initializing AVA. The models stay on the memory as long as the object AVA lives. This allows faster inference at the cost of higher peak memory usage.

Cuda supported models are automatically loaded and run on the GPU if cuda is available.
