.. _unie_apiserver:

UnieAPIServer
=============

OpenAI compatible API service of UnieInfra.


Initiate the service
--------------------

Before proceeding, ensure that you have the following:

1. **System Requirements**: Verify that the environment meets all technical requirements outlined in [installation](../getting_started/installation.rst).
2. **License Key**: Obtain a valid license key.

## Steps

1. Create unie_apiserver.yaml

.. code-block:: console

    version: '3.8'
    services:
        unie_apiserver:
            container_name: "unie_apiserver"
            environment:
                UNIEAI_LICENSE_KEY: ${UNIEAI_LICENSE_KEY}
            build: ./app/openai_api_server/
            ports:
                - "8080:8080"

2. Start-up

.. code-block:: console

    $ export UNIEAI_LICENSE_KEY="Your license key obtained from UnieAI"
    $ docker compose -f unie_apiserver.yml up unie_apiserver -d

## Troubleshooting
