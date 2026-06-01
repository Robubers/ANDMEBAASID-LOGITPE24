# Teised Konspektid 
[PROTSEDUURID](PROTSEDUURID.md) | [Select_laused](mockaroo.md) | [Kasutajate_loomine SQL server](kasutaja.md) | [Triggerid](trigerid.md) | [Kodutöö - keys](keys.md) | [Kasutaja loomine XAMPP-is](kasutajaXampp.md) |
[vaaded](vaade.md)


# Andmebaasi võtmete mõisted

## 1. Primary Key (Primaarvõti)

### Definitsioon

Primary Key on väli või väljade kombinatsioon, mis identifitseerib iga tabeli rea unikaalselt.

### Milleks kasutatakse

* Andmete üheseks tuvastamiseks.
* Tabelite vaheliste seoste loomiseks.
* Duplikaatide vältimiseks.

### Mille poolest erineb teistest võtmetest

* Ei tohi sisaldada NULL väärtusi.
* Tabelis saab olla ainult üks Primary Key.
* Valitakse kandidaatvõtmete hulgast peamiseks identifikaatoriks.


Siin on **ÕpilaseID** Primary Key, sest iga väärtus on unikaalne.

---

## 2. Foreign Key (Võõrvõti)

### Definitsioon

Foreign Key on väli, mis viitab teise tabeli Primary Key-le.

### Milleks kasutatakse

* Tabelite omavaheliseks ühendamiseks.
* Andmete tervikluse tagamiseks.

### Mille poolest erineb teistest võtmetest

* Ei pea olema unikaalne.
* Võib sisaldada korduvaid väärtusi.
* Viitab teise tabeli võtmele.



Siin on **ÕpilaseID** Foreign Key, sest see viitab tabeli Õpilased väljale ÕpilaseID.

---

## 3. Unique Key

### Definitsioon

Unique Key tagab, et kõik väärtused veerus on unikaalsed.

### Milleks kasutatakse

* Duplikaatide vältimiseks.
* Alternatiivsete unikaalsete tunnuste määramiseks.

### Mille poolest erineb teistest võtmetest

* Tabelis võib olla mitu Unique Key-d.
* Võib sisaldada NULL väärtusi (sõltub andmebaasisüsteemist).
* Ei ole tabeli peamine identifikaator nagu Primary Key.



Siin on **Email** Unique Key, sest sama e-posti aadress ei tohi korduda.

---

## 4. Simple Key

### Definitsioon

Simple Key koosneb ainult ühest atribuudist ehk ühest veerust.

### Milleks kasutatakse

* Ridade lihtsaks identifitseerimiseks.

### Mille poolest erineb teistest võtmetest

* Sisaldab ainult ühte välja.
* Vastand Composite Key-le, mis koosneb mitmest väljast.



Siin on **ISBN** Simple Key.

---

## 5. Composite Key

### Definitsioon

Composite Key koosneb kahest või enamast väljast, mis koos moodustavad unikaalse võtme.

### Milleks kasutatakse

* Kui üks väli üksi ei ole unikaalne.

### Mille poolest erineb teistest võtmetest

* Koosneb mitmest atribuudist.
* Kõik võtme osad koos peavad olema unikaalsed.


Siin moodustavad **ÕpilaseID + KursuseID** Composite Key.

---

## 6. Compound Key

### Definitsioon

Compound Key on Composite Key eriliik, kus kõik võtme osad on samuti Foreign Key-d.

### Milleks kasutatakse

* Seostabelites mitme tabeli ühendamiseks.

### Mille poolest erineb teistest võtmetest

* Kõik väljad viitavad teiste tabelite võtmetele.
* Kasutatakse sageli “many-to-many” seoste puhul.


Siin moodustavad **TellimusID + TooteID** Compound Key, sest mõlemad on Foreign Key-d.

---

## 7. Superkey

### Definitsioon

Superkey on üks või mitu välja, mis võimaldavad tabeli rea unikaalselt tuvastada.

### Milleks kasutatakse

* Unikaalsete identifikaatorite määramiseks.

### Mille poolest erineb teistest võtmetest

* Võib sisaldada liigseid atribuute.
* Candidate Key on Superkey minimaalne vorm.


Võimalikud Superkey-d:

* TöötajaID
* Isikukood
* TöötajaID + Nimi

---

## 8. Candidate Key

### Definitsioon

Candidate Key on minimaalne Superkey, mis identifitseerib rea unikaalselt.

### Milleks kasutatakse

* Primary Key kandidaadina.

### Mille poolest erineb teistest võtmetest

* Ei sisalda liigseid atribuute.
* Tabelis võib olla mitu Candidate Key-d.



Candidate Key-d:

* TöötajaID
* Isikukood

Mõlemad on unikaalsed ja minimaalsed.

---

## 9. Alternate Key

### Definitsioon

Alternate Key on Candidate Key, mida ei valitud Primary Key-ks.

### Milleks kasutatakse

* Täiendava unikaalsuse tagamiseks.

### Mille poolest erineb teistest võtmetest

* On samuti unikaalne.
* Ei ole tabeli peamine võti.


Kui Primary Key on **TöötajaID**, siis:

* **Isikukood** võib olla Alternate Key.
* **Email** võib samuti olla Alternate Key, kui see on unikaalne.

---

# Kokkuvõte

| Võti          | Peamine omadus                                |
| ------------- | --------------------------------------------- |
| Primary Key   | Peamine unikaalne identifikaator              |
| Foreign Key   | Viitab teise tabeli võtmele                   |
| Unique Key    | Väärtused peavad olema unikaalsed             |
| Simple Key    | Koosneb ühest väljast                         |
| Composite Key | Koosneb mitmest väljast                       |
| Compound Key  | Composite Key, mille osad on Foreign Key-d    |
| Superkey      | Identifitseerib rea unikaalselt               |
| Candidate Key | Minimaalne Superkey                           |
| Alternate Key | Candidate Key, mida ei valitud Primary Key-ks |















# SQL näited erinevate võtmete kohta

```sql
create database robert
use robert

create table telefonid(
telefonid_id int primary key identity(1,1),
telefoniNimetus varchar(20),
kogus int,
Kuupäev varchar(100),
telefoniHind money)

insert into telefonid(telefoniNimetus, kogus, Kuupäev, telefoniHind)
values('iPhone 16', 2000, '2026-10-5', 200)

insert into telefonid(telefoniNimetus, kogus, Kuupäev, telefoniHind)
values('iPhone 17', 1000, '2026-11-2', 1200)

insert into telefonid(telefoniNimetus, kogus, Kuupäev, telefoniHind)
values('iPhone 15', 500, '2024-12-14', 600)
```

---

# 1. Primary Key näide

```sql
create table telefonid(
telefonid_id int primary key identity(1,1),
telefoniNimetus varchar(20),
kogus int,
Kuupäev varchar(100),
telefoniHind money)
```

Selgitus:

* `telefonid_id` on Primary Key.
* Iga telefon saab unikaalse ID.

<img width="582" height="491" alt="{06E859B5-B38C-41E1-8FC0-3FFC99CF601B}" src="https://github.com/user-attachments/assets/f9270ab2-e323-4823-95a6-f51a1bd4a04c" />


---

# 2. Foreign Key näide

```sql
create table tellimused(
tellimusID int primary key identity(1,1),
telefonid_id int,
kogus int,

foreign key (telefonid_id)
references telefonid(telefonid_id)
)
```

Selgitus:

* `telefonid_id` on Foreign Key.
* See viitab tabeli `telefonid` Primary Key-le.

<img width="405" height="277" alt="{FEB21D5E-26BA-4F8C-8626-5B00AEEC584D}" src="https://github.com/user-attachments/assets/3083f881-7c33-4ae0-96fb-ac8782104771" />


---

# 3. Unique Key näide

```sql
create table kasutajad(
kasutajaID int primary key identity(1,1),
email varchar(100) unique
)
```

Selgitus:

* Sama e-mail ei saa korduda.

Sisesatsin tabelise enda meili:

<img width="484" height="348" alt="{259D29E4-9A8C-4012-BFE6-562B0135F908}" src="https://github.com/user-attachments/assets/5cd82052-40d8-43a2-beac-db7edc1f47f6" />

Sisestasin uuesti samat meili:

<img width="1294" height="375" alt="{041FF974-4125-4D3A-BC98-5A72E2653BD2}" src="https://github.com/user-attachments/assets/e5419d87-aa1d-41e2-89d3-087b4f52e27d" />

---

# 4. Simple Key näide

```sql
create table kliendid(
klientID int primary key,
nimi varchar(50)
)
```

Selgitus:

* `klientID` koosneb ainult ühest väljast.
* See on Simple Key.


Kontrollin Simple Key toimimist nii:
<img width="373" height="369" alt="{E2507410-97EE-4BDB-8989-3061E2EBB0C4}" src="https://github.com/user-attachments/assets/5c4ba23a-0413-45bf-8028-61dfce0deb28" />

Sisestasin sama ID, SQL annab vea, sest klientID on Primary Key ja peab olema unikaalne:

<img width="1165" height="456" alt="{09222993-3ADF-49AA-8F9C-1F5BAB138BA4}" src="https://github.com/user-attachments/assets/b7edcd1d-a7b9-4b2b-b609-370e88217300" />


# 5. Composite Key näide

```sql
create table kursused(
opilaneID int,
kursusID int,
hinne int,

primary key(opilaneID, kursusID)
)
```

Selgitus:

* Võti koosneb kahest väljast.
* Mõlemad väljad koos peavad olema unikaalsed.

Lisasin andmed tabelisse:

<img width="499" height="359" alt="{59AAE85A-FF34-4755-B135-F390E602803F}" src="https://github.com/user-attachments/assets/cf18b943-c13a-4643-8d42-d68e657701c2" />


Proovisin lisada sama kombinatsioon uuesti, SQL andis vea sest sama kombinatsioon ei tohi korduda:

<img width="536" height="562" alt="{97131917-8411-4F5F-BE7B-67171542D370}" src="https://github.com/user-attachments/assets/200c1f77-101e-4c2a-96a0-b37e4972506b" />



---

# 6. Compound Key näide

```sql
create table telefoniTellimus(
telefonid_id int,
tellimusID int,
kogus int,

primary key(telefonid_id, tellimusID),

foreign key (telefonid_id)
references telefonid(telefonid_id),

foreign key (tellimusID)
references tellimused(tellimusID)
)
```

Selgitus:

* Primary Key koosneb kahest Foreign Key-st.
* See on Compound Key.

---

# 7. Superkey näide

```sql
create table tootajad(
tootajaID int primary key,
isikukood varchar(20) unique,
nimi varchar(50)
)
```

Superkey näited:

* `tootajaID`
* `isikukood`
* `tootajaID + nimi`

Selgitus:

* Kõik need suudavad töötaja unikaalselt tuvastada.


Lisan andmed tabelisse:
<img width="506" height="139" alt="{7AE643FB-D4F2-4704-A2C7-F5AA4145084D}" src="https://github.com/user-attachments/assets/02f72e75-275d-4493-b3b4-1f386847116e" />

Kontrollin töötaja ID järgi:
<img width="300" height="75" alt="{93AB7825-5AF2-405F-9C65-2DAF9D00A8A2}" src="https://github.com/user-attachments/assets/fab5eba2-c5e1-494a-a333-d2ee69adbf2b" />


Kontrollin isikukoodi järgi:
<img width="354" height="161" alt="{36322B9C-B767-49AC-A1C3-32562D6CA61C}" src="https://github.com/user-attachments/assets/7bbe098d-873b-4dbd-b0ac-1527d8c73020" />

Kontrollin kombinatsiooni:
<img width="327" height="256" alt="{E362CB3F-96BB-4222-ACB3-C88B606D6623}" src="https://github.com/user-attachments/assets/ecb8af1c-e5c8-40c5-bb6e-709c5c7b69fd" />


---

# 8. Candidate Key näide

```sql
create table opilased(
opilaseID int primary key,
isikukood varchar(20) unique,
email varchar(100) unique
)
```



Candidate Key-d:

* `opilaseID`
* `isikukood`
* `email`

Selgitus:

* Kõik väljad on unikaalsed.
* Neist üks valitakse Primary Key-ks.

Sisestasin andmeid: 
<img width="442" height="152" alt="{59E69E72-F1AD-46F0-805A-8CDA353C3666}" src="https://github.com/user-attachments/assets/6fdb56fb-a167-4441-a75d-4b1472c13069" />

Kontrolli opilaseID järgi:
<img width="333" height="250" alt="{89DD3F68-D000-4721-807D-79224473B48B}" src="https://github.com/user-attachments/assets/1b2214d9-e03d-4b07-87c0-9e1208c4c515" />

Kontrolli isikukood järgi:
<img width="410" height="210" alt="{ACE7E766-6D76-4C26-A258-41AF0D3017D4}" src="https://github.com/user-attachments/assets/7be415ec-6ff5-4e37-9adc-f06f9f8722d0" />

Proovi lisada sama isikukood uuesti:
<img width="1268" height="332" alt="{3E0B5C72-A625-4365-B1D3-BBFA1A058701}" src="https://github.com/user-attachments/assets/f04cca28-482f-4b96-9b92-469a58f2ac6e" />
Annab vea

Samuti proovin sama e-maili:
<img width="1228" height="353" alt="{09FA8CA3-A2E2-452A-AA83-82E69A528C0D}" src="https://github.com/user-attachments/assets/6e38665e-a208-4b90-becf-2ece8348711e" />
Ka see annab vea. 

---


# 9. Alternate Key näide

```sql
create table raamatukogu(
raamatuID int primary key,
isbn varchar(30) unique,
pealkiri varchar(100)
)
```

Selgitus:

* `raamatuID` on Primary Key.
* `isbn` on Alternate Key, sest see on samuti unikaalne, kuid ei ole Primary Key.

Lisasin andmed tabelisse:
<img width="454" height="121" alt="{A1682F64-4F8B-47A0-9EA7-0CE32D4B5835}" src="https://github.com/user-attachments/assets/ed8e8281-ef51-4e91-ab92-26b24c1dba7b" />

Proovin lisada sama ISBN uuesti:

<img width="1209" height="348" alt="{7597E948-3D0D-4028-BE08-7B635281DF12}" src="https://github.com/user-attachments/assets/bc4b16cd-1be6-4047-a5da-2898da274bc5" />



```
```


























# Allikad 

TechTarget – DBMS keys explained
Väga hea ülevaade erinevatest võtmetest: Primary Key, Candidate Key, Superkey, Alternate Key jne.
DataCamp – SQL Foreign Key Tutorial
Selgitab Primary Key ja Foreign Key erinevusi ning sisaldab praktilisi SQL näiteid.
DataCamp – SQL Primary Key Tutorial
Hea allikas Primary Key ja tabelite seoste kohta.
Tutorial Reference – SQL Primary Keys and Foreign Keys
Lihtsas keeles seletatud võtmed ja tabelite vahelised suhted.
Database Star – Database Keys Guide
Sisaldab selgitusi Unique Key, Alternate Key, Composite Key ja teiste võtmete kohta.
SQLNoir – Primary Key vs Foreign Key
Visuaalne ja lihtne võrdlus Primary Key ja Foreign Key vahel.


https://www.techtarget.com/searchdatamanagement/answer/Definition-of-primary-super-foreign-and-candidate-key-in-the-DBMS

https://www.datacamp.com/tutorial/foreign-key

https://www.datacamp.com/tutorial/sql-primary-key

https://tutorialreference.com/sql/joining-tables/sql-primary-keys-and-foreign-keys

https://www.databasestar.com/database-keys/

https://www.sqlnoir.com/blog/primary-key-vs-foreign-key?




