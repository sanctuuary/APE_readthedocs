Mass spectronomy-based proteomics
=================================

This is a project used to demonstrate the sysnthesis functionality 
provided by APE.

The use case aims to demonstrate the usefulness of the synthesis 
approach for solving a workflow discovery problem in bioinformatics. 
The scenario was demonstrated in [[1]_].
	
**No1** use case describes the 1st Use Case described in the paper, 
labeled as **No. 1**.

.. note:: 
    In order to be able to execute the generated 
    workflows on the machine, the tools have to be annotated 
    accordingly, and the corresponding software should be 
    available.

In order to use the APE library from the command line, simply run the ``APE-<version>-executable.jar`` file using command:

.. code-block:: shell

    java -jar APE-<version>-executable.jar [path_to_ape_configuration_file]

No 1
^^^^

As an example, if you would download the 
`APE-1.0.1-executable.jar <https://repo.maven.apache.org/maven2/io/github/sanctuuary/APE/1.0.1/APE-1.0.1-executable.jar>`_ 
to the root of APE_UseCases repository on your local machine, 
you could run this demo by executing the following command:

.. code-block:: shell

    cd ~/git/APE_UseCases
    java -jar APE-1.0.1-executable.jar MassSpectometry/No1/ape.configuration

The results of the synthesis would be:

.. code-block:: shell

    MassSpectometry/No1/sat_solutions.txt - First 100 candidate solutions in textual format
    MassSpectometry/No1/Figures/          - Data-flow figures corresponding to the first 10 solutions
    MassSpectometry/No1/Implementations/  - Executable shell scripts corresponding to the first 6 solutions

.. [1] Magnus Palmblad, Anna-Lena Lamprecht, Jon Ison, Veit Schwämmle, 
       Automated workflow composition in mass spectrometry-based proteomics, 
       Bioinformatics, Volume 35, Issue 4, 15 February 2019, Pages 656–664, 
       https://doi.org/10.1093/bioinformatics/bty646
