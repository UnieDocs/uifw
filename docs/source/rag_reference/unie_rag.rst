.. _unie_rag:

RAG Reference
=============

This document details the RAG API endpoints, their functionalities, and expected request/response formats.

RAR Documentation
-----------------

This API provides RESTful services including:
- **Rag Chat**
- **Rag Search**
- **Retrieve**

## Base URL
```
http://localhost:8000/v1
```

Get Rag Chat
~~~~~~~~~~~~

**Endpoint:**
`POST /v1/rag/chat`

**Description:**
Get Rag Chat.

**Request:**

.. code-block:: python

    {
        "tags": [
            "rag"
        ],
        "summary": "Get Rag Chat",
        "operationId": "get_rag_chat_v1_rag_chat_post",
        "requestBody": {
            "content": {
                "application/json": {
                    "schema": {
                        "$ref": "#/components/schemas/Body_get_rag_chat_v1_rag_chat_post"
                    }
                }
            },
            "required": true
        }
    }

**Response:**

.. code-block:: python

    {
        "200": {
            "description": "Successful Response",
            "content": {
                "application/json": {
                    "schema": {
                        "$ref": "#/components/schemas/RetrievalResultSchema"
                    }
                }
            }
        },
        "422": {
            "description": "Validation Error",
            "content": {
                "application/json": {
                    "schema": {
                        "$ref": "#/components/schemas/HTTPValidationError"
                    }
                }
            }
        }
    }

Get Rag Search
~~~~~~~~~~~~~~

**Endpoint:**
`POST /v1/rag/search`

**Description:**
Get Rag Search.

**Request:**

.. code-block:: python

    {
        "tags": [
            "rag"
        ],
        "summary": "Get Rag Search",
        "operationId": "get_rag_search_v1_rag_search_post",
        "requestBody": {
            "content": {
                "application/json": {
                    "schema": {
                        "$ref": "#/components/schemas/Body_get_rag_search_v1_rag_search_post"
                    }
                }
            },
            "required": true
        }
    }

**Response:**

.. code-block:: python

    {
        "200": {
            "description": "Successful Response",
            "content": {
                "application/json": {
                    "schema": {
                        "$ref": "#/components/schemas/RetrievalResultSchema"
                    }
                }
            }
        },
        "422": {
            "description": "Validation Error",
            "content": {
                "application/json": {
                    "schema": {
                        "$ref": "#/components/schemas/HTTPValidationError"
                    }
                }
            }
        }
    }

Get Retrieve
~~~~~~~~~~~~

**Endpoint:**
`POST /v1/rag/retrieve`

**Description:**
Get Retrieve.

**Request:**

.. code-block:: python

    {
        "tags": [
            "rag"
        ],
        "summary": "Get Retrieve",
        "operationId": "get_retrieve_v1_rag_retrieve_post",
        "requestBody": {
            "content": {
                "application/json": {
                    "schema": {
                        "$ref": "#/components/schemas/Body_get_retrieve_v1_rag_retrieve_post"
                    }
                }
            },
            "required": true
        }
    }

**Response:**

.. code-block:: python

    {
        "200": {
            "description": "Successful Response",
            "content": {
                "application/json": {
                    "schema": {
                        "$ref": "#/components/schemas/RetrievalResultSchema"
                    }
                }
            }
        },
        "422": {
            "description": "Validation Error",
            "content": {
                "application/json": {
                    "schema": {
                        "$ref": "#/components/schemas/HTTPValidationError"
                    }
                }
            }
        }
    }
