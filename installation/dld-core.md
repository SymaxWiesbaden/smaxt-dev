# Download and Installation

\#\#\# Download and Installation



1.  Download the archive \*\*setup\\_smaxt\\_Database\\_Extention\\_V2.00\\_de.zip\*\*

    from \[www.smaxt.com\]\(http://www.smaxt.com/\) or detach the file from the

    mail, if you´ve received the installation-files together with the license

    via email. Move the archive to an appropriate directory.



2.  Open a shell and unzip the archive like this:



&gt;   unzip setup\\_smaxt\\_Database\\_Extention\\_V2.00\\_de.zip



\| \*\*Important\*\*                                                                                                                                                                                                                                                                                                                                                                                                     \|

\|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------\|

\| Make sure, that the directory, you choose fort he unzip-action, does not contain any space-characters, otherwise you´ll receive error during the installation!                                                                                                                                                                                                                                                    \|

\| \*\*Important\*\*                                                                                                                                                                                                                                                                                                                                                                                                     \|

\| If you perform the installation on an Unix-System, verify that the correct case of filenames is preserved. Some fileservers modify filenames durin copy-jobs in that way, that everything is changes to lowercase or only the first letter stays in upper, while the rest is converted to lower.                                                                                                                  \|

\| If your fileserver behaves like this, you´ll get errors during installation and therefore a corrupt smaxt-system.                                                                                                                                                                                                                                                                                                 \|



After unpacking and copying to the appropriate directory, the

subdirectory-structure should look like this:



&gt;   \*/smaxt\*



&gt;   \*/smaxt\\_api\*



&gt;   \*/smaxt\\_test\*



&gt;   \*/sys\*



While all these directories contain several files, you should find the following

ones in the main directory:



&gt;   \*\\_\\_make\\_db.cmd\*



&gt;   \*\\_\\_make\\_db.sh\*



&gt;   \*\\_\\_pwd.dat\*



&gt;   \*\\_\\_readme.txt\*



1.  If you install under UNIX, you must ensure that the user who is running the

    installation has execute privileges to the files. This can be done with the

    command:



&gt;   chmod -R 755 \\*



1.  Start your favorite editor and open the file \*\*\\_\\_pwd.dat\*\* to adjust

    passwords of the technical smaxt-users.  

    This file looks like  

      

    \*sys=sys\*  

    \*smaxt=smaxt\*  

    \*smaxt\\_test=smaxt\\_test\*  

    \*smaxt\\_api=smaxt\\_api\*  

    \*import\\_user=\\*\*  

      

    The password for the SYS user must set only for the reason, as in the first

    step of the installion, the smaxt user SMAXT, SMAXT\\_API and SMAXT\\_TEST are

    created, and for this SYS privileges are required.  

    For the technical smaxt users, you can choose the passwords as you like.  

    These are necessary, when you register a connection in smaxt Management

    Studio, or the smaxt Office add-ins or work with an application, that uses

    the smaxt API.  

      

    The user \*\*IMPORT\\_USER\*\* is initially set to \\*, which is retained for an

    initial installation. But if you´re later on installing an smaxt update with

    the option \*install\\_core\* \(see below\) and already have activated the

    rights&role-system, instead of \\*, you have to provide the logical

    smaxt-user here, that is entitled to perform imports.



2.  Check the ACL settings by opening the file \*\*sys/acl.sql\*\* in your favorite

    editor. This script determines which IP addresses the technical smaxt user

    can communicate with, if produced documents should be distributed via FTP or

    SMTP.  

    The default-behaviour of this script is:



3.  The database is bound to the \*\*Local-Loopback-Adapter 127.0.0.1\*\*, then

    communication can be done with any IP-address \(\*\*\\*\*\*\).



4.  Otherwise, the first section of the IP-address of the Databaseserver will be

    kept and the remaining sections will be set to \\* \(f.e. \*\*10.0.1.12\*\* will

    be set to \*\*10.\\*\)\*\* so that communication with any IP in your local

    environment should be possible.



    If you don´t agree with this, you can modifiy the script by assigning the

    desired IP-information to the variable \*\*v\\_host\*\* in lines 27 and 31.



5.  Verify and eventually modify the script \*\*sys/user.sql\*\*  

    When you invoke the following installation step with the option "full" or

    "createusers", then the required smaxt-user are created automatically in the

    destination database.  

    However, this will be done by assigning the default-tablespace settings,

    which typically is USERS as "default tablespace" and TEMP as "temporary

    tablespace"  

    \(see also 7.6.1.2 und 7.6.1.3\).  

    If you want to assign other tablespaces, you have to modify the script by

    adding following lines tot he CREATE USER - command:



&gt;   …



&gt;   DEFAULT TABLESPACE \&lt;usrtblspc\&gt;



&gt;   TEMPORARY TABLESPACE \&lt;tmptblspc\&gt;



&gt;   …



1.  Now perform the actual installation with the help of the script

    \*\*\\_\\_make\\_db.cmd\*\* \(for Windows\) or \*\*\\_\\_make\\_db.sh\*\* \(for Unix\).  

    Syntax of a \\_\\_make\\_db – call is like:



&gt;   \\_\\_make\\_db.cmd targetdb \[full\\|{createusers{ installcore{ installdemo}}}\]



&gt;   or



&gt;   ./\\_\\_make\\_db.sh targetdb \[full\\|{createusers{ installcore{ installdemo}}}\]



&gt;   For \*targetdb\* , the \*TNSNAME\* of the target database is expected \(f.e.:

&gt;   \*mydb.world\*\).  

&gt;   Alternatively, instead of a \*TNSNAME, you can also provide an

&gt;   EZCONNECT\*-sequence, which can be useful, if \*TNSNAME\*-resolution will not

&gt;   work against the target server. An \*EZCONNECT\*-Sequence followst he pattern:



&gt;   ipaddress:port/servicename



&gt;   f.e.: \*10.0.1.12:1521/mydb.world\*  

&gt;   



&gt;   If you encounter problems both variants, as for example the target database

&gt;   is already defined through environment variable and therefore the SQLPLUS

&gt;   call does not accept any \&lt;connect\\_identifier\&gt;, then you simply provide \@

&gt;   as targetdb.



&gt;   The kind of the installation is controlled with the second parameter of

&gt;   \\_\\_make\\_db.



&gt;   If \*full\* is specified, the smaxt users are created, the smaxt kernel will

&gt;   be installed and the test- and demo-data as well \(in the schema

&gt;   \*\*smaxt\\_TEST\*\*\).



&gt;   \\_\\_make\\_db.\[cmd\\|sh\] mydb.world full



&gt;   Instead of \*full\* you can a.so specifiy any combinition of the other

&gt;   installation-kind keywords, like f.e.:



&gt;   \\_\\_make\\_db.\[cmd\\|sh\] mydb.world createusers installcore



&gt;   for only creating the smaxt-users and install the smaxt core system, or:



&gt;   \\_\\_make\\_db.\[cmd\\|sh\] mydb.world installdemo



&gt;   to install the test- and demo-data later on.



