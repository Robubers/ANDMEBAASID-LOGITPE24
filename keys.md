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



<img width="373" height="369" alt="{E2507410-97EE-4BDB-8989-3061E2EBB0C4}" src="https://github.com/user-attachments/assets/5c4ba23a-0413-45bf-8028-61dfce0deb28" />

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


https://www.techtarget.com/searchdatamanagement/answer/Definition-of-primary-super-foreign-and-candidate-key-in-the-DBMS?utm_source=chatgpt.com 

https://www.datacamp.com/tutorial/foreign-key?utm_source=chatgpt.com

https://www.datacamp.com/tutorial/sql-primary-key?utm_source=chatgpt.com 

https://tutorialreference.com/sql/joining-tables/sql-primary-keys-and-foreign-keys?utm_source=chatgpt.com 

https://www.databasestar.com/database-keys/?utm_source=chatgpt.com 

https://www.sqlnoir.com/blog/primary-key-vs-foreign-key?utm_source=chatgpt.com 




