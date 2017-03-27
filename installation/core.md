# Installing the smaxt Database Extension

The smaxt Database Extension is the core of smaxt. It is responsible for the evaluations, the parameter handling and rendering resulting Office documents and that also contains the mechanisms for rights compliance and monitoring, job scheduling and eployment in directories and shipment by E-Mail, is a pure PL/SQL application that is installed through a SQL script into an existing database.

In theory, this is the only component that really needs to be installed. Basically it´s possible to configure and run smaxt completely via SQL scripts, although this is very troublesome.

Indeed, only the installation of the smaxt core would be needed on the  production system in an environment that consists of a development database, a test and/or integration database, as well as a production system. The configuration and the layout could be anticipated on the development environment and finally imported into the production.



