.. _installation:

Installation
============

uifw is the AI Inference Engine developed by UnieAI.

Requirements
------------

* **OS**: Linux
* **Python**: 3.9
* **GPU**: compute capability 7.0 or higher (e.g., V100, T4, RTX20xx, A100, L4, H100, etc.)
* **Network**: Ensure your environment can access the public network. After successfully deploying UnieInfra, the service can operate in a private network environment.

Pull Docker Images
~~~~~~~~~~~~~~~~~~


.. code-block:: console

    $ docker image pull unieai/uifw2

.. note::

    You will require a license key to operate the UnieInfra platform.
    The license key follows the format ``UUUUUU-NNNNNN-IIIIII-EEEEEE-XXXXXX-AI``.
