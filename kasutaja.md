# Teised Konspektid 
[PROTSEDUURID](PROTSEDUURID.md) | [Select_laused](mockaroo.md) | [Kasutajate_loomine SQL server](kasutaja.md) | [Triggerid](trigerid.md) | [Kodutöö - keys](keys.md) | [Kasutaja loomine XAMPP-is](kasutajaXampp.md) |
[vaaded](vaade.md)


## SQL Server – Kasutajate autentimine ja õiguste haldamine
Mis on autentimine SQL Serveris?
 ### Autentimine tähendab kasutaja tuvastamist ehk kontrollimist, kas kasutajal on õigus SQL Serverisse sisse logida.

**SQL Serveris kasutatakse kahte peamist autentimise tüüpi:**

1. Windows Authentication
Selle puhul kasutatakse samu kasutajaandmeid, millega logitakse sisse Windows operatsioonisüsteemi.

>Kasutajanimi ja parool on seotud Windowsiga. 
>Turvalisem lahendus. 
>Paroole haldab Windows. 
>Kasutaja ei pea eraldi SQL Serveri parooli teadma.

2. SQL Server Authentication
>Selle puhul luuakse kasutaja otse SQL Serverisse.
>Kasutaja ei ole seotud Windowsiga. 
>Määratakse eraldi kasutajanimi ja parool. 
>Sobib veebirakenduste jaoks. 
---------------------------------------------------------------
**Näide kasutajast: sekretarRobert. Parool: petrosyan**
----------------------------------------------------------------
## Kasutaja loomine SQL Serveris
1. Serveritaseme kasutaja loomine (Login)
Sammud
Ava:

Security → Logins
Tee paremklikk ja vali:

New Login...

<img width="722" height="654" alt="{379A48B3-AD78-4E12-AFE6-D6E40D23552B}" src="https://github.com/user-attachments/assets/d6e0ff5c-4c1e-45d6-8fc0-368e67472d14" />



Harjutamiseks võib eemaldada linnukese:  User must change password at next login.

**Server Roles**
Menüüst Server Roles saab määrata serveri üldised õigused.

Tavaliselt piisab rollist: public


<img width="716" height="652" alt="{36944406-EFB1-49BE-88A5-9761A1C595BA}" src="https://github.com/user-attachments/assets/cfe79e82-9efe-430c-ac96-ddf3085643b5" /> 

2. Andmebaasi kasutaja loomine (User)
Ava:

Database → Security → Users
Tee paremklikk:  New User...

Seosta kasutaja loginiga

<img width="299" height="125" alt="{491E93CD-9217-4430-9B38-11D133EA59C0}" src="https://github.com/user-attachments/assets/441ad5ab-4151-448c-9ba6-3c1a11e8d007" />



**Membership ja õigused**
Menüüst Membership saab määrata kasutaja rollid.

>db_datareader → võib lugeda SELECT

>db_datawriter → võib kirjutada INSERT, UPDATE, DELETE


<img width="702" height="651" alt="{5938AA54-D649-4E56-8394-9FA74E9D2952}" src="https://github.com/user-attachments/assets/3e958787-f1b7-45f8-99fa-acf9b31e6a60" />

-----------------------------------------------------------------------
## Kasutaja õiguste kontroll

1. tuleb sisselogida kasutajana sekretarRobert. Connect--> Database Engine

<img width="474" height="514" alt="{70E245D6-DE3A-40D9-8931-798033A1DD73}" src="https://github.com/user-attachments/assets/3d0feb71-dc26-4de9-95c0-94b78f8e7489" />


2. saab tabeli sisu näha ja sisestada uus kiri.
  <img width="994" height="531" alt="{C685B554-1915-4AA5-8D5F-98AAD65AA21A}" src="https://github.com/user-attachments/assets/4a1d9c80-fee1-4a68-a6bf-705d611d848b" />


3. kontrollime tegevus, mis ei ole lubatud kasutajale, näiteks tabeli loomine.

<img width="1004" height="504" alt="{E3013AD3-EA82-40A8-BBB2-C6050B75C85A}" src="https://github.com/user-attachments/assets/97bd6852-ec07-4e6a-8109-29a122f37c85" />




------------------------------------------------------------------------
SQL Server Authentication Mode muutmine
Kui ilmub viga: Error 18456, siis on tavaliselt lubatud ainult Windows Authentication.
Lahendus
Server → Properties
Security
Vali: SQL Server and Windows Authentication mode
GRANT käsud õiguste jagamiseks
GRANT käsuga antakse kasutajale õigused.

```sql
--GRANT - õiguste määramine
--DENY - õiguste keelamine

--db_datareader -SELECT 
--db_datawriter - INSERT, DELETE, UPDATE

--anname kasutajale directorIrina õigus 
--ainult kustutada ja uuendada tabelit 
--(DELETE, UPDATE, SELECT)

GRANT DELETE ON puhkus TO sekretarRobert;
GRANT UPDATE ON puhkus TO sekretarRobert;
GRANT SELECT ON puhkus TO sekretarRobert;

--keelame INSERT
DENY INSERT ON puhkus TO sekretarRobert;
```


<img width="834" height="588" alt="{E3B04D42-A4B6-43ED-A766-98A9DA775A50}" src="https://github.com/user-attachments/assets/56c61f45-685e-41b2-bd53-274d2b323ef9" />



Käsk	Tähendus
SELECT	Lugemine
INSERT	Lisamine
UPDATE	Muutmine
DELETE	Kustutamine

<img width="1023" height="646" alt="{9F89EBDD-498A-4FD7-83A2-F03756B74532}" src="https://github.com/user-attachments/assets/675433b6-216f-46c4-a661-2971c5c722f6" />





