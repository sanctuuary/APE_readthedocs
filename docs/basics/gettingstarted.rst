My first APE run
================

Automated workflow composition with APE can be performed through its 
command line interface (`CLI <../specifications/cli.html>`_), its application programming interface 
(`java API <../specifications/java.html>`_) or the RESTful API (`RESTful APE <../restful-ape/introduction.html>`_). 
The CLI provides a simple means to interact and experiment 
with the framework, while the java API provides more flexibility and control over 
the synthesis process. It can be used to integrate APE’s functionality 
into other systems. Finally, the RESTful API provides an interface for users to 
engage with APE's automated pipeline exploration capabilities through HTTP requests. RESTful API is also provided as a Docker container for easy deployment and management.

My first APE run
^^^^^^^^^^^^^^^^

The first APE run is demonstrated using the CLI. The following steps guide you through the process of setting up and running APE on a simple example.

Get the latest version of `APE_UseCases <https://github.com/sanctuuary/APE_UseCases>`_ 
by either `downloading the main <https://github.com/sanctuuary/APE_UseCases/archive/main.zip>`_
(zip) or cloning the repository: 

.. .. code-block:: shell
.. 
..     git clone git@github.com:sanctuuary/APE_UseCases.git

.. or

.. code-block:: shell

    git clone https://github.com/sanctuuary/APE_UseCases.git


Download the latest version of `APE-2.3.0-executable.jar <https://repo1.maven.org/maven2/io/github/sanctuuary/APE/2.3.0/APE-2.3.0-executable.jar>`_ 
and add it to the root of the project (``~/git/APE_UseCases``).
Navigate to the root of the project and execute the jar with an 
argument that is a (relative) path to the configuration file.

.. code-block:: shell

    cd ~/git/APE_UseCases
    java -jar APE-2.3.0-executable.jar ImageMagick/Example1/config.json

See `Use cases and Demos <../demo/demo-overview.html>`_ for more information about the results 
and on how to execute the composed workflow.
