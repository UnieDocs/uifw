.. _unie_license:

UnieLicense
===========

UnieInfra requires a valid license key to operate.
Please reach out to ``contact@unieai.com`` to obtain a ``unique ID`` for the continued operation of our product.

Register Environment
--------------------

Before proceeding with the registration, ensure that you have the following:

1. **System Requirements**: Verify that the environment meets all technical requirements outlined in [installation](../getting_started/installation.rst).
2. **Unique ID**: Obtain a unique identifier.

## Steps

1. Create unie_license.yaml

.. code-block:: console

    version: '3.8'
    services:
        unie_license:
            container_name: "unie_license"
            environment:
                UNIEAI_UNIQUE_ID: ${UNIEAI_UNIQUE_ID}
            build: ./app/license/

2. Obtain a license key

.. code-block:: console

    $ export UNIEAI_UNIQUE_ID="Your unique identifier obtained from UnieAI"
    $ docker compose -f unie_license.yml up unie_license
    > python resiter.py
    "Your license key will be located here."_

.. note::

    ``>`` means the command in executed in the docker

## Troubleshooting
