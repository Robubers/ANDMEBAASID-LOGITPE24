# PORTFOOLIO

[Select_laused](mockaroo.md) | [Kasutajate_loomine SQL server](kasutaja.md) | [Triggerid](Trigerid.md) | [Kodutöö - keys](keys.md)


# Andmebaaside Õpetaja portfoolio ||| LOGITpe24

Andmebaasidega seotud sql kood ja konspektid

[Kasutaja.XAMPP-is](kasutajaXampp.md) | [Select laused](select.md) | [Kasutaja loomine XAMPP-is](kasutajaXampp.md) | [Kasutaja loomine SQL Server](kasutaja.md) | [Triggerid](trigerid.md) | [Kodutöö - Keys](keys.md)


- SQL - structured Query Language - struktureeritud päringukeel
- DDL - Data Definition Language -andmebaasi struktuuri loomiseks - CREATE, ALTER
- DML - Data Manipulation Language -andmete lisamine ja uuendamine tabelis - INSERT, UPDATE, DELETE
  
## Sisukord
  - [Andmebaasihaldusüsteemid](#andmebaasihaldusüsteemid)
  - [Põhimõisted](#põhimõisted)
  - [Andmetüübid](#andmetüübid)
  - [Piirangud](#piirangud)
  - [Tabelivahelised Seosed](#tabelivahelised-seosed)

## Andmebaasihaldusüsteemid
1. SQL Server Management Stuudio (SQL Serveri haldamiseks)
   <img width="472" height="502" alt="{81ABDF60-8DD9-458A-B7D2-DCEB363321E1}" src="https://github.com/user-attachments/assets/fb13b99d-4abb-4280-9fdf-af8ffdacec1a" />

2. XAMPP -phpmyAdmin (mariaDB andmebaas) -vabavara

   ## Põhimõisted

- Andmebaas - struktueeritud andmete kogum
- Tabel - olem (entity)
- veerg - väli (field)
- rida - kirje (record)
- primaarne võti -PK- Primary Key - veerg (tavaliselt nimega id) unikaalse identifikaatooriga, mis eristab iga kirjet
- Välisvõti (võõrvõti) -FK Foreign Key - veerg, mis loob seose teise tabeli primaarvõtmega.

  ## Andmetüübid
  - INT, float, decimal(6,2) - numbrilised
  - varchar(50), char(6) -tekst/sümboolid
  - boolean, bool, bit -loogiline tüüp
  - date, time, datetime - kuupäeva
 
## Piirangud
```
1. Primary Key
2. Foreign Key
3. Unique
4. Not Null
5. Check
```
## Tabelivahelised Seosed
- üks  - ühele (nt mees --naine)
- üks - mitmele (õpilane käib erinevates õppeainetes)
  <img width="350" height="150" alt="{979F53E1-7365-40EE-BC26-CBFE1A45E637}" src="https://github.com/user-attachments/assets/33209fb4-d37e-4f77-82c5-e57f0c427d89" />

- mitu - mitmele (nt õpilane - õpetaja)

## Stored procedure
  Salvestatud protseduurid - sama mis on funktsioonid programeerimises - mingi tegevus(ed), mida saab automaatselt teha (INSERT, SELECT, UPDATE, DELETE)
```sql
CREATE PROCEDURE lisaKategooria
@nimi varchar(15)
AS
BEGIN
	INSERT INTO categories
	VALUES (@nimi);
	SELECT * FROM categories;
END
--kutse
EXEC lisaKategooria 'test';
```
<img width="500" height="250" alt="{846C3414-D27D-4B9A-B7E3-0729D595E74A}" src="https://github.com/user-attachments/assets/bfac6683-0b82-4402-8ad6-25f53f55b62a" />
