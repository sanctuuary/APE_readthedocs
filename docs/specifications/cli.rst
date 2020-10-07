APE as a Command Line Tool
==========================

Run APE from the Command Line
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

`APE-1.0.2-executable.jar <https://repo.maven.apache.org/maven2/io/github/sanctuuary/APE/1.0.2/APE-1.0.2-executable.jar>`_ 
is available in `maven repository <https://mvnrepository.com/artifact/io.github.sanctuuary/APE/latest>`_.

When running APE-<version>-executable.jar from the command line, 
it requires a `JSON configuration <setup.html#configuration-file>`_ file given as a parameter 
and executes the automated workflow composition process accordingly:

.. code-block:: shell

    java -jar APE-<version>-executable.jar [path-to-ape-configuration]

As an example, if you would download the 
`APE-1.0.2-executable.jar <https://repo.maven.apache.org/maven2/io/github/sanctuuary/APE/1.0.2/APE-1.0.2-executable.jar>`_ 
to the root of APE_UseCases repository on your local machine, 
you could run this demo by executing the following command:

.. code-block:: shell

    <~/git/APE_UseCases> java -jar APE-1.0.2-executable.jar ImageMagick/Example1/config.json
    
