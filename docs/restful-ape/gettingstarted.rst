Getting Started with RESTful APE
================================

This guide will help you get started with the RESTful API for the APE library, covering the initial setup, how to make your first API request, and a brief overview of the API's core functionalities.

Setting Up Your Environment
---------------------------

Before you begin, ensure you have the following prerequisites installed:

- Java JDK 11 or higher
- Maven (for building the project)
- An HTTP client (like Postman, or `curl` command-line tool)

**Running the Spring Boot Application**

1. Clone the RESTful APE repository:

.. code-block:: shell

   git clone https://github.com/sanctuuary/RESTAPE.git
   cd RESTAPE

2. To run the Spring Boot application directly:

.. code-block:: shell

   mvn spring-boot:run

Alternatively, you can build the jar package first:

.. code-block:: shell

   mvn clean package
   java -jar target/restape-[version].jar

Making Your First Request
-------------------------

With the RESTful API server active, you're ready to initiate your first request to explore computational pipelines. Below is a `curl` command example to get you started:

.. code-block:: shell

   curl -X POST [host]:[port]/api/explore -H "Content-Type: application/json" -d '{your_request_data}'

Ensure you replace `[host]`, `[port]`, and `{your_request_data}` with the correct values corresponding to your environment.

Exploring the OpenAPI Documentation
-----------------------------------

The RESTful APE API's OpenAPI documentation is your go-to resource for detailed information on endpoints, parameters, and response formats. It's interactive, allowing you to directly test API calls within the documentation itself.

Access the OpenAPI documentation at:

.. code-block:: none

   http://localhost:[port]/swagger-ui/index.html

Make sure to adjust `[port]` to match the port number where your RESTful API server is hosted.

For an introductory overview of the API, visit the preliminary `documentation <restful-api.html>`_

.. code-block:: none

   ./restful-api.html

This preliminary guide provides a quick glance at the API's capabilities. However, for a complete and interactive exploration, the OpenAPI documentation is recommended.

Next Steps
----------

- **Dive Deeper:** Utilize the OpenAPI documentation for a comprehensive understanding of the RESTful APE API.
- **Integration:** Incorporate the RESTful API into your applications to automate pipeline exploration seamlessly.
- **Engage:** Consider contributing to the RESTful APE project or reporting any issues you encounter on GitHub.

Congratulations on embarking on your journey to explore computational pipelines with RESTful APE. The combination of this preliminary overview and the OpenAPI documentation equips you with the knowledge to start integrating and leveraging the full potential of the RESTful APE API.
