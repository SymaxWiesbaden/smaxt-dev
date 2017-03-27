# Installation Requirements

smaxt can be installed on ORACLE™-databases of version 11gR2[^1]\[2\] and newer. It is independent on the ORACLE™ Editions, so it works on Standard-Server, Enterprise-Server as well as on the XE-Edition. There are no special requirements for the present database instance to run smaxt.

Only for the usage of the smaxt features for the job-driven production of documents, as well as their transport via FTP or SMTP, the ORACLE Scheduler  \(DBA\\_SCHEDULER\) and the network-access-control list \(DBMS\\_NETWORK\\_ACL\\_ADMIN\)\[^3\] must be activated.

The installation of smaxt is done with the help of a script using SQLPLUS and SQLLDR. Therefore, it can be performed from any client machine as well as directly on the Database-Server itself.

But keep in mind that if you like to perform the installation from a client, the \*Oracle instant client is not enough\*, because the SQLLDR is not included in this version. If you still try to execute the installation from such a system, you'll receive error message during the handling of the SEP files \(which contain smaxt internal reports as well as the sample projects\). The smaxt core will still work in that case, but you have to install the SEP-Files manually with the smaxt Management Studio \(see 5.3.2 Importieren\)

smaxt does not require an explicit dimensioned tablespace, because the system is very slim and except of temporarily storage of the generated documents as well as some log-messages, very few data will be stored permanently.

That’s why by default, the install script grants an UNLIMITED TABLESPACE to the smaxt user, but if you like so, you may restrict this tot he desired value. The size of tablespace then depends on the amount and size of documents, you´d expect to be generated and stored until the periodical clean-job is running.

---

\[^2\]: 

\[^3\]: For the ACL, an explicit activation of the XML database may be necessary. Refer to the appropriate documentation of ORACLE DB.

In theory, an installation on a 10 database is possibl, although this option is not fully tested and approved. If you need to make a such installation, you should get in contact SYMAX support prior of your installation trials.

