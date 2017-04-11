# Getting started

In this section you learn, how to create the first simple report with smaxt. You will see how you can easily create simple Excel documents with smaxt.

At this point, we are deliberately refraining from showing you the additional advanced features of smaxt, such as

* parameterization, 
* iteration quantities, 
* user rights,
* job control etc. 

These are discussed in detail in the following section "Understanding smaxt", together with all other features.

Although the following steps produce only a simple Excel report, the procedure is still a good entry point because the smaxt objects generated in this process can be extended and refined.

## Run Excel

After installing the smaxt Excel add-in, it is loaded automatically every time you start Excel. Therefore you will find the additional entry "smaxt" in the menu ribbon:

![](/assets/smaxt-ribbon.png)

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



In the dialog for managing the database connections, the technical connection data for the target database are recorded and stored under an alias name.  Please ask your database administrator for the settings you need to make.

![](/assets/smaxt-database-settings.png)

To create a new entry, click the \[+\] button and enter a displayname, the address of the database server, the port, and the service name. It is important that you establish a connection with the technical user **smaxt**, whose password was set in step "[Download and installation](/installation/dld-core.md)".



[^1]: Data templates are described later. In short, this is a collection of 1 to n data modules, which are specific database queries. So data templates are a kind of pattern for data collections.

