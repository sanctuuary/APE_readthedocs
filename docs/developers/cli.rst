APE from Command Line
=====================

.. important::
    APE v2.4.0 is not yet released, but a beta version is available for testing `here <https://github.com/sanctuuary/APE_readthedocs/blob/v2.4/files/APE-2.4.0-dev2-executable.jar>`_ .

Overview
--------
The APE command line tool allows users to execute automated workflow composition processes using different methods. Since version 2.4 APE supports three distinct methods: **synthesis**, **convert-tools**, and **bio.tools**.

The APE command line tool is distributed as an executable JAR file, which can be downloaded from the `Maven repository <https://mvnrepository.com/artifact/io.github.sanctuuary/APE>`_. Select the `latest release <https://mvnrepository.com/artifact/io.github.sanctuuary/APE/latest>`_ and download the executable JAR file. Under the `Files` section click `View All` to see the available files. In the list of files you will find the `APE-<version>-executable.jar` file. Download the file to your local machine.

Requirements
^^^^^^^^^^^^
To run APE v2.4 or higher you need to have `Java 17 
<https://www.oracle.com/java/technologies/javase/jdk17-archive-downloads.html>`_ 
(or higher) installed on your system (use the command ``$ java -version`` 
to check your local version). 

.. note::
    APE v2.4+ is required to run the CLI using `[method]` tag. For older versions, the method tag is not required, and `synthesis` is the default method.

Usage
-----

To run the APE v2.4+ executable JAR, use the following command:

.. code-block:: shell

    java -jar APE-2.4.0-executable.jar [method] [options]

Where `[method]` can be one of the following:

- `synthesis` - see :ref:`synthesis`
- `pull-a-tool` - see :ref:`pull-a-tool`
- `convert-tools` - see :ref:`convert-tools`
- `bio.tools` - see :ref:`bio.tools`

Methods
-------

.. _synthesis:
Synthesis
^^^^^^^^^

This method is the primary function of the APE tool, and it requires a configuration file as input.
The method executed the synthesis based on the provided configuration file.

Usage
"""""

.. code-block:: shell

    java -jar APE-<version>-executable.jar synthesis [path-to-configuration.json]

APE v2.4.0 also supports the legacy method of running synthesis using the following command:

.. code-block:: shell

    java -jar APE-<version>-executable.jar [path-to-configuration.json]

Parameters
""""""""""

- `[path-to-configuration.json]`: Only one argument is expected, which is the path to the configuration JSON file. In case the configuration file name is not provided, the tool will look for a file named `config.json` in the current directory. The path can be local or remote (URL).

Example
"""""""

.. code-block:: shell

    java -jar APE-2.4.0-executable.jar synthesis ImageMagick/Example1/config.json


.. _pull-a-tool:
Pull a Tool

Fetches a tool from bio.tools using the bio.tools API and converts it to APE-compatible tool annotation format and generates the initial CWL configuration file.

Usage
"""""

.. code-block:: shell

    java -jar APE-<version>-executable.jar pull-a-tool biotoolsID


Parameters
""""""""""

- `biotoolsID`: A string containing the bio.tools ID of the tool to be fetched. The bio.tools ID is the unique identifier for a tool in the bio.tools database. 


.. note::
    **How to obtain `biotoolsIDs`**

    The `biotoolsID` for each tool can be obtained from bio.tools. For example, the `biotoolsID` for the tool `comet <https://bio.tools/comet>`_ is `comet`. It is visible in the URL of the tool page. Alternatively, you can use bio.tools REST API to fetch the `biotoolsID` for a tool, see `comet entry <https://bio.tools/api/tool/comet>`_.

Example
"""""""

.. code-block:: shell

    java -jar APE-2.4.0-executable.jar pull-a-tool comet


.. _convert-tools:
Convert Tools
^^^^^^^^^^^^^

Retrieves tools from bio.tools using the bio.tools API and converts them to APE-compatible tool annotation format.

Usage
"""""

.. code-block:: shell

    java -jar APE-<version>-executable.jar convert-tools [path-to-biotoolsIDs.json]

Parameters
""""""""""

- `[path-to-biotoolsIDs.json]`: Only one argument is expected, which is the path to the file where the list of `biotoolsIDs` is stored (as JSON array). See the note above on how to obtain `biotoolsIDs`.

An example of the `biotoolsIDs.json` file is as follows:

.. code-block:: json

    [
        "comet",
        "peptideprophet",
        "proteinprophet",
        "stpeter",
        "mzrecal"
    ]

The bio.tools API used to fetch the tools is agnostic to the case of the tool names. For example, the tool `comet` can be written as `Comet`. 

Example
"""""""

.. code-block:: shell

    java -jar APE-2.4.0-executable.jar convert-tools tools/bioToolsIDs.json


.. _bio.tools:
Full bio.tools
^^^^^^^^^^^^^^

Fetches all well-annotated the tools from bio.tools using the bio.tools API.

Usage
"""""

.. code-block:: shell

    java -jar APE-<version>-executable.jar bio.tools

**Notes:**

- This method does not require any additional parameters. It will fetch the all the tools from bio.tools that are well-annotated, i.e., they have at least one input and one output fully specified (i.e., with a data type and a format). The tools will be converted to APE-compatible tool annotation format and stored in the `tools.json` file in the current directory.

Example
"""""""

.. code-block:: shell

    java -jar APE-2.4.0-executable.jar bio.tools


Error Handling
--------------
If no valid method is provided or if the required arguments are not supplied, an error message will be logged indicating the invalid input.

For more details regarding the `synthesis`, refer to the `setup.html#configuration-file` for JSON configuration file specifications.
