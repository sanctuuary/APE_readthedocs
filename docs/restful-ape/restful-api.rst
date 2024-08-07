RESTful API Methods
===================

This section offers a brief overview of the RESTful APE API, designed to facilitate automated pipeline exploration through HTTP requests. It serves as an initial sketch to familiarize users with the API's core functionalities and endpoints.

For comprehensive and up-to-date documentation, including all available endpoints, request parameters, and response schemas, please refer to our OpenAPI documentation. The OpenAPI specification provides a complete and interactive description of the API's capabilities, ensuring developers have access to the most accurate and detailed information for integrating with the RESTful APE service.

**Note:** The OpenAPI documentation represents the definitive source of information for working with the RESTful APE API, offering a level of detail and interactivity beyond what is provided in this preliminary sketch.

Index
-----

**Endpoint:** ``GET /``

The index endpoint of the RESTful APE API provides a welcome message.

**Success Response:**

- **Code:** 200
- **Content:** "Welcome to the RESTful APE API!"

Data Taxonomy
-------------

**Endpoint:** ``GET /data_taxonomy``

Retrieves data taxonomy based on the provided domain configuration file.

- **Parameters:** 

  - ``config_path`` (string): URL to the APE configuration file.

- **Success Response:**

  - **Code:** 200 
  - **Content:** application/json with taxonomy of data terms.

Tools Taxonomy
--------------

**Endpoint:** ``GET /tools_taxonomy``

Retrieves tools taxonomy based on the provided domain configuration file.

- **Parameters:** 

  - ``config_path`` (string): URL to the APE configuration file.

- **Success Response:**

  - **Code:** 200 
  - **Content:** application/json with taxonomy of tool terms.

Constraints
-----------

**Endpoint:** ``GET /constraints``

Retrieve constraint templates based on the provided domain configuration file.

- **Parameters:** 

  - ``config_path`` (string): URL to the APE configuration file.

- **Success Response:**

  - **Code:** 200 
  - **Content:** application/json with constraint templates.

Run Workflow Synthesis
----------------------

**Endpoint:** ``POST /run_synthesis``

Synthesize workflow based on the provided run configuration file.

- **Request Body:** JSON object containing the configuration for the synthesis.

- **Success Response:**

  - **Code:** 200 
  - **Content:** application/json with a list of resulting solutions.

Run Synthesis and Benchmarks
----------------------------

**Endpoint:** ``POST /run_synthesis_and_bench``

Synthesize workflow and provide design-time benchmarks based on the provided configuration.

- **Request Body:** JSON object containing the configuration for the synthesis.

- **Success Response:**

  - **Code:** 200 
  - **Content:** application/json with a list of resulting solutions and benchmarks.

Retrieve Workflow Image
-----------------------

**Endpoint:** ``POST /image``

Retrieve an image representing the workflow.

- **Request Body:** JSON object containing the information about the image.

- **Success Response:**

  - **Code:** 200 
  - **Content:** image/png with the workflow image.

Retrieve CWL File
-----------------

**Endpoint:** ``POST /cwl``

Retrieve a CWL file describing the workflow.

- **Request Body:** JSON object containing information for retrieving the CWL file.

- **Success Response:**

  - **Code:** 200 
  - **Content:** application/x-yaml with the CWL file.

Retrieve CWL Input File
-----------------------

**Endpoint:** ``GET /cwl_input``

Retrieve a CWL input file (.yml) representing the workflow inputs.

- **Parameters:** 

  - ``run_id`` (string): ID of the corresponding synthesis run.

- **Success Response:**

  - **Code:** 200 
  - **Content:** application/x-yaml with the CWL input file.

Retrieve Design-Time Benchmarks
-------------------------------

**Endpoint:** ``GET /design_time_benchmarks``

Retrieve a design-time benchmark file describing the workflow.

- **Parameters:** 

  - ``file_name`` (string): Name of the benchmark file.
  - ``run_id`` (string): ID of the corresponding synthesis run.

- **Success Response:**

  - **Code:** 200 
  - **Content:** application/json with the benchmark file.

Retrieve CWL Files as ZIP
-------------------------

**Endpoint:** ``POST /cwl_zip``

Retrieve a ZIP file comprising specified CWL files.

- **Request Body:** JSON object containing the `run_id` and a list of CWL file names.

- **Success Response:**

  - **Code:** 200 
  - **Content:** application/zip with the specified CWL files.

