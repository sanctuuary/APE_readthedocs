Install
=======

Requirements
^^^^^^^^^^^^^^
To run APE you need to have `Java 1.8 
<https://www.oracle.com/java/technologies/javase/javase-jdk8-downloads.html>`_ 
(or higher) installed on your system (use command ``$ java -version`` 
to check your local version). 

To build APE from source, 
`Maven 3.3+ <https://maven.apache.org/download.cgi>`_ has to be installed 
as well (use command ``$ mvn -version`` to check your local version).

Releases
^^^^^^^^

.. _1.0.1: https://mvnrepository.com/artifact/io.github.sanctuuary/APE/1.0.1
.. _1.0.2: https://mvnrepository.com/artifact/io.github.sanctuuary/APE/1.0.2

==========  =======  ========
Date        Version  Download
==========  =======  ========
15-07-2020  1.0.1_   `jar <https://repo.maven.apache.org/maven2/io/github/sanctuuary/APE/1.0.1/APE-1.0.1.jar>`__,
                     `executable <https://repo.maven.apache.org/maven2/io/github/sanctuuary/APE/1.0.1/APE-1.0.1-executable.jar>`__,
                     `javadoc <https://repo.maven.apache.org/maven2/io/github/sanctuuary/APE/1.0.1/APE-1.0.1-javadoc.jar>`__,
                     `sources <https://repo.maven.apache.org/maven2/io/github/sanctuuary/APE/1.0.1/APE-1.0.1-sources.jar>`__
----------  -------  --------
07-10-2020  1.0.2_   `jar <https://repo.maven.apache.org/maven2/io/github/sanctuuary/APE/1.0.2/APE-1.0.2.jar>`__,
                     `executable <https://repo.maven.apache.org/maven2/io/github/sanctuuary/APE/1.0.2/APE-1.0.2-executable.jar>`__,
                     `javadoc <https://repo.maven.apache.org/maven2/io/github/sanctuuary/APE/1.0.2/APE-1.0.2-javadoc.jar>`__,
                     `sources <https://repo.maven.apache.org/maven2/io/github/sanctuuary/APE/1.0.2/APE-1.0.2-sources.jar>`__
==========  =======  ========

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
                <version>1.0.2</version>
            </dependency>

    .. tab:: Gradle

        .. code-block:: bash

            // https://mvnrepository.com/artifact/io.github.sanctuuary/APE
            compile group: 'io.github.sanctuuary', name: 'APE', version: '1.0.2'

    .. tab:: Ivy

        .. code-block:: xml

            <!-- https://mvnrepository.com/artifact/io.github.sanctuuary/APE -->
            <dependency org="io.github.sanctuuary" name="APE" rev="1.0.2"/>

.. note:: 
    For information regarding dependencies (SBT, Grape, Buildr etc.), we refer to the `APE maven repository 
    <https://mvnrepository.com/artifact/io.github.sanctuuary/APE/latest>`_.

Build APE from source (using Maven)
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. tip::
    Building APE from source is not required to run it, as the latest stable 
    version is available at `maven repository <https://mvnrepository.com/artifact/io.github.sanctuuary/APE/latest>`_.
    Download the executable jar directly from `Releases <install.html#releases>`_.

From the project root, simply launch

.. code-block:: shell

    $ mvn -DskipTests=true install

to build the APE modules from the source tree. The built files will 
be generated under the ``/target`` directory. All the dependencies 
will be gathered by Maven and the following stand-alone module will be 
generated: ``APE-<version>-executable.jar``
