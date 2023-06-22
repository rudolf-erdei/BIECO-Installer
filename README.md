# BIECO Platform Installer
Welcome to the ***BIECO Platform Installer Repository***. This *Docker Compose YAML* file will help you install the entire BIECO Platform.

**Please remember that the platform and installer is still in Alpha Version, so problems will occur and it is not ready for production.**

[Official Website for the BIECO Research Project](https://bieco.org)

## Installing the Platform

You can install the platform using Docker Compose, with the shell command: **docker compose up**

## Default user for the Platform

The platform will be installed with all the needed information, including the schema and content of the database. The username and password are:

U: **admin@admin.com**

P: **administrator**

## Interaction between platform components

The Docker Application will provide a volume that will enable all Tools to use the same directories for storage.
In this regard, the /platform subdirectory of the bieco-data volume will contain sepparate directories
for all of the jobs in the sistem (based on the job ID). If any tool requires common files, these can be saved
or loaded from this directory.

Accessing a dockerized Tool is possible using the image name and the internal port. For example, the
URL for the BIECO Orchestrator will be: **http://bieco-orchestrator:4000/orchestrator/biecointerface** where
**bieco-orchestrator** is the image name and **4000** is the internal port. The mapped port is needed only for outside
access (outside the **bieco-net** network).

Tool Developers are advised to put URL's and ports as parameters that can be set by docker compose, so that the
platform will be flexible enough.

## Database usage
An instance of MySQL (currently version 5.7.33) comes preinstalled within the system.
If needed, it can be used, but please create a different database.

## Integration and ActiveMQ Usage
An instance of ActiveMQ comes preinstalled, as a requirement for some tools. If needed, please use the same instance.

## Troubleshooting
Sometimes, on Linux-based OS's, the platform won't start as the rights of some files are set wrong when pulling
or downloading. To solve this issue, please check that all files have the correct read/execution rights. Please
pay special attention to the **mysql-schema** folder and the files within it.