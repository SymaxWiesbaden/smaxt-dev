### Give permissions to smaxt

Smaxt only can create documents based on tables and views or table functions, if these are granted to the user smaxt. For tables and views, the SELECT right is necessary. You can grant this right to the required objects individually, by executing the respective _GRANT_ command:

`> grant select on <tablename|viewname> to smaxt;`

Use the following statement to create a script that creates the necessary GRANT rights for all tables and views for a specific owner \(= schema\). Run the script and type the desired owner name at the prompt:

`SET DEFINE ON`

`SET FEEDBACK OFF`

`SET PAGESIZE 0`

`spool _grants.sql`

`SELECT 'grant select on ' || o.owner || '.' || o.object_name || ' to SMAXT;' grant_cmd`

`FROM all_objects o`

`WHERE o.OBJECT_TYPE IN ('TABLE', 'VIEW')`

`AND o.OWNER = upper('&ownername')`

`ORDER BY o.OBJECT_NAME;`

`Beenden Sie die Ausgabe schließlich noch mit dem Befehl:`

`spool OFF`

Finally, exit the output with the command:

`spool OFF`

After the execution, the **file \_grants.sql** is located in the current directory. Please open it with your favorite editor and look nfor unwanted sharing, etc. You can then run the generated script with the named owner or as SYS to grant the permissions to smaxt. However, to evaluate return rates, which are provided by so-called table functions, the right is not the _SELECT_ but the _EXECUTE _right:

`grant execute on <functionname> to SMAXT;`

If the table function is within a package, it can not be released individually. Instead, the EXECUTE privilege must be granted at the package level:

`grant execute on <packagename> to SMAXT;`

**Note:**

> You can first of all release all the objects to smaxt and then use the smaxt-proprietary "rights and roll system" to allow user-specific individual queries to be made or prevented \(see chapter "Accounts, rights and roles"\).



