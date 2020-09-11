APE Setup
=========

Configuration file
^^^^^^^^^^^^^^^^^^

In order to run APE from the command line, a (JSON) configuration file needs to be provided. The file provides references to all required information, that can be classified in the following 3 groups:

1. *Domain model* - classification of the types and operations in the domain in form 
   of an **ontology** (see `ontology example <../demo/imagemagick.html#ontology>`_ in OWL format) 
   and a **tool annotation file** (see `tool annotations example <../demo/imagemagick.html#tools>`_ in JSON format).
2. *Workflow specification* - including a list of **workflow inputs/outputs** and template-based 
   (see constraint templates) **workflow constraints** (see workflow constraints example)
3. *Parameters* for the synthesis execution, such as the number of desired solutions, 
   output directory, system configurations, etc.

Although the command line tool takes the configuration file as a whole, the configuration can be divided into **core** and **run configuration** segments. This is especially visible when working with the APE API, where the two are explicitly distinguished.

The **core configuration** provides the crucial information needed to initially setup the environment, it can also be seen as *domain model configuration*, as it includes the information regarding the domain ontology and tool annotations. Once the framework is initialized, the user can run APE by providing a **run configuration**.

The **run configuration** contains all the information needed to execute the workflow synthesis and present the results to the user. This information includes the workflow specification (workflow inputs/ outputs and workflow constraints) and the execution parameters (such as path to the directory where the solutions will be generated, number of solutions needed, etc.).

These configurations are in JSON format and could be joined together, to serve as a setup- as well as a run configuration, because APE will only read the required fields. This is viible when APE is run from command line.

Examples of configurations can be found under `Use cases and Demos <../demo/imagemagick/imagemagick.html>`_.

Core configuration
~~~~~~~~~~~~~~~~~~

The core configuration is structured as follows:

+-----------------------------------+--------------------------------------------------------------------+
| Tag                               | Description                                                        |
+===================================+====================================================================+
| ``ontology_path``                 | path to the taxonomy file                                          |
+-----------------------------------+--------------------------------------------------------------------+
| ``ontologyPrexifIRI``             | absolute IRI to identify thhe elements in the taxonomy file        |
+-----------------------------------+--------------------------------------------------------------------+
| ``toolsTaxonomyRoot``             | name of the root tool class                                        |
+-----------------------------------+--------------------------------------------------------------------+
| ``dataDimensionsTaxonomyRoots``   | list of roots within the data taxonomy, each sub root represents   |
|                                   |                                                                    |
|                                   | data dimension (e.g. data format, data type, etc.)                 |
+-----------------------------------+--------------------------------------------------------------------+
| ``tool_annotations_path``         | path to the JSON file that contains basic tool annotation          |
|                                   |                                                                    |
|                                   | (provided demo example tool_annotations.json)                      |
+-----------------------------------+--------------------------------------------------------------------+

Run configuration
~~~~~~~~~~~~~~~~~

The run configuration is structured as follows:

+-----------------------------------+--------------------------------------------------+-------------------+
| Tag                               | Description                                      | Default           |
+===================================+==================================================+===================+
| ``constraints_path``              | path to the JSON file containing constraints     | No constraints    |
|                                   |                                                  |                   |
|                                   | representing workflow specification              |                   |
+-----------------------------------+--------------------------------------------------+-------------------+
| ``solution_min_length``           | minimum length from which solutions should       |                   |
|                                   |                                                  |                   |
|                                   | be searched                                      |                   |
+-----------------------------------+--------------------------------------------------+-------------------+
| ``solution_max_length``           | maximum length to which solutions should be      |                   |
|                                   |                                                  |                   |
|                                   | searched, put 0 in case of no limit              |                   |
+-----------------------------------+--------------------------------------------------+-------------------+
| ``max_solutions``                 | max number of solutions that would be returned   |                   |
+-----------------------------------+--------------------------------------------------+-------------------+
| ``solutions_path``                | path to the file where the workflow solutions    | No textual        |
|                                   |                                                  |                   |
|                                   | will be written				       | output            |
+-----------------------------------+--------------------------------------------------+-------------------+
| ``execution_scripts_folder``      | folder where the executable scripts will be      | No shell          |
|                                   |                                                  |                   |
|                                   | generated                                        | scripts           |
+-----------------------------------+--------------------------------------------------+-------------------+
| ``solution_graphs_folder``        | folder where the graphical representation        | No graphics       |
|                                   |                                                  |                   |
|                                   | of the workflows will be generated               |                   |
+-----------------------------------+--------------------------------------------------+-------------------+
| ``number_of_execution_scripts``   | number of executable scripts that will be        | 0                 |
|                                   |                                                  |                   |
|                                   | generated                                        |                   |
+-----------------------------------+--------------------------------------------------+-------------------+
| ``number_of_generated_graphs``    | number of workflow figures that will be          | 0                 |
|                                   |                                                  |                   |
|                                   | generated                                        |                   |
+-----------------------------------+--------------------------------------------------+-------------------+
| ``inputs[]``                      | each input represent a single instance that      | No inputs         |
|                                   |                                                  |                   |
|                                   | will be an input to the program                  |                   |
+-----------------------------------+--------------------------------------------------+-------------------+
| ``inputs[]/{}``                   | each of the inputs can be described using the    |                   |
|                                   |                                                  |                   |
|                                   | terms from data taxonomy, the tags used          |                   |
|                                   |                                                  |                   |
|                                   | (in our example "TypesTaxonomy" reflects         |                   |
|                                   |                                                  |                   |
|                                   | the corresponding taxonomy sub root              |                   |
+-----------------------------------+--------------------------------------------------+-------------------+
| ``outputs[]``                     | each output represent a single instance that     | No outputs        |
|                                   |                                                  |                   |
|                                   | will be an output of the program                 |                   |
+-----------------------------------+--------------------------------------------------+-------------------+
| ``outputs[]/{}``                  | each of the inputs can be described using        |                   |
|                                   |                                                  |                   |
|                                   | the terms from data taxonomy, the tags           |                   |
|                                   |                                                  |                   |
|                                   | used (in our example "TypesTaxonomy"             |                   |
|                                   |                                                  |                   |
|                                   | reflects the corresponding taxonomy sub root     |                   |
+-----------------------------------+--------------------------------------------------+-------------------+
| ``shared_memory``                 | true in a case of shared, memory structure,      | True              |
|                                   |                                                  |                   |
|                                   | false if the message passing structure should    |                   |
|                                   |                                                  |                   |
|                                   | be used                                          |                   |
+-----------------------------------+--------------------------------------------------+-------------------+
| ``debug_mode``                    | true for debug command line output               | False             |
+-----------------------------------+--------------------------------------------------+-------------------+
| ``use_workflow_input``            | ALL' if all the workflow inputs have to be       | ONE               |
|                                   |                                                  |                   |
|                                   | used,'ONE' if one of the workflow inputs         |                   |
|                                   |                                                  |                   |
|                                   | should be used or 'NONE' if none of the          |                   |
|                                   |                                                  |                   |
|                                   | workflow inputs has to be used                   |                   |
+-----------------------------------+--------------------------------------------------+-------------------+
| ``use_all_generated_data``        | ALL' if all the generated data has to be used,   | ALL               |
|                                   |                                                  |                   |
|                                   | 'ONE' if one of the data instances that are      |                   |
|                                   |                                                  |                   |
|                                   | generated as output, per tool, has to be used    |                   |
|                                   |                                                  |                   |
|                                   | or 'NONE' if none of the data instances is       |                   |
|                                   |                                                  |                   |
|                                   | obligatory to use                                |                   |
+-----------------------------------+--------------------------------------------------+-------------------+


Domain Model
^^^^^^^^^^^^^

APE loads the domain ontology from a file in Web Ontology Language 
(OWL) format. Domain ontology consists of taxonomic classifications 
of the data and operations in the application domain, and provides 
a controlled  vocabulary  that  allows  for  different  abstraction
levels  of  its  elements.

Demo file: `ImageMagick/imagemagick_taxonomy.owl <https://github.com/sanctuuary/APE_UseCases/blob/master/ImageMagick/imagemagick_taxonomy.owl>`_

Used to classify tools and data types into 2 different categories. General structure is that the main class "thing" has 2 subclasses, **Tools** and **Data** taxonomies. Furthermore, Data taxonomy consists of multiple subtaxpnpmies, where each represents a **dimension** of data, in the following example we discuss 2 different dimensions of data, namely, data *type* and data *format*.
- **thing** (root class in the OWL file)

  - **Tools Taxonomy** (URI provided as modulesTaxonomyRoot in config file)
  - **Type Taxonomy** (URI provided under **dataDimensionsTaxonomyRoots** in config file)
  - **Format Taxonomy** (URI provided under **dataDimensionsTaxonomyRoots** in config file)

**Tools Taxonomy** consists of terms that describes operations from the domain, these are called abstraction operations and they usually gropu concrete operations.
**Type Taxonomy** consists of actual data types from the domain, as well as the abstraction classes that subsume them.
**Format Taxonomy** consists of actual data Format from the domain, as well as the abstraction classes that subsume them.

Idea behind using a Format Taxonomy, is that a certain data instance require both, *data type* and *data format* to be identified. Thus, these are called dimensions of data. Having more than one data dimension is optional. Some use cases only one data dimension (see [GeoGMT](GeoGMT)), while some can have more than two.

A concrete example of a domain taxonomy can be found `here <https://github.com/sanctuuary/APE_UseCases/tree/master/ImageMagick#domain-ontology>`_.

.. note::
   Encoding supports explicit subclass relations in RDF format. The rest of the OWL file annotations will be omitted.


Tool Annotations
^^^^^^^^^^^^^^^^

Demo file: `ImageMagick/tool_annotations.json <https://github.com/sanctuuary/APE_UseCases/blob/master/ImageMagick/tool_annotations.json>`_
The file has the following structure:

.. code-block:: shell

   functions
      +function
         ID
         label
            taxonomyOperations[]
         ?inputs[]
            +input
               +dataSubTaxonomyRoot:[taxonomyTerm]
         ?outputs[]
            +output
               +dataSubTaxonomyRoot:[taxonomyTerm]
         ?implementation
            code

where (+) requires 1 or more, (?) requires 0 or 1 and no sign requires existence of exactly 1 such tag.

Regarding the semantics:

+-------------------------+----------------------------------------------------+
| ``function``            | an implementation/instance of a tool               |
+-------------------------+----------------------------------------------------+
| ``ID``                  | unique identifier of the tool                      |
+-------------------------+----------------------------------------------------+
| ``label``               | display label of the tool implementation           |
+-------------------------+----------------------------------------------------+
| ``taxonomyOperations``  | operations from the tool taxonomy (#taxonomy-file) |
|                         |                                                    |
|                         | that the current function implements               |
+-------------------------+----------------------------------------------------+
| ``input``               | a single input of the workflow                     |
+-------------------------+----------------------------------------------------+
| ``output``              | a single output of the workflow                    |
+-------------------------+----------------------------------------------------+
| ``dataSubTaxonomyRoot`` | data type that describes the input/output          |
|                         |                                                    |
|                         | (each taxonomyTerm from the [taxonomyTerm] list    |
|                         |                                                    |
|                         | has to belong to the corresponding subTaxonomy)    |
+-------------------------+----------------------------------------------------+
| ``code``                | code that will be used to implement the workflow   |
|                         |                                                    |
|                         | as a script                                        |
+-------------------------+----------------------------------------------------+

The Tool Annotations file is a collection of tools that have been semantically 
annotated, according to their inputs and outputs, based on the terms from the ontology. 
The following example annotated the tool ``compress``, which takes as 
input any ``Image`` (Type) of any Format and outputs an Image in the JPG 
format.

.. code-block:: json

   {
      "label": "compress",
      "id": "compress",
      "taxonomyOperations": ["Conversion"],
      "inputs": [
         { "Type": ["Image"] }
      ],
      "outputs": [
         { "Type": ["Image"], "Format": ["JPG"] }
      ],
      "implementation": { 
         "code": "@output[0]='@output[0].jpg'\n
                  convert $@input[0] $@output[0]\n" 
      }
   }

Referencing the Domain Model
~~~~~~~~~~~~~~~~~~~~~~~~~~~~
A reference to a class (or a set of classes) in the domain ontology 
must be in array format. This array represents a conjunction of classes 
from the ontology. For example, given the ontology below. Specifying 
``["A", "B"]`` as input for your tool makes sure only inputs of type 
``D`` and ``F`` are allowed.

.. image:: types_taxonomy_example.png

Tool Implementation
~~~~~~~~~~~~~~~~~~~
The code specified in the tool annotation could be used to constuct a 
script that executes the workflow. APE keeps track of the naming of 
the in- and output variables from tools. ``@output[0]`` references to 
the variable name of the first input type specified in the 
``inputs`` tag.

For example, take a look at the implementation of a tool called ``add``:

.. code-block:: json

   {
      "label": "add",
      "id": "add",
      "taxonomyOperations": ["Math"],
      "inputs": [
         { "Type": ["Number"] }
         { "Type": ["Number"] }
      ],
      "outputs": [
         { "Type": ["Number"]}
      ],
      "implementation": {
         "code": "@output[0] = $@input[0] + $@input[1]"
      }
   }

This could result in the following script, where ``node001`` and ``node002`` 
already have been instantiated. E.g., ``node001`` is either the user input, 
or the output of a previous tool.

.. code-block:: shell

   node003 = $node001 + $node002


Constraints File
^^^^^^^^^^^^^^^^

Demo file: `ImageMagick/Example1/constraints.json <https://github.com/sanctuuary/APE_UseCases/blob/master/ImageMagick/Example1/constraints.json>`_

The list of all the natural language templates is provided in 'SimpleDemo/constraints templates.json'. As an example we will present one of the constraint templates, namely "if then generate type" is represented as follows:

.. code-block:: json

	{
	   "constraintid": "gen_ite_t",
	   "description": "If we have generated data type ${parameter_1}, 
                           then generate type ${parameter_2} subsequently.",
	   "parameters": [
		  ["${parameter_1}"],
		  ["${parameter_2}"]
	   ]
	}

where both ``"${parameter_1}"`` and ``"${parameter_2}"`` represent a sequence of one or more data terms. The following encoding represents a use of such constraint in practice (tag ``"description"`` is not obligatory):

.. code-block:: json

   {
      "constraintid": "gen_ite_t",
      "parameters": [
         ["article","docx"],
         ["article","pdf"]
      ]
   }

The constraint is interpreted as: 
"If an **article** in **docx** format was generated, then an **article** in **pdf** format has to be generated subsequently."
