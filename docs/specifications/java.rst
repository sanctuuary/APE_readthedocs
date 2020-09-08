APE as a Java Library
=====================

Run APE from a Java environment
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Like the CLI, the APE API relies on a configuration file or object that references 
the domain ontology, tool annotations, workflow specification and execution 
parameters:

.. code-block:: java

    // set up the framework
    APE ape = new APE("path/to/setup-configuration.json");

    // run the synthesis
    SATsolutionsList solutions = ape.runSynthesis("path/to/run-configuration.json");
    // write the solutions for the file system
    APE.writeSolutionToFile(solutions);
    APE.writeDataFlowGraphs(solutions, RankDir.TOP_TO_BOTTOM);
    APE.writeExecutableWorkflows(solutions);

However, the API allows to generate and edit the configuration file programmatically:

.. code-block:: java

    // set up the framework
    APECoreConfig coreConfig = new APECoreConfig(...);
    APE ape = new APE(coreConfig);

    // run the synthesis
    APERunConfig runConfig = APERunConfig.builder()
                                 .withSolutionMinLength(1)
                                 .withSolutionMaxLength(10)
                                 .withMaxNoSolutions(100)
                                 .withApeDomainSetup(ape.getDomainSetup())
                                 .build();
                                 
    SATsolutionsList solutions1 = ape.runSynthesis(runConfig);

    // run the synthesis again with altered parameters
    runConfig.setUseWorkflowInput(ConfigEnum.ONE);
    SATsolutionsList solutions2 = ape.runSynthesis(runConfig);

For more information see `APE javadoc.io <https://javadoc.io/doc/io.github.sanctuuary/APE/latest/nl/uu/cs/ape/sat/APE.html>`_ page.

APE API functions
^^^^^^^^^^^^^^^^^

TODO

APE as a Web plug-in
^^^^^^^^^^^^^^^^^^^^^

TODO
