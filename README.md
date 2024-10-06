Overview
This playbook automates the installation and configuration of MongoDB version 4.4.22 on a group of servers. It performs tasks such as setting up a MongoDB replica set, creating a user, and restoring a MongoDB dump file. The playbook can be used to set up a 3-node MongoDB cluster, including an arbiter.

Prerequisites
Ansible should be installed on the control machine.
MongoDB servers should be defined under the mongodb group in your Ansible inventory file.
The necessary variables should be provided in a vars.yml file.

Playbook Structure

Update apt repository and install MongoDB: The playbook updates the apt repository, installs necessary packages (e.g., gnupg), and adds the MongoDB repository.
MongoDB Configuration: Configures mongod.conf to enable replication and listen on all network interfaces (0.0.0.0).
Adds a replication set (replSetName: rs0) and adjusts other necessary configurations.
Replica Set Initiation: Initializes a MongoDB replica set using the provided replica name and list of MongoDB hosts.
Database Creation: Creates a new MongoDB database and user with specified credentials (DB, DB_USER, DB_PASSWRD).
Restore MongoDB Dump: Copies a MongoDB dump file from the control machine to the target server and restores it into the specified database.

Variables
All necessary variables are stored in vars.yml:

DB: Name of the MongoDB database.
DB_USER: MongoDB database user.
DB_PASSWRD: MongoDB database password.
REPLICA_NAME: Name of the MongoDB replica set.
