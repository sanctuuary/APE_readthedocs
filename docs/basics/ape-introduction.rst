Introduction to APE
===================

About APE
^^^^^^^^^

.. image:: ../../img/logo.png
    :width: 200px
    :alt: APE logo
    :align: left

APE (Automated Pipeline Explorer) is a command line tool and Java API for the automated exploration of possible computational
pipelines (scientific workflows) from large collections of computational tools.

APE relies on a semantic domain model that includes tool and type taxonomies as controlled
vocabularies for the description of computational tools, and functional tool annotations
(inputs, outputs, operations performed) using terms from these taxonomies. Based on this
domain model and a specification of the available workflow inputs, the intended workflow
outputs and possibly additional constraints, APE then computes possible workflows.

Internally, APE uses a component-based program synthesis approach. It translates the domain
knowledge and workflow specification into logical formulas that are then fed to a SAT solver
to compute satisfying instances. These solutions are then translated into the actual
candidate workflows. For detailed description we refer to [1]_.

For our paper at ICCS 2020 [2]_ we created a video that explains APE in 5 minutes:

.. raw:: html

         <iframe width="720" height="405" src="https://www.youtube.com/embed/CzecqRJXmoM" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

|

.. note::
       Our `use cases <../demo/imagemagick.html>`_ are motivated by practical
       problems in various domains (e.g. bioinformatics, GIS [3]_).
       For one of the bioinformatics use cases, our intern Karl Allgaeuer developed
       a prototype of a web-based interface to APE. It is available at
       `ape.science.uu.nl <http://ape.science.uu.nl/>`_ (alpha).
       A Docker version of this demonstrator is available at
       `github.com/sanctuuary/Burke_Docker <https://github.com/sanctuuary/Burke_Docker>`_

Credits
^^^^^^^
APE has been inspired by the `Loose Programming framework PROPHETS <http://ls5-www.cs.tu-dortmund.de/projects/prophets/index.php>`_.
It uses similar mechanisms for semantic domain modeling, workflow specification and synthesis, but strives to provide the automated
exploration and composition functionality independent from a concrete workflow system.

We thank our brave first-generation users for their patience and constructive feedback that helped us to get APE into shape.

License
^^^^^^^
APE is licensed under the `Apache 2.0 <https://github.com/sanctuuary/APE/blob/master/LICENSE>`_ license.

Maven dependencies
^^^^^^^^^^^^^^^^^^
1. `OWL API <https://mvnrepository.com/artifact/net.sourceforge.owlapi/owlapi-distribution>`_ - LGPL or Apache 2.0
2. `SAT4J <https://mvnrepository.com/artifact/org.sat4j/org.sat4j.core>`_ - EPL or GNU LGPL
3. `apache-common-lang <https://mvnrepository.com/artifact/org.apache.commons/commons-lang3>`_ - Apache 2.0
4. `Apache Log4j Core <https://mvnrepository.com/artifact/org.apache.logging.log4j/log4j-core>`_ - Apache 2.0
5. `graphviz-java <https://mvnrepository.com/artifact/guru.nidi/graphviz-java>`_ - Apache 2.0
6. `org.json <https://mvnrepository.com/artifact/org.json/json>`_ - `JSON license <https://www.json.org/license.html>`_
7. `JUnit Jupiter API <https://mvnrepository.com/artifact/org.junit.jupiter/junit-jupiter-api>`_ - EPL 2.0
8. `SLF4J Simple Binding <https://mvnrepository.com/artifact/org.slf4j/slf4j-simple>`_ - MIT
9. `ANTLR 4 Runtime <https://mvnrepository.com/artifact/org.antlr/antlr4-runtime>`_ - BSD
10. `SnakeYAML <https://mvnrepository.com/artifact/org.yaml/snakeyaml>`_ - Apache 2.0

Contributors
^^^^^^^^^^^^
* Vedran Kasalica (v.kasalica[at]esciencecenter.nl), lead developer
* Maurin Voshol, student developer
* Koen Haverkort, student developer
* Anna-Lena Lamprecht (anna-lena.lamprecht[at]uni-potsdam.de), project initiator and principal investigator

References
^^^^^^^^^^
.. [1] Kasalica, V., & Lamprecht, A.-L. (2020).
       Workflow Discovery with Semantic Constraints:
       The SAT-Based Implementation of APE. Electronic Communications of the EASST, 78(0).
       https://doi.org/10.14279/tuj.eceasst.78.1092

.. [2] Kasalica V., Lamprecht AL. (2020)
       APE: A Command-Line Tool and API for Automated Workflow Composition.
       ICCS 2020. ICCS 2020. Lecture Notes in Computer Science, vol 12143. Springer,
       https://doi.org/10.1007/978-3-030-50436-6_34

.. [3] Kasalica, V., & Lamprecht, A.-L. (2019).
       Workflow discovery through semantic constraints: A geovisualization case study.
       In Computational science and its applications – ICCSA 2019
       (pp. 473–488), Springer International Publishing,
       https://doi.org/10.1007/978-3-030-24302-9_53
