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
`APE-2.5.2-executable.jar <https://repo.maven.apache.org/maven2/io/github/sanctuuary/APE/2.5.2/APE-2.5.2-executable.jar>`_ 
to the root of APE_UseCases repository on your local machine, 
you could run this demo by executing the following command:

.. code-block:: shell

    cd ~/git/APE_UseCases
    java -jar APE-2.5.2-executable.jar MassSpectometry/No1/config.json

The results of the synthesis would be stored under the directory 
specified in the configuration file (``solutions_dir_path`` parameter). The results of the synthesis would be:

.. code-block:: shell

    solutions_dir_path/solutions.txt - First X candidate solutions in textual format, where X is the number of solutions specified in the config file (``solutions`` parameter)
    solutions_dir_path/Figures/        - Workflow figures corresponding to the first Y solutions, where Y is the number of solutions specified in the config file (``number_of_generated_graphs`` parameter, 0 if not specified))
    solutions_dir_path/Executables/  - Executable shell scripts corresponding to the first Z solution, where Z is the number of solutions specified in the config file (``number_of_execution_scripts`` parameter, 0 if not specified))
    solutions_dir_path/CWL/ - CWL files corresponding to the first Q solution, where Q is the number of solutions specified in the config file (``number_of_cwl_files`` parameter, 0 if not specified)

.. [1] Magnus Palmblad, Anna-Lena Lamprecht, Jon Ison, Veit Schwämmle, 
       Automated workflow composition in mass spectrometry-based proteomics, 
       Bioinformatics, Volume 35, Issue 4, 15 February 2019, Pages 656–664, 
       https://doi.org/10.1093/bioinformatics/bty646
