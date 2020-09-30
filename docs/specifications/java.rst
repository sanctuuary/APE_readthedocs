APE as a Java Library
=====================

Run APE from a Java environment
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Like the CLI, the APE API relies on a configuration file or object that references 
the domain ontology, tool annotations, workflow specification and execution 
parameters:

.. code-block:: java

   APECoreConfig setup = new APECoreConfig(
         new File("GeoGMT/GMT_UseCase_taxonomy.owl"),
         "http://www.co-ode.org/ontologies/ont.owl#",
         "ToolsTaxonomy",
         Arrays.asList("TypesTaxonomy"),
         new File("GeoGMT/tool_annotations.json")
   );

   APE framework = new APE(setup);


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

.. note::
    The following documentation is for APE **1.0.2**, which will be released soon.
    If you cannot wait to get started with this part, use :download:`APE-1.0.2_0e3633-executable.jar <../../files/APE-1.0.2_0e3633-executable.jar>` 
    for now, generated from `this <https://github.com/sanctuuary/APE/tree/0e36337558957595d14fc466f5d3a78c110e180d>`_ commit.


Field info
~~~~~~~~~~

Request information about the configuration fields in JSON format:

.. code-block:: java

    JSONObject tag_info = APERunConfig.getTags().toJSON();

This results in the following (partial) JSON:

.. tabs::

    .. tab:: JSON

        .. code-block:: json

            {"tags": [
                {
                    "default": true,
                    "description": "",
                    "optional": true,
                    "tag": "shared_memory",
                    "label": "Use shared memory",
                    "type": "BOOLEAN"
                },
                {
                    "description": "",
                    "optional": false,
                    "tag": "max_solutions",
                    "label": "Maximum number of solutions",
                    "type": "INTEGER",
                    "constraints": {
                        "min": 0,
                        "max": 2147483647
                    }
                },
                {
                    "default": "ONE",
                    "description": "",
                    "optional": true,
                    "tag": "use_all_generated_data",
                    "label": "Use all generated data",
                    "type": "ENUM",
                    "constraints": {"options": [
                        "NONE",
                        "ONE",
                        "ALL"
                    ]}
                }
            ]}

    .. tab:: Structure

        .. code-block:: shell

            tags[] (JSONArray)
            ├── tag (String)
            ├── label (String)
            ├── description (String)
            ├── type (String)
            ├── optional (Boolean)
            ├──? default (Type)            (depending on `optional` and `type`)
            └──? constraints (JSONObject)  (depending on `type`)
                ├──? min (int)           (depending on `type`)
                ├──? max (int)           (depending on `type`)
                └──? options (String[])  (depending on `type`)


Request information about the configuration fields using the APEConfigTag.Info struct:

.. tabs::

    .. tab:: Java

        .. code-block:: java

            for(APEConfigTag.Info<?> tag : APERunConfig.getTags().getAll()){
                if(tag.type == APEConfigTag.TagType.INTEGER){
                    System.out.printf("%s needs a value from %s to %s\n", 
                        tag.label, 
                        tag.constraints.getInt("min"), 
                        tag.constraints.getInt("max")
                    );
                }
            }

    .. tab:: output

        .. code-block:: shell

            Maximum number of solutions needs a value from 0 to 2147483647
            Number of executions scripts needs a value from 0 to 2147483647
            Number of generated graphs needs a value from 0 to 2147483647

Evaluating an input value 
~~~~~~~~~~~~~~~~~~~~~~~~~

.. code-block:: java

    APE ape = new APE( ... );

    APERunConfig run_config = APERunConfig.builder()
        .withSolutionLength(1, 6)
        .withWorklowInput(ConfigEnum.ALL)
        .build();
            
    for(ValidationResult result : ape.validate(config).getFails()){
        System.out.printf("Tag %s in incorrect: %s", result.getTag(), result.getRuleDescription());
    }
