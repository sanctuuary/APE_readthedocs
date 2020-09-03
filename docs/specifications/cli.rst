APE as a Command Line Tool
==========================

Run APE from the Command Line
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

`APE-1.0.1-executable.jar <https://repo.maven.apache.org/maven2/io/github/sanctuuary/APE/1.0.1/APE-1.0.1-executable.jar>`_ 
is available in `maven repository <https://mvnrepository.com/artifact/io.github.sanctuuary/APE/latest>`_.

When running APE-<version>-executable.jar from the command line, 
it requires a `JSON configuration <setup.html>`_ file given as a parameter 
and executes the automated workflow composition process accordingly:

.. code-block:: shell

    java -jar APE-<version>-executable.jar [path-to-ape-configuration]

