.. _unie_worker:

UnieWorker
==========

Worker service of UnieInfra.
The type of worker could be llm, embedding, etc.


Initiate the service
--------------------

Before proceeding, ensure that you have the following:

1. **System Requirements**: Verify that the environment meets all technical requirements outlined in [installation](../getting_started/installation.rst).
2. **License Key**: Obtain a valid license key.

## Steps

1. Create unie_worker.yaml

.. code-block:: console

    version: '3.8'
    services:
        unie_worker:
            container_name: "unie_worker"
            entrypoint: ["python3.11"]
            environment:
               UNIEAI_LICENSE_KEY: ${UNIEAI_LICENSE_KEY}
               CUDA_VISIBLE_DEVICES: "0"
            build: .
            command:
               [
               "-m", "geninfra.serve.fast_worker",
               "--model-path", "/weight/llm/unieai/aqua/",
               "--model-names", "unieai/aqua",
               "--controller-address", "http://controller:8081",
               "--worker-address", "http://unie_worker:5051",
               "--num-gpus", "1",
               "--host", "0.0.0.0",
               "--port", "5051",
               "--gpu-memory-utilization", "0.9",
               "--enforce-eager",
               ]
            volumes:
               - "./weight:/weight"
            deploy:
               resources:
                  reservations:
                     devices:
                        - capabilities:
                           - gpu

2. Create unie_embed.yaml

.. code-block:: console

    version: '3.8'
    services:
        unie_embed:
            container_name: "unie_embed"
            entrypoint: ["python3.11"]
            environment:
               UNIEAI_LICENSE_KEY: ${UNIEAI_LICENSE_KEY}
               CUDA_VISIBLE_DEVICES: "0"
            build: .
            command:
               [
               "-m", "geninfra.serve.model_worker",
               "--model-path", "/weight/embed/GanymedeNil/text2vec-large-chinese",
               "--model-names", "GanymedeNil/text2vec-large-chinese",
               "--controller-address", "http://controller:8081",
               "--worker-address", "http://unie_embed:5001",
               "--num-gpus", "1",
               "--host", "0.0.0.0",
               "--port", "5001",
               ]
            volumes:
               - "./weight:/weight"
            deploy:
               resources:
                  reservations:
                     devices:
                        - capabilities:
                           - gpu

2. Start-up

.. code-block:: console

    $ export UNIEAI_LICENSE_KEY="Your license key obtained from UnieAI"
    $ docker compose -f unie_worker.yml up unie_worker -d
    $ docker compose -f unie_embed.yml up unie_embed -d

## Troubleshooting
