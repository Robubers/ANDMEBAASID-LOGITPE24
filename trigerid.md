## Triger - trigger -päästik
### Triger - andmebaasi objekt, käivtub automaatselt, kui toimub teatud sündmus (nt INSERT, UPDATE, DELETE).
trigerite loomine automatiseerib protsessid SQL serveris 

##Tablid mis peab looma enne trtigerite tegemist 


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


