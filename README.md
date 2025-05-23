# Exno.9-To explore and understand the various prompting techniques used for generating videos through AI models. 


# Register no.:212222240062
# Aim: 
To perform the Exploration of Prompting Techniques for Video Generation
# Algorithm: 
Design and implement Python-based applications that:

1. Accept user input as a prompt.

2. Interact with AI models (ChatGPT for task management, audio-focused models for sound generation, and video generation models).

3. Receive responses with task suggestions, generated audio, or video content.

4. Store, organize, and optionally download outputs.

5. Demonstrate progression from simple to advanced prompts.

![image](https://github.com/user-attachments/assets/92eb876b-1dbe-4741-8dcc-2dbc77e0ef70)

# Objective:

## Build ChatGPT-powered assistant that:

a. Organizes user-input daily tasks.
b. Evolves with progressively advanced prompt engineering.
c. Outputs categorized, prioritized, and optimized to-do lists.
d. Logs data for reuse and review.

![image](https://github.com/user-attachments/assets/7d37ff80-648c-4548-b805-e17ec43a2f0e)


## Build an AI audio content generator that:

a. Accepts user prompts for music, narration, or effects.
b. Interfaces with audio generation APIs.
c. Saves or plays audio.

![image](https://github.com/user-attachments/assets/66ebe0e9-b96e-4b7f-883f-d87936832d46)


## Build an AI video generation pipeline that:

a. Accepts textual prompts and creates visual stories or clips.
b. Demonstrates effect of prompt detail on output quality.
c. Interfaces with APIs such as RunwayML or Pika Labs.
![image](https://github.com/user-attachments/assets/31f06e3e-3386-4fa1-ac34-4cd954bdab34)


# Procedure:
Familiarize Yourself with Video Generation Models:
Begin by exploring AI tools capable of video generation from text prompts. Popular models for video generation include:
Runway Gen-2
Synthesia
Pictory
DeepBrain
Understand the capabilities and limitations of each tool before starting the experiment.
Create Simple Prompts for Video Generation:
Start with simple prompts to generate short videos. These prompts should describe the general subject or activity.
Example prompt: "A person walking in a park."
Experiment with More Detailed Prompts:
Gradually refine your prompts by adding specific details, such as the setting, lighting, actions, or expressions.
Example prompt: "A person in a red jacket walking along a sunny park path, with birds flying in the sky, and a dog running beside them."
Add Time and Motion Elements:
Incorporate aspects like timing, transitions, or camera movement in your prompts.
Example prompt: "A time-lapse video of the sun setting over the ocean, with the camera slowly zooming out from a beach, capturing the waves and changing colors in the sky."
Test Different Video Styles:
Experiment with different styles of video generation, such as animations, live-action, cinematic, or artistic.
Example prompt: "An animated scene of a futuristic city at night, with glowing neon lights, flying cars, and a bustling crowd of people."
Iterate and Adjust Prompts:
Evaluate the generated video and refine the prompt if needed. Consider aspects like the pacing, transitions, and consistency of motion in the video.
Example: After reviewing, refine the prompt to add more details about the camera angles or actions: "A cinematic shot of a car speeding through a neon-lit city at night, with reflections on the wet street and a high-speed chase scene."
Generate Multiple Versions:
Generate multiple versions of the same prompt with slight variations to compare how the video output differs based on the phrasing of the prompt.
Save and Compare Outputs:
Save different versions of the videos and compare the results to understand how different prompts produce varying styles, sequences, and video qualities.

## Step-by-Step Implementation – Task Manager:

## Step 1: Set Up API Access

Create an OpenAI account

Obtain your API key.

Install necessary Python libraries:
```
pip install openai python-dotenv
```
Store your API key in a .env file:
```
OPENAI_API_KEY=your_openai_key_here
```
## Step 2: Basic Prompt – Simple Task Listing
```py
import os
import openai
from dotenv import load_dotenv

load_dotenv()
openai.api_key = os.getenv("OPENAI_API_KEY")

def ask_chatgpt(prompt):
    response = openai.ChatCompletion.create(
        model="gpt-4",
        messages=[{"role": "user", "content": prompt}]
    )
    return response['choices'][0]['message']['content']
```
### Basic prompt
```py
simple_prompt = "Organize my tasks: buy groceries, finish homework, call mom."
response = ask_chatgpt(simple_prompt)
print("\nSimple Response:\n", response)
```
## Step 3: Intermediate Prompt – Add Prioritization and Deadlines
```
intermediate_prompt = (
    "Organize and prioritize these tasks based on urgency and time required: "
    "1. Buy groceries, 2. Finish homework (due tomorrow), 3. Call mom, 4. Reply to emails, 5. Exercise for 30 minutes."
)
response = ask_chatgpt(intermediate_prompt)
print("\nIntermediate Response:\n", response)
```
## Step 4: Advanced Prompt – Include Categorization, Time Blocks, Suggestions
```py
advanced_prompt = (
    "Create a daily schedule using time blocks for the following tasks. Categorize them as personal, academic, or health. "
    "Include any optimization tips: 1. Finish AI assignment (due at 5 PM), 2. Gym session, 3. Buy vegetables, 4. Team meeting at 11 AM, 5. Review notes, 6. Meditation."
)
response = ask_chatgpt(advanced_prompt)
print("\nAdvanced Response:\n", response)
```
Step 5: Logging Responses
```py
import json
from datetime import datetime

def log_response(prompt, response):
    entry = {
        "timestamp": str(datetime.now()),
        "prompt": prompt,
        "response": response
    }
    with open("task_log.json", "a") as f:
        json.dump(entry, f)
        f.write("\n")

log_response(advanced_prompt, response)
```
## Step-by-Step Implementation – Audio Generation:

## Step 1: Choose an AI Tool for Audio (e.g., ElevenLabs, Bark, Google TTS)

Register and obtain API key.

Install required libraries (example with ElevenLabs):
```
pip install elevenlabs
```
## Step 2: Generate Audio with Prompt Input
```py
from elevenlabs import generate, play, set_api_key
import os

set_api_key(os.getenv("ELEVENLABS_API_KEY"))

def generate_audio(prompt_text):
    audio = generate(
        text=prompt_text,
        voice="Rachel",
        model="eleven_monolingual_v1"
    )
    play(audio)

prompt_text = "Hello! This is your AI narrator helping you stay productive today."
generate_audio(prompt_text)
```
## Step-by-Step Implementation – Video Generation:

## Step 1: Choose a Video Generation Tool (e.g., RunwayML, Synthesia, Pictory, DeepBrain)

Explore each tool's capabilities, GUI interface, and API availability.

## Step 2: Create Simple Prompts for Video Generation:

Example: "A person walking in a park."

## Step 3: Experiment with More Detailed Prompts:

Example: "A person in a red jacket walking along a sunny park path, with birds flying in the sky, and a dog running beside them."

## Step 4: Add Time and Motion Elements:

Example: "A time-lapse video of the sun setting over the ocean, with the camera slowly zooming out from a beach, capturing the waves and changing colors in the sky."

## Step 5: Test Different Video Styles:

Example: "An animated scene of a futuristic city at night, with glowing neon lights, flying cars, and a bustling crowd of people."

## Step 6: Iterate and Adjust Prompts:

Example refinement: "A cinematic shot of a car speeding through a neon-lit city at night, with reflections on the wet street and a high-speed chase scene."

## Step 7: Generate Multiple Versions:

Use variations of the same prompt to observe output differences.

## Step 8: Save and Compare Outputs:

Archive video outputs to evaluate style, transitions, and content alignment.

Example Code (API use with RunwayML – Pseudo):
```py
import requests

payload = {
    "prompt": "A scenic mountain view with sunrise and moving clouds",
    "resolution": "1080p",
    "duration": 10
}
headers = {"Authorization": f"Bearer {os.getenv('RUNWAY_API_KEY')}"}
response = requests.post("https://api.runwayml.com/v1/video", json=payload, headers=headers)
print(response.json())
```
# Result:

The application successfully demonstrates:

Task organization with ChatGPT.

Audio narration generation using advanced prompting.

Video generation showing differences in prompt quality.
![image](https://github.com/user-attachments/assets/22af2f2b-8938-4297-ae33-2085026bcf5d)


# Conclusion:
This experiment shows how various prompting techniques can be effectively used to build AI-powered applications. In this case:

ChatGPT helps structure daily life with natural prompts.

Audio APIs bring those prompts to life through narration or sound design.

Video models generate visuals based on the level of descriptive prompting.

The approach is scalable to full creative workflows like audiobooks, explainer videos, or task automation.
