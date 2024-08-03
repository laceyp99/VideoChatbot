# Video QA GPT

## Overview
This project demonstrates a chatbot capable of answering questions about video content by processing video frames and leveraging the power of OpenAI's GPT-4o-mini model. It focuses on efficient video processing and handling OpenAI's API limitations to provide detailed context and reference frames for accurate responses.

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