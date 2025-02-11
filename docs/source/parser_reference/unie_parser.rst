.. _unie_parser:

PARSER Reference
=============

This document details the PARSER API endpoints, their functionalities, and expected request/response formats.

PARSER Documentation
--------------------

This API provides RESTful services including:
- **Parser Info**
- **Document Parser Info**
- **Chunk Info**
- **Manual Document Parser**

## Base URL
```
http://localhost:8000/v1
```

Get Parser Info
~~~~~~~~~~~~~~~

**Endpoint:**
`GET /v1/parser/info`

**Description:**
Get Parser Info.

**Request:**

.. code-block:: python

    {
        "tags": [
            "parser"
        ],
        "summary": "Get Parser Info",
        "operationId": "get_parser_info_v1_parser_info_get"
    }


**Response:**

.. code-block:: python

    {
        "200": {
            "description": "Successful Response",
            "content": {
                "application/json": {
                    "schema": {
                        "$ref": "#/components/schemas/ParserSchema"
                    }
                }
            }
        }
    }

Get Document Parser Info
~~~~~~~~~~~~~~~~~~~~~~~~

**Endpoint:**
`GET /v1/parser/info/document/{doc_id}`

**Description:**
Get Document Parser Info.

**Parameters:**

* `doc_id` (string, required): The ID of the document.
* `page` (integer, optional): The page number. Defaults to 1.
* `page_size` (integer, optional): The page size. Defaults to 10.

**Request:**

.. code-block:: python

    {
        "tags": [
            "parser"
        ],
        "summary": "Get Document Parser Info",
        "operationId": "get_document_parser_info_v1_parser_info_document__doc_id__get",
        "parameters": [
            {
                "name": "doc_id",
                "in": "path",
                "required": true,
                "schema": {
                    "type": "string",
                    "format": "uuid",
                    "title": "Doc Id"
                }
            },
            {
                "name": "page",
                "in": "query",
                "required": false,
                "schema": {
                    "type": "integer",
                    "default": 1,
                    "title": "Page"
                }
            },
            {
                "name": "page_size",
                "in": "query",
                "required": false,
                "schema": {
                    "type": "integer",
                    "default": 10,
                    "title": "Page Size"
                }
            }
        ]
    }


**Response:**

.. code-block:: python

    {
        "200": {
            "description": "Successful Response",
            "content": {
                "application/json": {
                    "schema": {
                        "$ref": "#/components/schemas/DocumentParseStatus"
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

Get Chunk Info
~~~~~~~~~~~~~~

**Endpoint:**
`GET /v1/parser/info/chunk/{chunk_id}`

**Description:**
Get Chunk Info.

**Parameters:**

* `chunk_id` (string, required): The ID of the chunk.

**Request:**

.. code-block:: python

    {
        "tags": [
            "parser"
        ],
        "summary": "Get Chunk Info",
        "operationId": "get_chunk_info_v1_parser_info_chunk__chunk_id__get",
        "parameters": [
            {
                "name": "chunk_id",
                "in": "path",
                "required": true,
                "schema": {
                    "type": "string",
                    "format": "uuid",
                    "title": "Chunk Id"
                }
            }
        ]
    }

**Response:**

.. code-block:: python

    {
        "200": {
            "description": "Successful Response",
            "content": {
                "application/json": {
                    "schema": {
                        "$ref": "#/components/schemas/ChunkSchema"
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

Run Manual Document Parser
~~~~~~~~~~~~~~~~~~~~~~~~~~

**Endpoint:**
`PUT /v1/parser/run/document/{doc_id}`

**Description:**
Run Manual Document Parser.

**Parameters:**

* `doc_id` (string, required): The ID of the document.

**Request:**

.. code-block:: python

    {
        "tags": [
            "parser"
        ],
        "summary": "Run Manual Document Parser",
        "operationId": "run_manual_document_parser_v1_parser_run_document__doc_id__put",
        "parameters": [
            {
                "name": "doc_id",
                "in": "path",
                "required": true,
                "schema": {
                    "type": "string",
                    "format": "uuid",
                    "title": "Doc Id"
                }
            }
        ]
    }

**Response:**

.. code-block:: python

    {
        "200": {
            "description": "Successful Response",
            "content": {
                "application/json": {
                    "schema": {
                        "$ref": "#/components/schemas/DocumentParseStatus"
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
