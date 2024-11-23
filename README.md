This Ansible playbook installs MongoDB 7.0 on a set of Ubuntu servers and configures them as part of a replica set. It also configures MongoDB's settings, creates a new database, and sets up a user for that database. This playbook can be used to deploy and configure MongoDB in a production-like environment.

Prerequisites

You have an Ansible control machine set up.
MongoDB servers are listed under the mongodb group in your Ansible inventory.
SSH access is available to all MongoDB servers with sudo privileges.

Playbook Structure

Purge the existing Mongod service: Before executing the main task, the playbook purges the Mongod service on all hosts if the service is already available
Install the required service: PyMongo needs to be installed to execute some tasks.
Update apt repository and install MongoDB: The playbook updates the apt repository, installs necessary packages (e.g., gnupg), and adds the MongoDB repository.
MongoDB Configuration: Configures mongod.conf to enable replication and listen on all network interfaces (0.0.0.0).
Replica Set Initiation: Initializes a MongoDB replica set using the provided replica name and list of MongoDB hosts.
Database Creation: Creates a new MongoDB database and user with specified credentials (DB, DB_USER, DB_PASSWRD).

Variables

All necessary variables are stored in vars.yml:

DB: Name of the MongoDB database.
DB_USER: MongoDB database user.
DB_PASSWRD: MongoDB database password.
REPLICA_NAME: Name of the MongoDB replica set.
