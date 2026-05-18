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
**Näide kasutajast: DirectorIrina. Parool: director**
----------------------------------------------------------------
## Kasutaja loomine SQL Serveris
1. Serveritaseme kasutaja loomine (Login)
Sammud
Ava:

Security → Logins
Tee paremklikk ja vali:

New Login...

<img width="692" height="619" alt="{F81FB66F-5AD4-4F72-A4B9-ABE3DFC8FBE8}" src="https://github.com/user-attachments/assets/8dda8181-97bd-4dab-8b0c-dfc40ca2242c" />

Harjutamiseks võib eemaldada linnukese:  User must change password at next login.

**Server Roles**
Menüüst Server Roles saab määrata serveri üldised õigused.

Tavaliselt piisab rollist: public

<img width="608" height="624" alt="{74E6C2F2-D279-4893-BA71-F894D42CCC6E}" src="https://github.com/user-attachments/assets/32010587-ed96-44ae-bfdc-0f96f35c081a" />

2. Andmebaasi kasutaja loomine (User)
Ava:

Database → Security → Users
Tee paremklikk:  New User...

Seosta kasutaja loginiga
<img width="432" height="305" alt="{8DE41755-97AF-4FCF-8B94-566BCB6762AA}" src="https://github.com/user-attachments/assets/aa6d46c4-9d30-4733-ad85-5efb07b48b04" />

**Membership ja õigused**
Menüüst Membership saab määrata kasutaja rollid.

>db_datareader → võib lugeda SELECT

>db_datawriter → võib kirjutada INSERT, UPDATE, DELETE


<img width="704" height="359" alt="{8E881781-2794-4125-8A0E-792277A44AB1}" src="https://github.com/user-attachments/assets/ccfbb016-cbab-4723-8144-83b1e519b719" />

-----------------------------------------------------------------------
## Kasutaja õiguste kontroll

1. tuleb sisselogida kasutajana directorIrina. Connect--> Database Engine

   <img width="475" height="509" alt="{0B7D6CFF-C5A1-4787-AB29-B47C84FC8AD5}" src="https://github.com/user-attachments/assets/c657826a-af2c-4327-80c9-6a231056d101" />

2. saab tabeli sisu näha ja sisestada uus kiri.
   <img width="1304" height="617" alt="{C560C57E-771A-4E21-A4C9-84D3942377A1}" src="https://github.com/user-attachments/assets/ca32536c-fac8-42c6-af6e-86db07f81fb2" />

3. kontrollime tegevus, mis ei ole lubatud kasutajale, näiteks tabeli loomine.

<img width="1350" height="704" alt="{5CC712EA-AE9B-4D4A-B3E8-02F2C462230E}" src="https://github.com/user-attachments/assets/3d88b065-65b8-4b25-9a8c-fd7d6553acfd" />



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

GRANT DELETE ON puhkus TO directorIrina;
GRANT UPDATE ON puhkus TO directorIrina;
GRANT SELECT ON puhkus TO directorIrina;

--keelame INSERT
DENY INSERT ON puhkus TO directorIrina;

```


<img width="832" height="696" alt="{A72F3912-2C8A-4D1F-9906-1ABE1AFC2CED}" src="https://github.com/user-attachments/assets/4b6946ba-ef85-4e85-a985-c4db74bb09c5" />


Käsk	Tähendus
SELECT	Lugemine
INSERT	Lisamine
UPDATE	Muutmine
DELETE	Kustutamine

<img width="1139" height="788" alt="{7D4AB79A-03CD-4E4A-A834-E2D6E2ADBE68}" src="https://github.com/user-attachments/assets/e06dd536-a5e5-4eb4-895c-ae61d0cb22fd" />



    
Ülesanne 1:
Luua andmebaas: MovieBase

Luua tabelid: 

movies (id, moviesNimi, moviesYear, movieDir и movieCost).
guest (id, name)
Lisada vähemalt 7 kirjet.

Luua kasutaja Produtsent parooliga director, kellel on järgmised õigused:
Õigus vaadata ja uuendada tabeli movies välju movieDir ja movieCost + lisada üks enda valitud privileeg.
Õigus vaadata ja lisada kirjeid tabelisse guest.
Keela andmete kustutamine tabelis.
Vihje! UPDATE õigused parem lubada SQL käsuga
GRANT UPDATE (movieCost, movieDir)
ON movies
TO Produtsent;
