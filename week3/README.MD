# Building a YouTube Video Summary Bot

In this project, you'll create a powerful tool that automatically summarizes YouTube videos using Python and some amazing libraries. By the end, you'll understand how to work with text, audio, and even AI-powered language models to create a practical application.

## Table of Contents

1.  [Introduction to Google Colab](#1-introduction-to-google-colab)
2.  Essential Libraries(#2-essential-libraries)
3.  Downloading Videos: Pytube in Action(#3-downloading-videos-pytube-in-action)
4.  Transcribing Audio: Whisper's Magic(#4-transcribing-audio-whispers-magic)
5.  Communicating with AI: OpenAI API Requests(#5-communicating-with-ai-openai-api-requests)
6.  Crafting Effective Prompts(#6-crafting-effective-prompts)
7.  Putting It All Together: Building the Bot(#7-putting-it-all-together-building-the-bot)

## 1. Introduction to Google Colab

We'll be using Google Colab, a free online environment where you can write and run Python code. It's perfect for project like these because it comes with many libraries pre-installed, saving you the hassle of setting things up, and it also comes with T40 GPU for infrence. 

## 2. Essential Libraries

Before we dive in, let's install the tools we'll need:

```bash
!pip install pytube
!pip install -U openai-whisper
!pip install subprocess
!pip install ffmpeg
!pip install openai
```

These libraries do the following:

*   **Pytube:** Helps us download YouTube videos.
*   **OpenAI Whisper:** Converts spoken language in the video to text (transcription).
*   **OpenAI:** Lets us interact with powerful AI models that understand and generate text.


## 3. Downloading Videos: Pytube in Action

Downloading videos from YouTube is a crucial step in our project. We'll be using Pytube, a Python library that simplifies this process.

Now, let's write a Python function to download the audio from a YouTube video:

```python
# Import the YouTube class from the pytube library
from pytube import YouTube

# Define a function to download the audio from a YouTube video
def download_audio(youtube_url, output_path='.', filename='audio.mp4'):
    # Create a YouTube object using the provided URL
    yt = YouTube(youtube_url)
    
    # Get the audio-only stream from the video
    audio_stream = yt.streams.get_audio_only()
    
    # Download the audio stream to the specified output path with the given filename
    audio_stream.download(output_path=output_path, filename=filename)
    
    # Return the filename of the downloaded audio file
    return filename
```
This function: 
- Creates a YouTube object by passing the YouTube video URL.
- Extracts the audio-only stream from the video using streams.get_audio_only().
- Downloads the audio stream to the specified output path with the provided filename.
- Returns the filename of the downloaded audio file.

**Finding and Using Documentation:**

1.  **Pytube Documentation:** The official Pytube documentation is your best friend: [Pytube Github repo](https://github.com/pytube/pytube)
2.  **Example Code:** Look for examples in the "Quickstart" section or the "User Guide." These examples show you how to download videos and audio.
3.  **Adapt and Experiment:** Try running the examples and then modify them to fit your needs. For instance, you might want to change the filename or download location.

## 4. Transcribing Audio: Whisper's Magic

Transcribing audio from YouTube videos is a critical step in our project. We'll be using Whisper, an audio transcription library powered by machine learning.

Now, let's write a Python function to transcribe audio from a video file:

```python
# Import the whisper module for audio transcription
import whisper

# Define a function to transcribe audio to text using Whisper
def transcribe_audio_to_text(audio_file_path):
    # Load the pre-trained Whisper model
    model = whisper.load_model("base")
    
    # Transcribe the audio file to text
    result = model.transcribe(audio_file_path)
    
    # Print the transcribed text
    print(result["text"])
    
    # Return the transcribed text
    return result['text']
```

This function:
- Imports the `whisper` module, which provides access to the Whisper library for audio transcription.
- Defines a function `transcribe_audio_to_text` that takes an audio file path as input and transcribes the audio to text using the pre-trained Whisper model.
- The transcribed text is printed and returned for further processing.

To learn more about how Whisper works and how to customize it, check out the [Whisper GitHub repository](https://github.com/openai/whisper).

## 5. Communicating with AI: OpenAI API Requests

Communicating with AI models is where the real magic happens in our project. We'll be using the OpenAI API to interact with powerful language models that can understand and generate text.

Now, let's write a Python function to summarize text using the OpenAI API:

```python
# Import the required modules from the OpenAI library
import openai

# Define a function to summarize text using GPT models from the OpenAI API
def summarize_text_with_gpt(transcribed_text):
    # Set up API request parameters
    api_url = "https://api.openai.com/v1/chat/completions"
    api_key = "<your-api-key>"
    headers = {"Authorization": f"Bearer {api_key}"}
    
    # Create an OpenAI client
    client = openai.OpenAI(api_key=api_key)
    
    # Define the message prompt
    prompt = {
        "model": "gpt-3.5-turbo-0125",
        "messages": [
            {"role": "system", "content": "You are a helpful assistant"},
            {"role": "user", "content": f"Provide a summary of the following in Markdown format using bullet points:\n\n{transcribed_text}"}
        ]
    }
    
    # Send request to OpenAI API and get response
    response = client.chat.completions.create(**prompt)
    
    # Extract the generated summary from the response
    summary = response.choices[0].message.content
    
    # Print and return the summary
    print(summary)
    return summary
```

This function communicates with the OpenAI API to generate a summary of the transcribed text using GPT models. Here's what happens:
- We set up the API request parameters including the API URL, API key, and request headers.
- We create an OpenAI client using the provided API key.
- We define a message prompt specifying the GPT model to use and the user's input text.
- We send the prompt to the OpenAI API and receive a response containing the generated summary.
- Finally, we extract and print the summary.

Make sure to replace `<your-api-key>` with your actual OpenAI API key before using this function.


## 6. Crafting Effective Prompts

The key to getting good summaries is asking the AI the right questions (prompts).  In our code, we ask it to:

```python
{"role": "user", "content": f"Provide a summary of the following in Markdown format using bullet points:\n\n{transcribed_text}"}
```

By being specific and asking for bullet points, we guide the AI to create a clear and concise summary.

## 7. Putting It All Together: Building the Bot

The rest of the code combines all the steps:

1.  Download the video's audio.
2.  Transcribe the audio into text.
3.  Summarize the text using the AI model.
4.  Format the summary nicely using Markdown.
5.  Save the summary to a file.

**Your Turn:**

Now it's your time to experiment! Try summarizing different videos and see how the AI performs. You can even try changing the prompt to get different kinds of summaries.  Have fun exploring the power of AI and programming!
