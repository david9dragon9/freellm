This is a helpful utility for calling LLM APIs and enforcing rate limits.

# Requirements
- openai
- google-generativeai
- concurrent
- dataclasses

# Usage
First, import functions:
```python
from llms import create_client, batch_call, call_llm
```

Then create a client:
```python
client = create_client(service="YOUR SERVICE", api_key="YOUR API KEY")
```

To call an LLM for a single request:
```python
results = call_llm(
    messages, # List of messages for requests. Can either be string if there is only one message (from the user), or a list of dicts (standard openai format).
    "MODEL NAME", #  (e.g. "Meta-Llama-3.1-8B-Instruct"),
    service="YOUR SERVICE",
    client=client,
)
```

To call an LLM for a batch of requests:
```python
results = batch_call(
    prompts, # List of messages for requests. Can either be list of strings if there is only one message (from the user), or a list of list of dicts (standard openai format).
    "MODEL NAME", #  (e.g. "Meta-Llama-3.1-8B-Instruct"),
    service="YOUR SERVICE",
    client=client,
    rpm=30 # requests per minute rate limit. Will be automatically enforced
)
```

# Supported Models

`freellm` supports the following platforms:
- openai
- sambanova
- groq
- together
- mistral
- glhf
- scaleway
- gemini

# Contact
Questions? Contact david9dragon9@gmail.com
