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

Releases
^^^^^^^^
+------------+---------+---------------------------------------------------------------------------------------------------------------+
| Date       | Version | Download                                                                                                      |
+------------+---------+---------------------------------------------------------------------------------------------------------------+
| 15-07-2020 | 1.0.1   | `jar <https://repo.maven.apache.org/maven2/io/github/sanctuuary/APE/1.0.1/APE-1.0.1.jar>`_,                   |
|            |         | `executable <https://repo.maven.apache.org/maven2/io/github/sanctuuary/APE/1.0.1/APE-1.0.1-executable.jar>`_, |
|            |         | `javadoc <https://repo.maven.apache.org/maven2/io/github/sanctuuary/APE/1.0.1/APE-1.0.1-javadoc.jar>`_,       |
|            |         | `sources <https://repo.maven.apache.org/maven2/io/github/sanctuuary/APE/1.0.1/APE-1.0.1-sources.jar>`_        |
+------------+---------+---------------------------------------------------------------------------------------------------------------+

Add APE to your Maven project
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
To add a dependency on APE using Maven, use the following:

.. code-block:: xml

    <!-- https://mvnrepository.com/artifact/io.github.sanctuuary/APE -->
    <dependency>
        <groupId>io.github.sanctuuary</groupId>
        <artifactId>APE</artifactId>
        <version>1.0.1</version>
    </dependency>

For information regarding Gradle, Ivy, etc. we refer to the `APE mvn repository 
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
