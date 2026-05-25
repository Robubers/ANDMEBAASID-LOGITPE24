## Triger - trigger -päästik
### Triger - andmebaasi objekt, käivtub automaatselt, kui toimub teatud sündmus (nt INSERT, UPDATE, DELETE).
trigerite loomine automatiseerib protsessid SQL serveris 

##Tabelid mis peab looma enne trigerite tegemist 


```sql

CREATE database TRIGERIDLOGITPE24

use TRIGERIDLOGITPE24;

CREATE TABLE linnad(
linnId int primary key identity(1,1),
linnanimi varchar(30) unique,
maakond varchar(30) unique, 
rahvaarv int);

select * from linnad;

insert into linnad(linnanimi, maakond, rahvaarv)
VALUES('Tallinn', 'Harjumaa', 600000);

--tabel logi -tabel, mis täidab triger!!! kui kasutaja tä´idab tabeli linnad 

create table logi(
id int primary key identity(1,1),
kasutaja varchar(50),
aeg DATETIME, 
andmed TEXT);

SELECT * FROM logi 
```


##Trigeri loomine

```sql
CREATE TRIGGER linnalisamine
ON linnad --tabel, mida trigger jälgib
FOR INSERT 
AS
INSERT logi(kasutaja, aeg, andmed)
SELECT 
SYSTEM_USER, --sisselogitud user 
GETDATE(), 
CONCAT ('LISATUD: ',inserted.linnanimi, ', ',
inserted.maakond, ', ', inserted. rahvaarv)
FROM inserted;


--kontrollimiseks tuleb lisada linna tabelisse linnad

insert into linnad(linnanimi, maakond, rahvaarv)
VALUES('Tartu', 'Tartumaa', 200000);

SELECT * FROM linnad;
SELECT * FROM logi;


insert into linnad(linnanimi, maakond, rahvaarv)
VALUES('Viljandi', 'Viljandimaa', 50000);
```

<img width="705" height="594" alt="{76BB8D75-EBA3-4D13-844B-86C073D8E871}" src="https://github.com/user-attachments/assets/fb7761c7-694b-4d2f-9271-18df16c56379" />

```sql
--2. DELETE triger - jälgib kustutamine tabelis linnad
--ja teeb vastava kirje logi tabelisse

CREATE TRIGGER linnakustutamine
ON linnad --tabel, mida trigger jälgib
FOR DELETE 
AS
INSERT logi(kasutaja, aeg, andmed)
SELECT 
SYSTEM_USER, --sisselogitud user 
GETDATE(), 
CONCAT ('KUSTUTATUD: ',deleted.linnanimi, ', ',
deleted.maakond, ', ', deleted. rahvaarv)
FROM deleted;

--kontroll 
DELETE FROM linnad WHERE linnId = 4

SELECT * FROM linnad;
SELECT * FROM logi;
```
<img width="629" height="446" alt="{0E747321-AF21-4F73-AA2D-FA33C25974BB}" src="https://github.com/user-attachments/assets/6037e6c5-6ac1-4b6c-800c-ef7232fb7261" />
