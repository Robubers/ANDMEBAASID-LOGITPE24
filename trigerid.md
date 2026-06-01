# Teised Konspektid
[PROTSEDUURID](PROTSEDUURID.md) | [Select_laused](mockaroo.md) | [Kasutajate_loomine SQL server](kasutaja.md) | [triggerid](trigerid.md) | [Kodutöö - keys](keys.md) | [Kasutaja loomine XAMPP-is](kasutajaXampp.md) |
[vaaded](vaade.md)


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


```sql
--3.UPDATE trigger -jälgib ueendused/muutused tabelis linnad
--ja teeb vastava kirje tabelis logi

CREATE TRIGGER linnauuendamine
ON linnad --tabel, mida trigger jälgib
FOR UPDATE
AS
INSERT logi(kasutaja, aeg, andmed)
SELECT 
SYSTEM_USER, --sisselogitud user 
GETDATE(), 
CONCAT ('VANAD ANDMED : ',
deleted.linnanimi,', ', deleted.maakond,', ', deleted. rahvaarv, 
' ||| uued andmed: ',
inserted.linnanimi,', ', inserted.maakond,', ', inserted. rahvaarv)
FROM deleted INNER JOIN inserted
ON deleted.linnId=inserted.linnId;

--kontroll
UPDATE linnad SET linnanimi='Tallinn22', rahvaarv=700000
Where linnId=1;
```
<img width="631" height="434" alt="{32235D6A-0224-4FB6-80A0-A586721EC013}" src="https://github.com/user-attachments/assets/8a89d677-98e1-402a-8839-d8a178a43199" />


```sql

--triger sisse või välja lülitamine 
DISABLE TRIGGER linnalisamine ON linnad;
DISABLE TRIGGER linnakustutamine ON linnad;
ENABLE TRIGGER linnauuendamine ON linnad;


--ühine trigger mis jälgib kas lisamine või kustutamine tabelisse linnad



CREATE TRIGGER linnalisaminekustutamine
ON linnad --tabel, mida trigger jälgib
FOR INSERT 
AS
BEGIN
SET NOCOUNT ON;
	INSERT logi(kasutaja, aeg, andmed)
	SELECT 
	SYSTEM_USER, --sisselogitud user 
	GETDATE(), 
	CONCAT ('LISATUD: ',inserted.linnanimi, ', ',
	inserted.maakond, ', ', inserted. rahvaarv)
	FROM inserted

	UNION ALL

	SELECT 
	SYSTEM_USER, --sisselogitud user 
	GETDATE(), 
	CONCAT ('kustutatud: ',deleted.linnanimi, ', ',
	deleted.maakond, ', ', deleted. rahvaarv)
	FROM deleted;
END;

SELECT * FROM linnad;
SELECT * FROM logi; 


DELETE FROM linnad WHERE linnId = 5


insert into linnad(linnanimi, maakond, rahvaarv)
VALUES('Viljandi', 'Viljandimaa', 50000);
```

<img width="738" height="641" alt="{106584FD-025D-4F06-A7DF-EFC3FF330C84}" src="https://github.com/user-attachments/assets/c48ba888-9412-42cd-8f0a-2bb1dcb3d8fc" />


# XAMPP

<img width="579" height="603" alt="{4B9C4CD3-8F78-4E7F-A2F2-C4E1FBA06EF8}" src="https://github.com/user-attachments/assets/5ac17aed-e645-45e8-9ca9-230043dcce1b" />

<img width="595" height="279" alt="{F89AEB92-6E2F-465C-9CCF-4BFF78E8DF73}" src="https://github.com/user-attachments/assets/2c8f5f59-a8c9-48b8-8074-d95827f3c749" />

<img width="567" height="604" alt="{746B7971-791D-4188-A1DA-5512134A1F9B}" src="https://github.com/user-attachments/assets/58096863-da17-428d-b4df-c30fd418d808" />

<img width="608" height="259" alt="{12940AA0-A75B-4431-92FF-0F5FBFCBF121}" src="https://github.com/user-attachments/assets/f874c23a-3d1f-4b4d-9d4b-3127ea222016" />

<img width="602" height="187" alt="{CD0CFD3F-520E-4A16-93DA-2B50D4370B6C}" src="https://github.com/user-attachments/assets/7fdff14d-294c-4e9b-a9c2-d3cd1b8143c8" />

<img width="558" height="568" alt="{F94BDF66-DE5D-43D7-9FB3-4C83E7AD0941}" src="https://github.com/user-attachments/assets/d919a5ce-9989-4fb2-af4d-8e5a7ad28719" />

<img width="599" height="255" alt="{6D9BC435-EBDE-4795-B767-1D1540B42A7F}" src="https://github.com/user-attachments/assets/d4c28b2b-85e6-4bb9-ba8d-58440857c196" />

<img width="620" height="306" alt="{453F59F9-1822-42E8-A7EA-D431B5B84D1C}" src="https://github.com/user-attachments/assets/a16a5572-002a-4883-b09f-2291524cbf34" />

<img width="573" height="605" alt="{240AD045-46DB-4472-BF6A-330B526C0BAE}" src="https://github.com/user-attachments/assets/cf4633f1-6ca5-483c-834e-9fa56197c380" />

<img width="610" height="231" alt="{576E0986-1579-4B68-B3D3-8411DCB5E5C3}" src="https://github.com/user-attachments/assets/dfecc5a6-5349-40fb-935d-f4aa0769e04d" />

<img width="610" height="432" alt="{2C1027BC-9988-488F-9EBB-FDB423C94DA6}" src="https://github.com/user-attachments/assets/f5b637d1-9b2f-4299-8f93-55ba8ee42ceb" />

<img width="602" height="639" alt="{11A2B5B4-FE0F-4E42-A5AB-87AB5D529E64}" src="https://github.com/user-attachments/assets/3021e143-27ba-432c-a8a0-b8d85f86b53e" />

<img width="589" height="327" alt="{B5275750-C2F7-448D-8EF4-7D837A6F5087}" src="https://github.com/user-attachments/assets/1a86a26d-01b2-46ad-962d-c6b489c32079" />
