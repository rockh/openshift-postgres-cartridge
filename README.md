Openshift Postgres 9.5.3 Cartridge for OpenShift V2
=============================

The Crunchy PG Cartridge is named openshift-postgres-cartridge, which will allow you to install a single standalone PostgreSQL server or a more complex configuration of a “master” and “standby” replication configuration. 

This cartridge runs on Openshift v2, both Origin and Enterprise.

NOTE
----
This cartridge does NOT run in an Auto-Scale app configuration.  You
can however get the same result if you run this cartridge (with any 
web framework) standalone, and then configure your other Openshift
apps to port-forward to this PG instance.

Installing
---------------

To install this in Origin V2, enter the following into the downloadable
cartridge "install your own cartridge" field:

http://cartreflect-claytondev.rhcloud.com/github/rockh/openshift-postgres-cartridge

This will use the reflector to add a customised PostgreSQL cartridge to your
web application.

Patch
---------------

This version of PostgreSQL includes a fix applied to the pgstat.c source file that allows PostgreSQL to bind to an alternative host address rather than the default of localhost. This fix is required for running PostgreSQL on the current OpenShift platform due to the localhost (127.0.0.1) not being available for application use. The STATHOST environment variable is defined by this version of PostgreSQL for this purpose. 


Testing
-------------
Various environment variables are set that allow you to connect
to the database as follows:

psql -U $OPENSHIFT_POSTGRESQL_DB_USERNAME -h $OPENSHIFT_POSTGRESQL_DB_HOST $OPENSHIFT_POSTGRESQL_DB_NAME

The PostgreSQL port is 5432.  The database user is $USER which has superuser privs.

The PostgreSQL data directory is found at ~/app-root/data/.pg

