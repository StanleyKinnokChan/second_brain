# Amazon Polly

- converts **text** into **life-like** speech (**no translation**)
- Type:
    - **standard**: Concatenative (phonemes)
    - **neural**: phonemes ⇒ spectrograms ⇒ vocoder ⇒ audio
- output: PCM, MP3….
- Use **speech synthesis markup language (SSML)** for additional control over how polly generates speech
    - emphasize
    - certain pronunciation
    - exaggerate
    - …
