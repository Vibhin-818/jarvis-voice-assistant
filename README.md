# JARVIS â€” Desktop Voice Assistant

A Python desktop assistant controlled entirely by voice. It listens for a command, speaks the response back, and performs the action locally.

## What it can do

- **Voice input** with `speech_recognition` (microphone, with a 7 second listen window)
- **Spoken replies** with `pyttsx3` (SAPI5 voice)
- **Open applications**: Notepad, Chrome, Command Prompt
- **Web actions**: open sites, search YouTube, fetch Wikipedia summaries
- **Communication**: send WhatsApp messages through `pywhatkit`, send email over SMTP
- **Utilities**: play songs, tell jokes, report the current time, show the public IP address

## How it works

```
microphone -> speech_recognition -> intent matching -> action
                                          |
                                    pyttsx3 speaks the result
```

Command handling is a simple intent router in `jarvis.py`, which keeps the project easy to extend with new commands.

## Requirements

```
SpeechRecognition
pyttsx3
wikipedia
pywhatkit
pyjokes
requests
```

Install with:

```bash
pip install SpeechRecognition pyttsx3 wikipedia pywhatkit pyjokes requests
```

On Windows, `pyttsx3` uses SAPI5, so no extra audio driver is needed.

## Run

```bash
python JARVIS/jarvis.py
```

Say "Jarvis" followed by a command, for example: "open notepad", "search Wikipedia for machine learning", "play a song on YouTube".

## Security note

Email credentials must be supplied through environment variables, not hard-coded:

```python
import os
EMAIL_USER = os.getenv("EMAIL_USER")
EMAIL_PASS = os.getenv("EMAIL_PASS")
```

## Roadmap

- Wake-word detection instead of always-listening
- Replace the intent router with a small local LLM for free-form commands
- Package as a Windows tray application

## Structure

```
JARVIS/
  jarvis.py     # assistant logic and intent handling
  about.txt     # original project notes
```
