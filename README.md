# Video QA GPT

## Overview
This project demonstrates a chatbot capable of answering questions about video content by processing video frames and leveraging the power of OpenAI's GPT-4o-mini model. It focuses on efficient video processing and handling OpenAI's API limitations to provide detailed context and reference frames for accurate responses.

## Approach
Currently, the OpenAI API limits each API call to 250 frames of image data. My current approach to load longer videos, is to prompt GPT 4o mini every 250 frames to describe the video in natural language. I also have included in the system message to for the model to pick a frame reccomendation so that a reference frame will be passed to the final model for supplemental context to the natural language description of the video chunk. This will be done as a video processing step before interacting with the informed model. This processing step is necessary to increase the video length limit that the chatbot can answer questions about. The processing extends the maximum limit from 8.3 seconds to over 2 hours of video (((8.3 * 4) * 250)/60/60). The question is how well do these descriptions inform the chatbot to answer your questions?

## Requirements
* Python 3.x
* OpenAI API Key
* Libraries: openai, python-dotenv, opencv-python, IPython

## Installation
Install the required libraries using pip:
```bash
pip install openai python-dotenv opencv-python 
``` 

## Environment Setup
Create a '.env' file in the project directory and add your OpenAI API key:
```makefile
OPENAI_API_KEY=your_api_key_here
```
## Cost Assesment
**GPT-4o**:
Using this video processing method is pretty expensive. Even at 150x150, it costs $0.32 for one set of 250 frames. Then incorporate the additional system message text and the expected output text (output tokens cost ~3x more than input normally). Thats $0.35-0.50 every 8.3 seconds of video. Thats $2.50-$3.50 every minute of video. Also this is just to generate the helpful context to supply a conversational chatbot that can answer questions about the video (which would then add more cost), so this is all a video processing fee before the user even can try out the chatbot. That seems pretty unrealistic. I'd never pay $2.50+ to have a chatbot answer questions on a one minute video.

**GPT-4o-mini**:
GPT 4-o mini is way more cost efficient. A little bit less than a penny for every 250 frames (8.3 seconds) of video. There will still be an uploading cost attached to this ($0.32 for almost 5 mins), but thats more reasonable. Also compressing the video by 4x frames helps with processing cost and time. 