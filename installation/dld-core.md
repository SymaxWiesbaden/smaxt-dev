### Download and Installation

#### 1. Download the archive

Download the archive \*\*setup\_smaxt\_Database\_Extention\_V3.00\_en.zip\*\* from \[www.smaxt.com\]\([http://www.smaxt.com/\](http://www.smaxt.com/%29\) or detach the file from the email, if you´ve received the installation-files together with the license via email. Move the archive to an appropriate directory.

#### 2. Unzip the archive

Open a shell and unzip the archive like this:

`>   unzip setup\_smaxt\_Database\_Extention\_V2.00\_de.zip`

**Important:**

> Make sure, that the directory, you choose fort he unzip-action, does not contain any space-characters, otherwise you´ll receive error during the installation!

**Important: **

> If you perform the installation on an Unix-System, verify that the correct case of filenames is preserved. Some fileservers modify filenames durin copy-jobs in that way, that everything is changes to lowercase or only the first letter stays in upper, while the rest is converted to lower.
>
> If your fileserver behaves like this, you´ll get errors during installation and therefore a corrupt smaxt-system.

After unpacking and copying to the appropriate directory, the subdirectory-structure should look like this:

```
> /smaxt
> /smaxt_api
> /smaxt_test
> /sys
```

While all these directories contain several files, you should find the following ones in the main directory:

```
> __make_db.cmd
> __make_db.sh
> __pwd.dat
> __readme.txt
```

#### 3. Installation under UNIX

If you install under UNIX, you must ensure that the user who is running the installation has execute privileges to the files. This can be done with the command:

```
 chmod -R 755 \\*
```

#### 4. Adjust passwords of the technical smaxt-users

Start your favorite editor and open the file `__pwd.dat` to adjust passwords of the technical smaxt-users. This file looks like:

```
 \*sys=sys\*  
 \*smaxt=smaxt\*  
 \*smaxt\\_test=smaxt\\_test\*  
 \*smaxt\\_api=smaxt\\_api\*  
 \*import\\_user=\\*\*
```

The password for the _SYS-User_ must be set only for the reason, as in the first step of the installion, the smaxt users _SMAXT_, _SMAXT\_API_ and _SMAXT\_TEST_ are created, and for this SYS privileges are required.

For the technical smaxt users, you can choose the passwords as you like. These are necessary, when you register a connection in smaxt Management Studio, or the smaxt Office add-ins or work with an application, that uses the smaxt API.

The user **IMPORT\_USER** is initially set to \_, which is retained for an initial installation. But if you´re later on installing an smaxt update with the option `install_core` \(see below\) and already have activated the rights and role-system, instead of \_, you have to provide the logical smaxt-user here, that is entitled to perform imports.

#### 5. Check ACL Settings

Check the ACL-Settings by opening the file `sys/acl.sql` in your favorite editor. This script determines which IP-Addresses the technical smaxt user can communicate with, if produced documents should be distributed via FTP or SMTP. The default-behaviour configured in this script is:

1. If the database is bound to the **Local-Loopback-Adapter 127.0.0.1**, then communication can be done with any IP-address \(\*\).
2. In other cases, the first section of the IP-address of the Database-Server will be kept and the remaining sections will be set to \(\*\), so that communication with any IP in your local environment should be possible. For example **10.0.1.12** will be set to **10.\***

   If you don´t agree with this, you can modifiy the script by assigning the desired IP-information to the variable `v\_host` in line 27 and 31.

#### 6. Ceck the script sys/user.sql

Nect you have to verify the script `sys/user.sql` and eventually to modify it. When you invoke the following installation step with the option "full" or"createusers", then the required smaxt-user are created automatically in the destination database.

However, this will be done by assigning the default-tablespace settings, which typically is _USERS_ as "default tablespace" and _TEMP_ as "temporary tablespace" \(see also 7.6.1.2 und 7.6.1.3\).

If you want to assign other tablespaces, you have to modify the script by adding following lines to the _CREATE USER_ - command:

`>   …`

`>   DEFAULT TABLESPACE \<usrtblspc\>`

`>   TEMPORARY TABLESPACE \<tmptblspc\>`

`>   …`

#### 7. Run installation script

Now perform the installation with the help of the script **\_\_make\_db.cmd** \(for Windows\) or **\_\_make\_db.sh** \(for Unix\). The syntax of a **\_\_make\_db** – call is like:

`>   __make_db.cmd targetdb [full|{createusers{ installcore{ installdemo}}}]`

or

`>   ./__make\_db.sh targetdb [full|{createusers{ installcore{ installdemo}}}]`

For _targetdb_ , the _TNSNAME_ of the target database is expected \(f.e.: mydb.world\). Alternatively, instead of a _TNSNAME_, you can also provide an _EZCONNECT_-sequence, which can be useful, if _TNSNAME_-resolution will not work against the target server. An _EZCONNECT_-sequence follows the pattern:

`>   ipaddress:port/servicename`

For example: _10.0.1.12:1521/mydb.world_

If you encounter problems with both variants, as for example the target database is already defined through environment variable and therefore the SQLPLUS call does not accept any _&lt;connect\_identifier&gt;_, then you simply provide @ as targetdb.

The kind of the installation is controlled with the second parameter of **\_make\_db**_. If full_ is specified, the smaxt users are created, the smaxt kernel will be installed and the test- and demo-data will be installed in the schema _smaxt\_TEST_.

`>   __make_db.[cmd|sh] mydb.world full`

Instead of _full_ you can a.so specifiy any combinition of the other installation-kind keywords, like f.e.:

`>   __make_db.[cmd|sh] mydb.world createusers installcore`

for only creating the smaxt-users and install the smaxt core system, or:

`>   __make_db.[cmd|sh] mydb.world installdemo`

to install the test- and demo-data later on.

**Update installieren:**

> If you´re already running a previous version of smaxt, there is no need to install the smaxt users again, so you can simply use the parameter "installcore", or, if you like to to update the test- and demo-data as well, the combination "installcore installdemo".

If you have specified the desired combination of **\_\_make\_db** parameters, press _Enter \_to start the installation.  
 All steps of the installation will be logged in the file \*\*\_\_make\_db.log\*\*. The installation typically takes less than five minutes, even when doing a full installation.[^2]

After the installation please open the **\_\_make\_db.log **file and check it for appearances of ORA-messages to identify possible errors that might have appeared during the installation.[^1]

**Note:**

> Occasionally we have noticed problems during upload and processing of smaxt-internal reports and demo-projects \(SEP-files\). You can recognize those problems by the messages "ERROR: wrong storage format, file can not be processed!" or "Could not add LogMsg to non-active JobId". Until now, we have not found the reason for this, but it looks like, that on some systems, processing the SEP-files with SQLLDR leads to an illegal modification of the files, so that subsequent processing fails. Anyway, the function of the smaxt core system is not affected due to this problem. However, you should import the smaxt's internal reports and sample-projects manually through Management Studio \(see 5.3.2 Importieren\). You´ll find these SEP-files in the directories\_ /smaxt/reports \_and /smaxt\_test/reports of the extracted archive.

[^1]: At some steps of the installation, warnings can be issued, wich can be irgnored. They can easily be identified as they start with "! Warning is ok here, because we try to xxx from xxx that are defined later...".

[^2]: Please keep in mind, that during the installation, it may sometimes look like it is freezed, because nothing happens for a while \(for example during processing of TSX\_OOXML\_WORKBOOK\_type\_bdy.sql\). But this is not the case, as for larger and more complex elements, it can possibly take a while until they are installed correctly.

