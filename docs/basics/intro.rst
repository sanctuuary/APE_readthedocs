Getting started with APE
========================

Introduction to APE
^^^^^^^^^^^^^^^^^^^

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
candidate workflows. For detailed description we refer to [[1]](#1).

For our paper at `ICCS 2020 <https://www.iccs-meeting.org/iccs2020/>`_) [2] we created a video that explains APE in 5 minutes:

[YOUTUBE VIDEO]

.. .. embed:: https://www.youtube.com/watch?v=CzecqRJXmoM
     :max_width: 720
     :max_height: 480

My first APE run
^^^^^^^^^^^^^^^^

TODO
