APE Setup
=========

Configuration file
^^^^^^^^^^^^^^^^^^

The configuration file provides references to all therefor required information:

1. *Domain model* - classification of the types and operations in the domain in form 
   of an **ontology** (see `ontology example <../demo/imagemagick.html#ontology>`_ in OWL) 
   and a **tool annotation file** (see `tool annotations example <../demo/imagemagick.html#tools>`_ in JSON).
2. *Workflow specification* - including a list of **workflow inputs/outputs** and template-based 
   (see constraint templates) **workflow constraints** (see workflow constraints example)
3. *Parameters* for the synthesis execution, such as the number of desired solutions, 
   output directory, system configurations, etc.

Core configuration
~~~~~~~~~~~~~~~~~~

TODO

Run configuration
~~~~~~~~~~~~~~~~~

TODO

Domain Model
^^^^^^^^^^^^^

TODO

APE loads the domain ontology from a file in Web Ontology Language 
(OWL) format. Domain ontology consists of taxonomic classifications 
of the data and operations in the application domain, and provides 
a controlled  vocabulary  that  allows  for  different  abstraction
levels  of  its  elements.

Tool Annotations file
^^^^^^^^^^^^^^^^^^^^^

TODO

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

TODO
