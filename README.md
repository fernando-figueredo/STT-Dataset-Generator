# STT-Dataset-Generator
This notebook generates a Training Dataset that can be applied in Speech to Text Artificial Intelligence such as Mozzilla Deepspeech. the dataset can be generated from .wav audios, which can be extracted from youtube videos for example, and are transcribed by the library "SpeechRecognition" which in this case used the Google API for Transcription in PT-BR

---

# Adjusting Parameters


you can choose the minimum duration of silence and the minimum amplitude in dBFS that will be considered silence in the parameters of the function "split_on_silence" from the pydub library

```bash
chunks = split_on_silence (
    # Use the loaded audio.
    song, 
    # Specify that a silent chunk must be at least or x ms long.
    min_silence_len = x,
    # Consider a chunk silent if it's quieter than -y dBFS.
    silence_thresh = -y
)
```

You can choose the language of the audio to be transcribed when calling the "speech recognition" function
```bash
transcricao = (r.recognize_google(audio_text,language='pt-BR'))
```
