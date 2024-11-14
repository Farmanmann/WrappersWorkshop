# Large Language Model (LLM) Wrapper from Scratch using OpenAI API

This project demonstrates a custom-built Python wrapper around OpenAI's Large Language Model (LLM) API, encapsulating key functionalities for generating dynamic, memory-enhanced conversational responses. The wrapper effectively manages conversation history, prioritizes important messages, and handles errors gracefully, ensuring robust and efficient API usage.

I presented this project to colleagues in my organization to deepen their understanding of LLMs and demonstrate the potential applications of these powerful models in real-world scenarios.

## Project Overview

The **LLM Wrapper** provides a high-level interface to OpenAI's models (e.g., `gpt-3.5-turbo`). Designed for both simplicity and flexibility, it includes features such as memory management, retry logic, message prioritization, and dynamic chunking of conversations. This framework supports interactive, memory-rich conversations that can be adapted for chatbots, customer support tools, or educational resources.

### Key Features

- **Flexible Memory Management**: Retains and prioritizes conversation history up to a customizable token limit, allowing context-aware responses.
- **Error Handling & Retries**: Implements robust error-handling mechanisms to gracefully manage API rate limits and unexpected interruptions.
- **Dynamic Chunking**: Splits long conversation threads into manageable parts, enabling smooth processing within token constraints.
- **Configurable**: Parameters like model type, token limits, and memory settings can be adjusted dynamically.

### Learning Outcomes and Teaching Highlights

Through this project, I introduced colleagues to the following concepts:

1. **Understanding Large Language Models (LLMs)**: Provided insights into how LLMs like GPT-3.5 work, focusing on token limits, language generation, and context retention.
2. **API Wrapper Design**: Explained the design principles behind creating robust, reusable, and flexible API wrappers.
3. **Error Handling and Rate Limiting**: Discussed effective strategies to manage API constraints, emphasizing resilience in real-world applications.
4. **Real-world Applications of LLMs**: Demonstrated practical applications for chatbots, interactive learning tools, and other natural language processing use cases.

## Getting Started

### Prerequisites

- Python 3.7+
- OpenAI API Key (required for access to OpenAI models)

### Installation

1. **Clone the repository**:
   ```bash
   git clone https://github.com/your-username/LLM-wrapper.git
   cd LLM-wrapper
2. **Set up your API key** Export your OpenAI key as an environment variable.
   (you will have to pay for your own OpenAI key to use any sort of AI, once you have got the key put it in the quotes)
   ```bash
   export OPENAI_API_KEY='your_api_key'

## Usage

### 1. Initialize the LLM Wrapper

The `LLMWrapper` lets you select between the chat and completion models. Initialize it by specifying the model type.

```python
from llm_wrapper import LLMWrapper, ChatMessage
```
# Initialize LLM wrapper with your choice of model ("chat" or "completion")
llm_wrapper = LLMWrapper(api_key="your_api_key", model_type="chat")  # Use "chat" for chat model, "completion" for completion model

### 2. Generate Responses Based on Model Choice

#### Using the Chat Model

If `model_type="chat"` is chosen, you can use chat-based interactions:

```python
# Define a list of messages for a conversation
messages = [ChatMessage(role="user", content="Hello, how can you help me today?")]

# Generate a response from the chat model
response = llm_wrapper.generate_response(messages)
print(response.choices[0].message.content)
```

if `model_type="chat"` is chosen, you can use chat-based interactions:

```python
# Define a prompt for a completion task
prompt = "Explain the concept of machine learning in simple terms."

# Generate a response from the completion model
response = llm_wrapper.generate_response(prompt)
print(response.choices[0].text.strip())
```

### 3. Configure Model and Memory Options

```python
# Switch between models
llm_wrapper.set_model("gpt-4")  # Example of changing the model dynamically

# Enable or disable memory for chat model
llm_wrapper.set_memory_usage(use_memory=True)
```

### 4. Manage Long Conversations and Prioritize Messages

```python
# Prioritize messages if certain ones need emphasis in the memory
prioritized_messages = llm_wrapper.prioritize_messages(messages)

# Split long conversations into chunks based on token limits
chunks = llm_wrapper.split_long_conversation(messages, max_tokens_per_chunk=500)
for chunk in chunks:
    response = llm_wrapper.generate_response(chunk)
    print(response.choices[0].message.content)
```

This is a workshop presented by Farman Ali for ACM Education on LLMs and Wrapper Methods. Please contact me if you need any support.

   
