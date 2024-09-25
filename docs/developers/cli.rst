APE Command Line Tool Documentation
=====================================

Overview
--------
The APE command line tool allows users to execute automated workflow composition processes using different methods. This tool supports three distinct methods: **synthesis**, **convert-tools**, and **bio.tools**.

Usage
-----
To run the APE executable JAR, use the following command:

.. code-block:: shell

    java -jar APE-<version>-executable.jar [method] [options]

Where `[method]` can be one of the following:

1. **synthesis**
2. **convert-tools**
3. **bio.tools**

Methods
-------


Synthesis
^^^^^^^^^

This method is the primary function of the APE tool, and it requires a configuration file as input.
The method executed the synthesis based on the provided configuration file.

**Usage:**

.. code-block:: shell

    java -jar APE-<version>-executable.jar synthesis [path-to-configuration.json]

APE v2.4.0 also supports the legacy method of running synthesis using the following command:

.. code-block:: shell

    java -jar APE-<version>-executable.jar [path-to-configuration.json]

**Parameters:**

- `args`: An array of strings containing the arguments provided to the method. Only one argument is expected, which is the path to the configuration JSON file. In case the configuration file name is not provided, the tool will look for a file named `config.json` in the current directory.

Convert Tools
^^^^^^^^^^^^^

Retrieves tools from bio.tools using the bio.tools API and converts them to APE-compatible tool annotation format.

**Usage:**

.. code-block:: shell

    java -jar APE-<version>-executable.jar convert-tools [path-to-biotoolsIDs.json]

**Parameters:**

- `args`: An array of strings containing the arguments provided to the method. Only one argument is expected, which is the path to the file where the biotoolsIDs are stored.

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


**How to obtain `biotoolsIDs`**

The `biotoolsID` for each tool can be obtained from bio.tools. For example, the `biotoolsID` for the tool `comet <https://bio.tools/comet>`_ is `comet`. It is visible in the URL of the tool page. Alternatively, you can use bio.tools REST API to fetch the `biotoolsID` for a tool, see `comet entry <https://bio.tools/api/tool/comet>`_.



Full bio.tools
^^^^^^^^^^^^^^

Fetches all well-annotated the tools from bio.tools using the bio.tools API.

**Usage:**

.. code-block:: shell

    java -jar APE-<version>-executable.jar bio.tools

**Notes:**

- This method does not require any additional parameters. It will fetch the all the tools from bio.tools that are well-annotated, i.e., they have at least one input and one output fully specified (i.e., with a data type and a format). The tools will be converted to APE-compatible tool annotation format and stored in the `tools.json` file in the current directory.

Examples
--------
Here are some example commands to illustrate the usage of each method:

1. To execute synthesis with a configuration file:

.. code-block:: shell

    java -jar APE-2.4.0-executable.jar synthesis ImageMagick/Example1/config.json

2. To convert tools:

.. code-block:: shell

    java -jar APE-2.4.0-executable.jar convert-tools tools/bioToolsIDs.json

3. To fetch tools from bio.tools:

.. code-block:: shell

    java -jar APE-2.4.0-executable.jar bio.tools

Error Handling
--------------
If no valid method is provided or if the required arguments are not supplied, an error message will be logged indicating the invalid input.

For more details regarding the `synthesis`, refer to the `setup.html#configuration-file` for JSON configuration file specifications.
