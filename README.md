# Welcome to smaxt

Smaxt is a fully  integrated production system for Microsoft Office™ Documents[\[1\]](#_ftn1). smaxt is completely installed and running inside a schema of an ORACLE™ database. No additional tools are required.

It is estimated that, based on numerous reporting and BI projects, between 40% and 60% \(in some cases even up to 100%\) of the reports generated by those reporting and BI-Tools, are simply used to convert data into Microsoft Excel™ workbooks, in Microsoft PowerPoint™ presentations, and also in Microsoft Word™ documents.

This is usually done by performing the relevant reports and then manually using the export function to transfer the results in a .xlsx file. Sometimes, the only way to achieve this is using the clipboard via copy and paste.

smaxt, however, is a directly in the ORACLE™ database integrated solution, that produces the desired Office™ documents perfect, immediately and without any intermediate steps.

This leads to a number of advantages:

* Since smaxt is located in the ORACLE database, there´s no need to transfer the data to another system \(ad hoc or nightly ETL jobs\), as it is usually necessary for other reporting and business intelligence tools. This means network resources are conserved and evaluations can take place with utmost efficiency, timeliness and speed.
* smaxt works within the ORACLE Server, which means, that no deployment, configuration and maintenance of additional systems \(software and hardware\) is required, so smaxt saves you administrative costs.
* smaxt relies on SQL as query language and Word and Excel or PowerPoint as layouting-tools, so that typically those people, how should use smaxt, already have all the required Know-how and no not have to learn handle new tools.
* The "point-of-failures" are reduced to 1, because if the ORACLE DB is up, then also smaxt is running. More questions such as "is the Reportingserver down?" or "is the network connection established or is it currently very slow?"are thus eliminated.

However, if you have a problem in your environment with some of the above points, since these may violate applicable policies in your organization, then you are of course free to set up another Oracle instance \(e.g. the free Oracle XE - database\) as a host for the smaxt system and provide the data for the reporting and document generation in conventional way, like database links , ETL or similar tranfser-mechanisms.

Above these mentioned features, smaxt provides some functionalities and capabilities, which make the system very efficient and:

* Simple output of data, where not only the number of rows is not predictable \(what for tables and views is perfectly normal\), but also the number of columns and their titles may vary per evaluation \(e.g., "all customers that have revenues in the period of X" or "all funds, which are currently registered for sale in country Y"\), i.e. a kind of smaxt internal pivoting takes place here.
* Output of data, where with a simple click, rows are transposed to columns and vice versa.
* Configurable, multiple reusable data modules, which can be grouped together in any variation for evaluation and therefore allow very flexible and multifaceted evaluations.
* The resulting Excel workbooks are cell-precisely and 'alive', i.e. the data output will be exact there, where it´s expected. References, formulas, and charts are still working and will update, if any modification in the evaluated data series will be done. Also subsequent processes, which are based on such XLSX documents or refer to their content, can rely on clean documents.
* Built-in mechanisms to distribute the generated Office documents to a FTP storage, via E-mail delivery, or in directories. Doing this, directories, recipient, subject texts u.v.m. can also be parameterized and will be replaced with data of current context.
* Integrated job scheduling to run production automatically for example, daily, per week, at the end of the month and to provide recurrent documents.
* Integrated rights - and role-system for protection of sensitive data modules or complete evaluation prior to illegal execution.
* Simple PL/SQL API, to allow the existing applications, that are based on a SQL-enabled programming language, generate and receive Office documents ad hoc.

This documentation introduces you in all features of smaxt, where the construction of the first part is kept in a chronologically tutorial style. It starts  with the installation, then shows how to produce a simple evaluation document, which is step by step refined and goes deeper and deeper in the smaxt details.

This is followed by a description of all features of smaxt as well as the features of the smaxt Office add-ins and the meaning of the individual forms of the management interface.

In the Appendix then individual aspects of smaxt are listed in detail, so that it can be used as a reference book.

**Important note:**

```
Oracle is a registered trademark of Oracle and/or its affiliates. 
Excel, Office, PowerPoint, Word, Windows and Microsoft are registered trademarks 
or trademarks of Microsoft Corporation in the United States and/or other countries.
```



---

[\[1\]](#_ftnref1) DBO = data-based Office

