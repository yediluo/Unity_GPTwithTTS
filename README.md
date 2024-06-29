# Text to Speech in Unity

## Overview

This Unity project demonstrates how to convert text into speech in real time using OpenAI's TTS (Text-to-Speech) API. The script included avoids saving the audio to a file and instead plays the speech directly through an `AudioSource` component in Unity. This approach is ideal for applications that require immediate playback and do not need to store the audio data.

## Prerequisites

- Unity Editor (2019.4 or later recommended).
- An active internet connection to access the OpenAI API.
- An API key from OpenAI.

## Setup

1. **OpenAI API Key**: You will need an API key from OpenAI to use their TTS service. Replace the `apiKey` variable in the script with your actual API key.

2. **Unity Project Setup**:
    - Create a new Unity project or open an existing one.
    - Import the script into your project.
    - Create an empty GameObject in your scene and attach the script to it.
    - Create an `AudioSource` component on the same GameObject or another GameObject in the scene. Assign this `AudioSource` to the `audioSource` field of the script through the Unity Inspector.

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
