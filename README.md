# AssemblyAI Speech-to-Speech with Pipecat

A voice agent built with [Pipecat](https://github.com/pipecat-ai/pipecat) and the [AssemblyAI](https://www.assemblyai.com) native speech-to-speech API. Speak directly with the agent in your browser — no separate STT or TTS services needed.

## Setup

1. Copy the example env file and add your API key:

```sh
cp .env.example .env
```

2. Run the bot:

```sh
uv run bot.py
```

Open the URL printed in the terminal to start a conversation.

## How it works

`pipecat_assemblyai_realtime.py` is a Pipecat `LLMService` plugin that connects directly to AssemblyAI's native S2S WebSocket API. It handles audio streaming, turn detection, transcription, and speech synthesis in a single connection — replacing the usual STT → LLM → TTS pipeline with one service.

`bot.py` wires that service into a Pipecat pipeline and defines the agent's behavior: system prompt, tools, and transport (WebRTC or Daily).
