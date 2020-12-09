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
---

# Generating the Dataset

As a result of this notebook, a folder will be obtained with the audios cut into smaller parts "chunk_ (i) .txt" (approximately one cut for each sentence) and a file "transcript.txt" in which each line will correspond to an audio transcript (if the API is unable to transcribe the audio, a blank line will be placed)

The dataset itself must cross these two information in a single file. The following describes how to generate the dataset according to the Mozzilla Deepspeech model, but the same logic can be adapted for other types of STT applications.

### Step 1:
   Download the folder generated to your PC 

### Step 2:
Create a .txt file describing all the files in the downloaded folder using the following command that must be executed in the terminal (in my case Windows 10 was used):
- Put you path to the folder in the command cd

```bash
cd c:\user\fernando\download\STTDataset
```
-press ENTER and type the following command
```bash
dir /b /o:n > files.txt
```
### Step 3:
Delete the names "audio.wav" and "transcript.txt" from "files.txt" as they will not be part of the dataset

### Step 4
Organize the file names from the "files.txt" in numerical order with a .txt editor (I recommend using EM_Editor)

### Step 5
Use a spreadsheet editor to generate the ".tsv" file (I used google sheets) using the path information of the files and the transcript in "transcript.txt" which will already be in the correct order

### Step 6
Organize the sentences in alphabetical order and delete blank sentences

### Step 7
Complete the .tsv information using the standard Mozzilla Deepspeech documentation

### Step 8
Download the file as a .tsv

### Step 9 
Save the audio files "Chunk_(i).wav" in a folder named "clips"

---
# Comments

- Note that the .wav files are large, if you would like to make your dataset lighter, you can convert them to .mp3 at the end of the process

- You can separate the generated dataset for training, testing and validation

---
# References

[1] Stack Overflow. **Split audio files using silence detection** [link](https://stackoverflow.com/questions/45526996/split-audio-files-using-silence-detection/46001755)

[2] Lets Code. **Speech Recognition com Python** (portuguse) [link](https://letscode.com.br/blog/speech-recognition-com-python)

[3] Uberi. **SpeechRecognition** [link](https://github.com/Uberi/speech_recognition#readme)

