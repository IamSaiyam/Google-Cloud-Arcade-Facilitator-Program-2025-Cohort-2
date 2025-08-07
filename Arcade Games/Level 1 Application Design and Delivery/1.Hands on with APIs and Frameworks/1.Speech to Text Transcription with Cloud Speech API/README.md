# Speech to Text Transcription with the Cloud Speech API

**Lab Duration:** 30 minutes  
**Difficulty:** Introductory  
**No cost**

---

## Overview

This lab introduces Google Cloud's Speech-to-Text API, which transcribes audio speech files into text in over 80 languages. It focuses on exploring speech recognition capabilities through API requests.

---

## What This Lab Teaches

- Creating and using API keys to authenticate requests
- Constructing Speech-to-Text API requests using `curl`
- Sending audio files to the API for transcription
- Transcribing audio in multiple languages by setting language parameters
- Understanding API responses including transcription text and confidence scores

---

## Important Command Learned

To call the Speech-to-Text API and receive transcribed results, you use the following `curl` command:

```
curl -s -X POST -H "Content-Type: application/json" --data-binary @request.json \
"https://speech.googleapis.com/v1/speech:recognize?key=${API_KEY}" > result.json
``` 

This command sends a transcription request using a JSON configuration and stores the API response locally.

---

## What I Learned

- How powerful and flexible the Speech-to-Text API is in supporting multiple languages and encoding types
- The importance of constructing proper API requests with authentication and relevant parameters
- Practical use of `curl` for interacting with REST APIs
- How speech recognition confidence metrics provide insight into transcription accuracy
- The value of cloud-hosted AI services to simplify speech transcription tasks without local infrastructure

---

This lab provided foundational skills to build applications that incorporate speech recognition via a cloud API, enabling development of voice-enabled and intelligent applications.