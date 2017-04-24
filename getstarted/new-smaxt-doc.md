## Create a new smaxt document

There are two ways to create a new smaxt document:

* Based on an existing data template[^1]
* From scratch", i.e. by selecting objects granted to smaxt
  \(see chapter [Give permissions to smaxt](/installation/give-permissions-to-smaxt.md)\)

In the present case, a document "from scratch" is to be created, by selecting a table or view shared with smaxt.  
 Therefore, click the _"Create from scratch"_ option in the smaxt ribbon:

![](/assets/create-from-scratch.png)

### Login to the database

Since there is no connection to a smaxt database yet, the prompt will appear to log in to the desired database:

![](/assets/smaxt-db-login.png)

Use the combination button \(1\) to select the desired database connection. Since this is a new installation, you must first define a connection \(see below\) by clicking on the button \(2\). Then enter your name \(3\) and your password \(4\).

Note

> After a new installation, each username is allowed and the password **password** is valid for all users. Restrictions can be made later in "Accounts, Rights and Roles".

In the dialog for managing the database connections, the technical connection data for the target database are recorded and stored under an alias name.  
  Please ask your database administrator for the settings you need to make.

![](/assets/smaxt-database-settings.png)

To create a new entry, click the \[+\] button and enter a displayname, the address of the database server, the port, and the service name. It is important that you establish a connection with the technical user **smaxt**, whose password was set in step "[Download and installation](/installation/dld-core.md)".

Note:

> The configured database connections shared by the smaxt modules are stored  
> in `%appdata%\Symax\Smaxt\dbconfig.properties`.
>
> The section "7.5.2 Configuring / distributing configured database connections" provides information on how to save this file or to maintain it centrally and distribute it to several computers.

### Selecting the object to be reported

After you have logged in, all database schemas, in which objects have been shared to smaxt, are offered to you[^2]. Below the schema nodes, the respective shared objects are listed \(1\).

As soon as the object to be reported has been selected in the upper part, a list of possible columns is offered in the middle \(2\), which are all selected by default.

An optional sort can also be set under "order by" \(3\), in which the column to be sorted and the mode, ascending or descending, are defined.

Finally, you have to specify a category \(4\) and a name \(5\) for the query before you can click "Ok".

![](/assets/smaxt-choose-table-or-view.png)

Optionally, you can set the "preview SQL" checkbox to check the automatically generated SQL statement and, if necessary, manually edit it and then validate it against the database.

### Positioning of smaxt objects

In the previous step, you selected a table or view and the columns and then clicked "ok".  In this way, some smaxt objects have been created in the background:

* First, a data module, based on the generated SQL query, was created
* Second, a data template named with the alias `"PRODUCTLIST"` was created and the previously generated data module has been added to it.
* Third, a data configuration has been created. Usually, this would not be necessary for such simple and unparameterized applications. However, the data has to be available for the production of an Excel document - anyhow.\(Data Configurations will be described later in this document\).

All three object types were stored in the category, defined in step "Selecting the object to be reported". The category was named, as defined in this step \(`/GettingStarted`\).

In order to avoid collisions with evaluations of the same name, which are recorded by persons working in parallel, a unique number has been attached to the names so that the name `PRODUCTLIST` is ultimately replaced by e.g. `Productlist_10001`.

In the smaxt taskpane at the right screen side in Excel, you can now see that Datamodule object . It has the aliasname  `PRODUCTLIST` and returns a table.

This shall be placed now into the Excel sheet at cell B2.  This works by drag and drop. Therefore select the object, keep the left mouse button pressed, draw it to the cell B2 and release the mouse button. This is shown in the following image:

![](/assets/drag-object-to-excel.png)

[^1]: Data templates are described later. In short, this is a collection of 1 to n data modules, which are specific database queries. So data templates are a kind of pattern for data collections.

[^2]: Depending on the size of the database and the number of objects to be examined, it may take a few seconds until the dialog appears and you can select objects.

