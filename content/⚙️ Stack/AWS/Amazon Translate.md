# Amazon Translate

- text translation (language to language one word at a time)
- 2 parts process
    1. **encoder reads source** => semantic representation (meaning)
    2. **Decoder reads meaning** => writes target language
- use attention mechanism ensure ‘meaning’ is translated
- **Auto detection of source language**
- use cases
    - multilingual user experience (always a component of a business process)
    - emails, in-game chat, customer live chat
    - translate incoming data
    - combined with comprehend, transcribe, polly, data in S3
    - **commonly integrates with other services/ apps/ platforms**
