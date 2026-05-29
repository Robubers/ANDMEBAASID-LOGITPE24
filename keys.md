## Andmebaasi võtmed (keys)

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

### Näide

Tabel: **Õpilased**

| ÕpilaseID | Nimi          | Klass |
| --------- | ------------- | ----- |
| 1         | Mari Maasikas | 10A   |
| 2         | Jaan Tamm     | 10B   |

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

### Näide

Tabel: **Tellimused**

| TellimusID | ÕpilaseID | Toode      |
| ---------- | --------- | ---------- |
| 101        | 1         | Sülearvuti |
| 102        | 2         | Hiir       |
| 103        | 1         | Klaviatuur |

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

### Näide

Tabel: **Kasutajad**

| KasutajaID | Email                                   |
| ---------- | --------------------------------------- |
| 1          | [mari@email.com](mailto:mari@email.com) |
| 2          | [jaan@email.com](mailto:jaan@email.com) |

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

### Näide

Tabel: **Raamatud**

| ISBN     | Pealkiri         |
| -------- | ---------------- |
| 97812345 | Andmebaasid      |
| 97867890 | Programmeerimine |

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

### Näide

Tabel: **ÕpilaseKursused**

| ÕpilaseID | KursuseID | Hinne |
| --------- | --------- | ----- |
| 1         | MAT101    | 5     |
| 1         | ENG202    | 4     |

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

### Näide

Tabel: **TellimusTooted**

| TellimusID | TooteID | Kogus |
| ---------- | ------- | ----- |
| 1001       | 501     | 2     |
| 1001       | 502     | 1     |

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

### Näide

Tabel: **Töötajad**

| TöötajaID | Isikukood   | Nimi |
| --------- | ----------- | ---- |
| 1         | 39801010011 | Mari |

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

### Näide

Tabel: **Töötajad**

| TöötajaID | Isikukood   | Nimi |
| --------- | ----------- | ---- |
| 1         | 39801010011 | Mari |

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

### Näide

Tabel: **Töötajad**

| TöötajaID | Isikukood   | Email                                   |
| --------- | ----------- | --------------------------------------- |
| 1         | 39801010011 | [mari@email.com](mailto:mari@email.com) |

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




