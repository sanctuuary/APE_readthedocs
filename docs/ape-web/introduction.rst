Introduction to APE Web
=======================

`APE Web <https://github.com/sanctuuary/APE-Web>`_ is a web interface build around APE to provide a user-friendly interface for using APE.
It allows users to set up and share domains, and run APE to explore workflows online.
The inputs, outputs and constraints for workflows can easily be configured via the interface.
Additional tools are also included, such as a visual constraint sketcher and workflow comparer.

APE Web is available under the Apache 2.0 license.

.. note:: This project is not actively maintained. An alternative is the `Workflomics platform <https://workflomics.org/>`_ which uses APE to generate candidate workflows and takes it a step further by providing a platform for benchmarking the generated workflows.

Dependencies
^^^^^^^^^^^^

Front-end
~~~~~~~~~
The front-end is built in TypeScript using Node.js, with the most important dependencies being:

* `React <https://www.npmjs.com/package/react>`_ - MIT
* `Next.js <https://www.npmjs.com/package/next>`_ - MIT
* `Ant Design <https://www.npmjs.com/package/antd>`_ - MIT
* `TypeScript <https://www.npmjs.com/package/typescript>`_ - Apache 2.0

Back-end
~~~~~~~~
The back-end is built in Kotlin, with the most important dependencies being:

* `Spring Boot <https://mvnrepository.com/artifact/org.springframework.boot/spring-boot-starter-web>`_ - Apache 2.0
* `Spring Data MongoDB <https://mvnrepository.com/artifact/org.springframework.data/spring-data-mongodb>`_ - Apache 2.0
* `Kotlin Stdlib Jdk8 <https://mvnrepository.com/artifact/org.jetbrains.kotlin/kotlin-stdlib-jdk8>`_ - Apache 2.0

Contributors
^^^^^^^^^^^^
| This project was initially developed by students from the bachelor Computer Science at Utrecht University within the Software Project course, and students from Grafisch Lyceum Utrecht:
| Silvan Eelman, Koen Haverkort, Alex Janse, Matthijs Rademaker, Megan Tjoeng, Inge van Dam, Jeroen van der Wal, Sem van Nieuwenhuizen, Rense Wolters, Sarrisa Wouts.

The project was later further developed by the following contributors:

* Vedran Kasalica (v.kasalica[at]esciencecenter.nl), lead developer
* Koen Haverkort, student developer
* Anna-Lena Lamprecht (anna-lena.lamprecht[at]uni-potsdam.de), project initiator and principal investigator
