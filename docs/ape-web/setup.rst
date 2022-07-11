Setup
=====

Requirements
^^^^^^^^^^^^
To set up APE Web, you need to have either:

* `Docker <https://www.docker.com/get-started/>`_ with Docker compose.
* `Node.js 14 <https://nodejs.org/en/>`_ (or higher),
  `Java 11 <https://www.oracle.com/java/technologies/downloads/#java11>`_ (or higher),
  `Maven 3.3+ <https://maven.apache.org/download.cgi>`_,
  and a `MongoDB database <https://www.mongodb.com/try/download>`_.

We recommend using Docker to set up APE Web.

Configuration
^^^^^^^^^^^^^

First, copy the ``.env`` file in the front-end directory to a new file named ``.env.production.local``.
In this file, change any of the URL configurations as necessary.
If APE Web runs behind an Apache or Nginx proxy, these can most likely be kept as localhost.

.. attention:: Do make sure to change the ``APPLICATION_SECRET`` to ensure secure session storage.

If you wish to change the port of the front-end, or the database username and password, you need to edit the Docker compose environment file:
go to the root directory of the project and copy the ``.env`` file to a new file named ``.env.local``.
Change the values as needed.

.. note:: Make sure the ``FE_PORT`` in the environment file in the root directory matches the port of ``NEXT_PUBLIC_FE_URL`` in the environment file from the front-end.

Docker setup
^^^^^^^^^^^^

Running the container
~~~~~~~~~~~~~~~~~~~~~

After configuring APE Web, you can start APE Web by running:

.. code-block:: shell

  docker-compose up -d

Creating the first administrator account (Docker)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

After setting up APE Web and running it for the first time, you should create an initial administrator account.
To do this, follow these steps:

1. Register a user on the website.
2. Use the ``register-admin.sh`` script that is found in the ``scripts`` directory. This script requires the following parameters:

  * The MongoDB database container name.
  * The MongoDB database root username and password.
  * The e-mail address of the user which should be made an administrator.

After the script is done, the user with the given e-mail address will be an administrator on the website.

Manual setup
^^^^^^^^^^^^

Back-end
~~~~~~~~

First, the back-end needs to be built. To build the back-end, navigate to the back-end directory and run:

.. code-block:: shell

  mvn package -DskipTests=true

The built ``back-end-<version>.jar`` file can now be found in the "target" directory.

Before running the back-end, make sure the MongoDB database is running. The back-end will not start if it cannot make a connection to the database.
If the database is online, start the back-end using:

.. code-block:: shell

  java -jar back-end-<version>.jar

Front-end
~~~~~~~~~

To create an optimized production build, run the command following command in the front-end directory:

.. code-block:: shell

  npm run build

To start the production build, now run:

.. code-block:: shell

  npm run start

Creating the first administrator account (manually)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

After setting up APE Web and running it for the first time, you should create an initial administrator account.
To do so, first create an account on the website, then connect to your MongoDB database and run the following commands, where the e-mail address is replaced with the e-mail address of the account that should be made an administrator.

.. code-block:: javascript

  use ape

  var newAdmin = db.user.findOne(
  { "email": { $eq: "email@email.mail" } }
  );

  db.user.updateOne(
    newAdmin,
    { $set: { status: "Approved" } }
  );

  db.userApproveRequest.updateOne(
    { userId: newAdmin._id },
    { $set: { status: "Approved" } }
  );

  db.userAdmin.insertOne(
    { userId: newAdmin._id, adminStatus: "Active" }
  );

This will find the user account with the given e-mail address, and apply the following changes to it:

* Approve the account on the website so it is activated.
* Update the approve request as the account has now been approved.
* Give the account an admin status on the website.
