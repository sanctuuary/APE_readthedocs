Getting Started with APE
========================

Automated workflow composition with APE can be performed through its 
command line interface `(CLI) <../specifications/cli.html>`_ or its application programming interface 
`(API) <../specifications/java.html>`_. While the CLI provides a simple means to interact and experiment 
with the system, the API provides more flexibility and control over 
the synthesis process. It can be used to integrate APE’s functionality 
into other systems.

My first APE run
^^^^^^^^^^^^^^^^

.. code-block:: shell

    git clone git@github.com:sanctuuary/APE_UseCases.git

or

.. code-block:: shell

    git clone https://github.com/sanctuuary/APE_UseCases.git

Download the latest version of `APE-<version>-executable.jar <https://repo.maven.apache.org/maven2/io/github/sanctuuary/APE/1.0.1/APE-1.0.1-executable.jar>`_ and add it to the APE_UseCases directory (``~/git/APE_UseCases``)

.. code-block:: shell

    cd ~/git/APE_UseCases
    java -jar APE-1.0.1-executable.jar ImageMagick/Example1/config.json

See `ImageMagick: Example 1 <../demo/imagemagick.html>`_ for more information about the results and on how to execute the composed workflow.