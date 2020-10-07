Getting Started with APE
========================

Automated workflow composition with APE can be performed through its 
command line interface (`CLI <../specifications/cli.html>`_) or its application programming interface 
(`API <../specifications/java.html>`_). While the CLI provides a simple means to interact and experiment 
with the framework, the API provides more flexibility and control over 
the synthesis process. It can be used to integrate APE’s functionality 
into other systems.

My first APE run
^^^^^^^^^^^^^^^^

Get the latest version of `APE_UseCases <https://github.com/sanctuuary/APE_UseCases>`_ 
by either `downloading the master <https://github.com/sanctuuary/APE_UseCases/archive/master.zip>`_
(zip) or cloning the repository: 

.. .. code-block:: shell
.. 
..     git clone git@github.com:sanctuuary/APE_UseCases.git

.. or

.. code-block:: shell

    git clone https://github.com/sanctuuary/APE_UseCases.git


Download the latest version of `APE-1.0.2-executable.jar <https://repo.maven.apache.org/maven2/io/github/sanctuuary/APE/1.0.2/APE-1.0.2-executable.jar>`_ 
and add it to the root of the project (``~/git/APE_UseCases``).
Navigate to the root of the project and execute the jar with an 
argument that is a (relative) path to the configuration file.

.. code-block:: shell

    cd ~/git/APE_UseCases
    java -jar APE-1.0.2-executable.jar ImageMagick/Example1/config.json

See `Use cases and Demos <../demo/demo-overview.html>`_ for more information about the results 
and on how to execute the composed workflow.
