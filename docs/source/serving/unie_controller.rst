.. _unie_controller:

UnieController
==============

Controller of UnieInfra.


Initiate the service
--------------------

Before proceeding, ensure that you have the following:

1. **System Requirements**: Verify that the environment meets all technical requirements outlined in [installation](../getting_started/installation.rst).
2. **License Key**: Obtain a valid license key.

## Steps

1. Create unie_controller.yaml

.. code-block:: console

    version: '3.8'
    services:
        unie_controller:
            container_name: "unie_controller"
            environment:
                UNIEAI_LICENSE_KEY: ${UNIEAI_LICENSE_KEY}
            build: ./app/controller/
            ports:
                - "8081:8081"

2. Start-up

.. code-block:: console

    $ export UNIEAI_LICENSE_KEY="Your license key obtained from UnieAI"
    $ docker compose -f unie_controller.yml up unie_controller -d

## Troubleshooting
