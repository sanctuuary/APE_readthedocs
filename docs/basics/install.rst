Install
=======

Requirements
^^^^^^^^^^^^^^
To `run <../specifications/cli.html>`_ APE you need to have `Java 1.8 
<https://www.oracle.com/java/technologies/javase/javase-jdk8-downloads.html>`_ 
(or higher) installed on your system (use command ``$ java -version`` 
to check your local version). 

To `build <install.html#build-ape-from-source-using-maven>`_ APE from source, 
`Maven 3.3+ <https://maven.apache.org/download.cgi>`_ has to be installed 
as well (use command ``$ mvn -version`` to check your local version).

.. tip::
    Building APE from source is not required to run it, as the latest stable 
    version is available at `maven repository <https://mvnrepository.com/artifact/io.github.sanctuuary/APE/latest>`_.
    Download the exectable jar directly from `Releases <install.html#releases>`_.

Releases
^^^^^^^^
+------------+------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------+
| Date       | Version                                                                      | Download                                                                                                      |
+------------+------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------+
| 15-07-2020 | `1.0.1 <https://mvnrepository.com/artifact/io.github.sanctuuary/APE/1.0.1>`_ | `jar <https://repo.maven.apache.org/maven2/io/github/sanctuuary/APE/1.0.1/APE-1.0.1.jar>`_,                   |
|            |                                                                              | `executable <https://repo.maven.apache.org/maven2/io/github/sanctuuary/APE/1.0.1/APE-1.0.1-executable.jar>`_, |
|            |                                                                              | `javadoc <https://repo.maven.apache.org/maven2/io/github/sanctuuary/APE/1.0.1/APE-1.0.1-javadoc.jar>`_,       |
|            |                                                                              | `sources <https://repo.maven.apache.org/maven2/io/github/sanctuuary/APE/1.0.1/APE-1.0.1-sources.jar>`_        |
+------------+------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------+

Add APE to your project
^^^^^^^^^^^^^^^^^^^^^^^
To add a dependency on APE, use the following:

.. tabs::

    .. tab:: Maven

        .. code-block:: xml

            <!-- https://mvnrepository.com/artifact/io.github.sanctuuary/APE -->
            <dependency>
                <groupId>io.github.sanctuuary</groupId>
                <artifactId>APE</artifactId>
                <version>1.0.1</version>
            </dependency>

    .. tab:: Gradle

        .. code-block:: bash

            // https://mvnrepository.com/artifact/io.github.sanctuuary/APE
            compile group: 'io.github.sanctuuary', name: 'APE', version: '1.0.1'

    .. tab:: Ivy

        .. code-block:: xml

            <!-- https://mvnrepository.com/artifact/io.github.sanctuuary/APE -->
            <dependency org="io.github.sanctuuary" name="APE" rev="1.0.1"/>

.. note:: 
    For information regarding dependencies, we refer to the `APE maven repository 
    <https://mvnrepository.com/artifact/io.github.sanctuuary/APE/latest>`_.

Build APE from source (using Maven)
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
From the project root, simply launch

.. code-block:: shell

    $ mvn -DskipTests=true install

to build the APE modules from the source tree and the built files will 
be generated under the ``/target`` directory. All the dependencies 
will be gathered by Maven and the following stand-alone module will be 
generated: ``APE-<version>-executable.jar``
