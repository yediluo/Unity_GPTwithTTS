# Text to Speech in Unity

## Overview

This Unity project demonstrates how to convert text into speech in real time using OpenAI's TTS (Text-to-Speech) API. The script avoids saving the audio to a file and instead plays the speech directly through an `AudioSource` component in Unity. This approach is ideal for applications that require immediate playback and do not need to store the audio data.

## Prerequisites

- Unity Editor (our version is 2022.3.17f1)
- An active internet connection to access the OpenAI API.
- An API key from OpenAI.

## Setup
**OpenAI API Key**: You will need an API key from OpenAI to use their TTS service. Replace the `apiKey` variable in the TTS.cs and GPTManager.cs with your actual API key.

## Usage

- The script is designed to be triggered through UI events or other game events. To initiate speech synthesis, call the `GenerateSpeech(string txt)` method with the desired text as the argument. 

- The method can be connected to UI elements (like buttons) via the Unity Inspector by dragging the GameObject with the script attached into the onClick event and selecting the `GenerateSpeech` method.

## How It Works

The `GenerateSpeech` method performs the following operations:
- **Building the Request**: It constructs a JSON payload with the required parameters (model, voice, input text).
- **Sending the Request**: It uses `UnityWebRequest` to send a POST request to OpenAI's API endpoint.
- **Handling the Response**: On success, it directly loads the audio data into an `AudioClip` and plays it using the assigned `AudioSource`. On failure, it logs the error.

The audio data is streamed directly into Unity's audio system without being saved to disk, which is achieved by using `DownloadHandlerAudioClip` configured to handle the audio format returned by the API (MPEG in this case).

## Notes

- Ensure that the API key is kept secure and not exposed in your public or shared code.
- You might need to handle exceptions and errors, especially related to network issues or API limits.
