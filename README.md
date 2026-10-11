# ChatGPT Mini Bot

A beginner-friendly AI chatbot built with Python and the Groq API, powered by the `openai/gpt-oss-20b` model.

This project demonstrates how to integrate a Large Language Model (LLM) into a Python application and generate AI-powered responses from user input. It is a simple first step toward understanding Generative AI, prompt-based interaction, API integration, and conversational AI.

## Project Overview

ChatGPT Mini Bot is a lightweight, command-line AI application that allows users to enter a question or prompt and receive an AI-generated response.

The application sends the user's input to a language model through the Groq API, receives the generated response, and displays it in the terminal.

Despite its name, this project is an independent chatbot application. It does not directly connect to OpenAI's ChatGPT service; it uses the Groq API to access the configured model.

## Key Features

- **AI-Powered Responses:** Generates answers using a Large Language Model.
- **Interactive User Input:** Accepts questions and prompts through the terminal.
- **Groq API Integration:** Connects Python to an AI model through the Groq SDK.
- **Simple Implementation:** Uses a small, readable Python program.
- **Prompt-Based Interaction:** Sends user-provided text to the model.
- **Beginner-Friendly:** Suitable for learning the fundamentals of LLM application development.

## Technology Stack

| Technology | Purpose |
|---|---|
| Python | Core programming language |
| Groq API | Sends prompts to the AI model and receives responses |
| Groq Python SDK | Integrates the Groq API with Python |
| `openai/gpt-oss-20b` | Language model configured in the project |
| Terminal / Command Prompt | User input and response display |

## How It Works

The chatbot follows a straightforward workflow:

1. Initializes the Groq client using an API key.
2. Prompts the user to enter a question or message.
3. Sends the prompt to the configured language model.
4. Receives the generated response from the API.
5. Extracts the response text from the API result.
6. Displays the answer in the terminal.

### Workflow

```text
User Input
    |
    v
Python Application
    |
    v
Groq API
    |
    v
GPT-OSS-20B Model
    |
    v
Generated Response
    |
    v
Terminal Output
```

## Project Structure

```text
chatgpt-mini-bot/
│
├── LLM First Project.py
└── README.md
```

- `LLM First Project.py` — Contains the main Python application.
- `README.md` — Provides project documentation and setup instructions.

## Requirements

Before running the project, make sure you have:

- Python 3 installed.
- A working internet connection.
- A Groq account.
- A valid Groq API key.
- The required Python package installed.

## Installation and Setup

### Step 1: Clone the Repository

Open a terminal or command prompt and run:

```bash
git clone https://github.com/muhammad-musab03/chatgpt-mini-bot.git
```

Navigate to the project directory:

```bash
cd chatgpt-mini-bot
```

### Step 2: Install Python Dependencies

Install the Groq Python SDK:

```bash
python -m pip install groq
```

If your system uses `python3`, run:

```bash
python3 -m pip install groq
```

### Step 3: Obtain a Groq API Key

1. Visit the official [Groq Console](https://console.groq.com/).
2. Sign in or create an account.
3. Open the API keys section.
4. Create an API key following the available instructions.
5. Copy the key and store it securely.

An API key is required because the application communicates with a hosted AI model through the Groq API.

### Step 4: Configure Your API Key

The current Python source code contains this placeholder:

```python
api_key = "ADD YOUR API KEY"
```

Replace the placeholder with your own Groq API key on your local machine.

**Important:** Do not commit your real API key to a public GitHub repository. For a more secure implementation, load the key from an environment variable instead of hardcoding it.

### Step 5: Run the Application

Execute the following command from the project directory:

```bash
python "LLM First Project.py"
```

If necessary, use:

```bash
python3 "LLM First Project.py"
```

Once the program starts, enter a prompt when the terminal asks for input. The generated answer will appear below the input prompt.

## How to Use the Chatbot

The application accepts one prompt per execution.

### Example

```text
Confused? Perfect. I’m here. 😂: What is Artificial Intelligence?

LLM Response:
Artificial Intelligence is a field of computer science
that focuses on building systems capable of performing
tasks that typically require human intelligence.
```

The example response is illustrative. Actual answers may differ depending on the prompt and model output.

### Example Prompts to Try

You can experiment with prompts such as:

- What is Artificial Intelligence?
- Explain Python in simple English.
- What is a Large Language Model?
- Explain machine learning with an example.
- Write a simple Python program to add two numbers.
- Explain how APIs work.

These examples help demonstrate the chatbot's general-purpose text-generation capabilities.

## Understanding the Code

The main application is contained in `LLM First Project.py`.

### 1. Importing the Groq SDK

```python
from groq import Groq
```

This imports the `Groq` client class required to communicate with the Groq API.

### 2. Initializing the Client

```python
client = Groq(
    api_key="ADD YOUR API KEY"
)
```

The client uses the API key to authenticate requests. Replace the placeholder with a valid key locally before running the application.

### 3. Accepting User Input

```python
prompt = input("Confused? Perfect. I’m here. 😂: ")
```

The `input()` function accepts a message from the user and stores it in the `prompt` variable.

### 4. Sending a Request to the Model

```python
response = client.chat.completions.create(
    model="openai/gpt-oss-20b",
    messages=[
        {
            "role": "user",
            "content": prompt
        }
    ]
)
```

This sends the user's prompt to the configured model through the Groq API.

The `messages` list contains the user's message. The role `"user"` identifies the message as input from the user.

### 5. Displaying the Generated Response

```python
print("\nLLM Response:")
print(response.choices[0].message.content)
```

The first line prints a heading. The second extracts and displays the generated response text.

## API Integration

This project uses the Groq Python SDK and the chat completions interface.

Official resources:

- [Groq Console](https://console.groq.com/)
- [Groq Documentation](https://console.groq.com/docs)
- [Groq Python SDK](https://github.com/groq/groq-python)
- [Groq API Reference](https://console.groq.com/docs/api-reference)

### Model Configuration

The current source code specifies:

```python
model="openai/gpt-oss-20b"
```

The model name identifies the model requested by the application. Model availability and API support can change, so consult the official Groq documentation if the API returns a model-related error.

## Security Best Practices

API keys are private credentials and should be handled carefully.

- Never publish your real API key in source code.
- Never upload a file containing your API key to a public repository.
- Use an environment variable or a local `.env` file for credentials.
- Add secret files to `.gitignore`.
- If a key is accidentally exposed, revoke it and create a replacement.
- Avoid sharing confidential or sensitive personal information with AI services.

For this beginner project, the current source code uses a placeholder that must be replaced locally. Environment-based configuration is a recommended improvement for future development.

## Troubleshooting

### 1. `ModuleNotFoundError: No module named 'groq'`

Install the missing dependency:

```bash
python -m pip install groq
```

Make sure you install the package into the same Python environment used to run the program.

### 2. Authentication Error

Check that the API key is valid, has not been revoked, and is correctly configured.

### 3. Model Error

Verify that the configured model is available to your Groq API account. Refer to the official model documentation for current availability.

### 4. Connection Error

Check your internet connection and try again. Temporary service issues may also affect API requests.

### 5. API Usage Limit

Check the usage limits and account status shown in the Groq Console.

## Current Limitations

This is an early-stage learning project with a deliberately simple implementation.

- Accepts one prompt per execution.
- Does not maintain conversation history between messages.
- Does not provide a graphical user interface.
- Requires internet access to communicate with the API.
- Depends on API availability and applicable usage limits.
- Does not currently implement custom error handling or response streaming.

## Future Improvements

Potential enhancements include:

- Maintaining multi-turn conversation history.
- Adding error handling for failed API requests.
- Loading API keys from environment variables.
- Adding a graphical or web-based interface.
- Allowing configurable model selection.
- Adding conversation reset functionality.
- Supporting response streaming.
- Creating a chat history export feature.

These are possible future improvements and are not claimed as existing features.

## Learning Objectives

This project provides practical experience with:

- Python programming and user input.
- API clients and HTTP-based service integration.
- Large Language Models (LLMs).
- Prompt-based text generation.
- AI application workflows.
- Secure configuration practices.
- Building a foundation for more advanced Generative AI projects.

## Author

**Muhammad Musab**

GitHub: [muhammad-musab03](https://github.com/muhammad-musab03)

## License

No license has currently been specified for this repository. If you intend to allow others to reuse, modify, or distribute this project, consider adding an appropriate open-source license.

---

**Project Purpose:** This repository is a hands-on learning project created to explore Python, Large Language Models, and API-based Generative AI applications.
