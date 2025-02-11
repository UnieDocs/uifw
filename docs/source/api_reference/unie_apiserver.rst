.. _unie_apiserver:

API Reference
=============

This document details the OpenAI-compatible API endpoints, their functionalities, and expected request/response formats.

OpenAI API Server Documentation
-------------------------------

This API provides RESTful services including:
- **Chat Completions**
- **Completions**
- **Embeddings**

## Base URL
```
http://localhost:8000/v1
```

Authentication
~~~~~~~~~~~~~~

To access the API, provide a Bearer token in the `Authorization` header. The API key validation will reject unauthorized requests if API keys are configured.

```http
Authorization: Bearer YOUR_API_KEY
```

List Available Models
~~~~~~~~~~~~~~~~~~~~~

**Endpoint:**
`GET /v1/models`

**Description:**
Fetches a list of all available models for completion and embeddings.

**Response:**

.. code-block:: python

    {
      "data": [
        {
          "id": "model_name",
          "root": "model_name",
          "permission": [/* permissions details */]
        }
      ]
    }

Create Chat Completion
~~~~~~~~~~~~~~~~~~~~~~

**Endpoint:**
`POST /v1/chat/completions`

**Description:**
Generates a completion for a given chat prompt.

**Request:**

.. code-block:: python

    {
      "model": "model_name",
      "messages": [
        {"role": "system", "content": "You are a helpful assistant."},
        {"role": "user", "content": "Tell me a joke."}
      ],
      "temperature": 0.7,
      "top_p": 0.9,
      "n": 1,
      "max_tokens": 100,
      "stream": false
    }

**Response:**

.. code-block:: python

    {
      "model": "model_name",
      "choices": [
        {
          "message": {
            "role": "assistant",
            "content": "Why don't skeletons fight each other? They don't have the guts."
          },
          "index": 0,
          "finish_reason": "stop"
        }
      ],
      "usage": {
        "prompt_tokens": 10,
        "completion_tokens": 20,
        "total_tokens": 30
      }
    }

Create Completion
~~~~~~~~~~~~~~~~~

**Endpoint:**
`POST /v1/completions`

**Description:**
Generates a text completion based on the provided prompt.

**Request:**

.. code-block:: python

    {
      "model": "model_name",
      "prompt": "Once upon a time",
      "max_tokens": 100,
      "temperature": 0.7,
      "top_p": 0.9,
      "n": 1,
      "stream": false
    }

**Response:**

.. code-block:: python

    {
      "model": "model_name",
      "choices": [
        {
          "text": " there was a princess who lived in a castle.",
          "index": 0,
          "finish_reason": "stop"
        }
      ],
      "usage": {
        "prompt_tokens": 5,
        "completion_tokens": 10,
        "total_tokens": 15
      }
    }

Create Embeddings
~~~~~~~~~~~~~~~~~

**Endpoint:**
`POST /v1/embeddings`

**Description:**
Generates embeddings for the input text.

**Request:**

.. code-block:: python

    {
      "model": "model_name",
      "input": ["The quick brown fox jumps over the lazy dog."]
    }

**Response:**

.. code-block:: python

    {
      "data": [
        {
          "object": "embedding",
          "embedding": [/* embedding values */],
          "index": 0
        }
      ],
      "model": "model_name",
      "usage": {
        "prompt_tokens": 9,
        "total_tokens": 9
      }
    }

Error Handling
~~~~~~~~~~~~~~

The API responds with error messages in case of invalid requests or issues during processing. The error message follows this structure:

.. code-block:: python

    {
      "error": {
        "message": "Error description",
        "type": "invalid_request_error",
        "param": "parameter_name",
        "code": "error_code"
      }
    }

.. note::

    - All models available for completion, chat, and embedding are listed via the `/v1/models` endpoint.
    - For streaming responses, use the `stream` parameter in both `/v1/completions` and `/v1/chat/completions`. The API will return responses in the event-stream format.
    - For additional information, refer to the official [OpenAI API documentation](https://platform.openai.com/docs/api-reference).
