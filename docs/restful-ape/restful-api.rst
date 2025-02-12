RESTful API Methods
===================

This section offers a brief overview of the RESTful APE API, designed to facilitate automated pipeline exploration through HTTP requests. For comprehensive and up-to-date information, please refer to our OpenAPI documentation.

.. note::
   The OpenAPI specification is the definitive source of details for all endpoints.

Index
-----

**Endpoint:** GET /

Provides a welcome message.

**Success Response:**
- **Code:** 200
- **Content:** "Welcome to the RESTful APE API!"

Data Taxonomy
-------------
**Endpoint:** GET /data_taxonomy

Retrieves data taxonomy based on the provided domain configuration file.
The data taxonomy is retrieved from the OWL file specified in the configuration (e.g., EDAM ontology). Additionally, data terms not supported by the domain are removed from the taxonomy (for example data types and formats not supported by the annotated tools and operations), ensuring that only relevant data terms are included.

- **Parameters:**
  - *config_path* (string): URL to the APE configuration file.

**Success Response:**
- **Code:** 200
- **Content:** application/json with taxonomy of data terms.

Tools Taxonomy
--------------
**Endpoint:** GET /tools_taxonomy

Retrieves tools taxonomy based on the provided domain configuration file.
The tools taxonomy is retrieved from the OWL file specified in the configuration (e.g., EDAM ontology) and extended with the tools supported by the domain. Additionally, operations not supported by the annotated tools are removed from the taxonomy, ensuring that only relevant operations are included.

- **Parameters:**
  - *config_path* (string): URL to the APE configuration file.

**Success Response:**
- **Code:** 200
- **Content:** application/json with taxonomy of tool terms.

Constraint Templates
--------------------
**Endpoint:** GET /constraint_templates

Retrieve constraint templates based on the provided domain configuration file. These templates specify constraints supported by APE that can be used to guide the synthesis process.

- **Parameters:**
  - *config_path* (string): URL to the APE configuration file.

**Success Response:**
- **Code:** 200
- **Content:** application/json with constraint templates.

Domain Constraints
------------------
**Endpoint:** GET /domain_constraints

Retrieve a fixed set of domain constraints specified in the domain configuration file.

- **Parameters:**
  - *config_path* (string): URL to the APE configuration file.

**Success Response:**
- **Code:** 200
- **Content:** application/json with domain-specific constraints.

Domain I/O
----------
**Endpoint:** GET /domain_io

Retrieve default domain input and output data terms based on the provided domain configuration file.

- **Parameters:**
  - *config_path* (string): URL to the APE configuration file.

**Success Response:**
- **Code:** 200
- **Content:** application/json with a taxonomy of data terms.

Run Workflow Synthesis
----------------------
**Endpoint:** POST /run_synthesis

Synthesize workflow based on the provided run configuration file.

- **Request Body:** JSON object containing the synthesis configuration.

**Success Response:**
- **Code:** 200
- **Content:** application/json with a list of resulting solutions.

Run Synthesis and Benchmarks
----------------------------
**Endpoint:** POST /run_synthesis_and_bench

Synthesize workflow and provide design-time benchmarks based on the provided configuration.

- **Request Body:** JSON object containing the synthesis configuration.

**Success Response:**
- **Code:** 200
- **Content:** application/json with resulting solutions and benchmarks.

Retrieve Workflow Image
-----------------------
**Endpoint:** POST /image

Retrieve an image representing the workflow.

- **Request Body:** JSON object containing image information.

**Success Response:**
- **Code:** 200
- **Content:** image/png with the workflow image.

Retrieve CWL File
-----------------
**Endpoint:** POST /cwl

Retrieve a CWL file describing the workflow.

- **Request Body:** JSON object containing CWL file retrieval details.

**Success Response:**
- **Code:** 200
- **Content:** application/x-yaml with the CWL file.

Retrieve CWL Input File
-----------------------
**Endpoint:** GET /cwl_input

Retrieve a CWL input file (.yml) representing the workflow inputs.

- **Parameters:**
  - *run_id* (string): ID of the corresponding synthesis run.

**Success Response:**
- **Code:** 200
- **Content:** application/x-yaml with the CWL input file.

Retrieve Design-Time Benchmarks
-------------------------------
**Endpoint:** GET /design_time_benchmarks

Retrieve a design-time benchmark file describing the workflow.

- **Parameters:**
  - *file_name* (string): Name of the benchmark file.
  - *run_id* (string): ID of the corresponding synthesis run.

**Success Response:**
- **Code:** 200
- **Content:** application/json with the benchmark file.

Retrieve CWL Files as ZIP
-------------------------
**Endpoint:** POST /cwl_zip

Retrieve a ZIP file comprising specified CWL files.

- **Request Body:** JSON object containing the *run_id* and a list of CWL file names.

**Success Response:**
- **Code:** 200
- **Content:** application/zip with the specified CWL files.
