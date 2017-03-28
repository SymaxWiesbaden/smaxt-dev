### Activating the license

After the installation of the smaxt core is done, the license information must be installed. You have received this along with the download instructions and it looks somewhat like this:

`UPDATE lookup SET intval = 30,strval= 'your company', txtval='256805E1DF9A4DD9B1F390FBF936F1DA98E1124EF9D3040132BA6322D3C27E7ED90898634E2F92592BFC6F4F9CBCAC65BB9EA9EAFB5C67BCB2ED69265FBE9FDC6CB8A19E76FCE56D34E85C8CDBF8D4898FD09738A488C5D117C54DC4C6A484B290D4DEA19D24F0A87E323B72C8E1FD9BFC1A2BEBDFA5ED2182099668FBE96EC2F4E9EF9C3ED3398DE1E11B30E99463BA9A417306E6F5B8224AB7361E257404B1CA' WHERE CATEGORY = 'DBVersion' AND NAME = 'LicInfo';`

Copy your personal license information into clipboard and start _SQLPLUS_.

Connect tot he target-database with user **SMAXT** \(use the password you have set in the installation, which by default is **smaxt**\) and paste the license-info from clipboard into the _SQLPLUS_-window and press _Enter_.

Finally type **COMMIT;** and again press _Enter_.

he whole process should look similar like this:

`• sqlplus smaxt/smaxt@127.0.0.1:1521/orcl.symaxag.de`

`SQL*Plus: Release 11.2.0.3.0 Production on Mo Mai 12 13:09:32 2014`

`Copyright © 1982, 2011, Oracle. All rights reserved.`

`Verbunden mit:`

`Oracle Database 11g Release 11.2.0.1.0 - Production`

`• UPDATE lookup SET intval = 30,strval=’your company’, txtval=’256805E1DF9A4DD9B1F390FBF936F1DA98E1124EF9D3040132BA6322D3C27E7ED90898634E2F92592BFC6F4F9CBCAC65BB9EA9EAFB5C67BCB2ED69265FBE9FDC6CB8A19E76FCE56D34E85C8CDBF8D4898FD09738A488C5D117C54DC4C6A484B290D4DEA19D24F0A87E323B72C8E1FD9BFC1A2BEBDFA5ED2182099668FBE96EC2F4E9EF9C3ED3398DE1E11B30E99463BA9A417306E6F5B8224AB7361E257404B1CA’ WHERE CATEGORY = 'DBVersion’ AND NAME = 'LicInfo’;`

`1 Zeile wurde aktualisiert.`

`• commit;`

`Transaktion mit COMMIT abgeschlossen.`

