create database robertKT
use robertKT



--TABELID
create table Lennujaam (
Lennujaam_id int primary key identity(1,1),
Lennujaamanimi varchar(30),
Linn varchar(30)
)


create table lend4(
lend_id int primary key identity (1,1),
Lennunumber int,
Väljumisaeg time,
Lennujaam_id int,
foreign key (Lennujaam_id) references Lennujaam(Lennujaam_id)
)


create table Reisija4(
reisija_id int primary key identity(1,1),
Nimi varchar(20),
Piletinumber int,
lend_id int,
foreign key (lend_id) references lend2(lend_id)
)



select * from Lennujaam

select * from lend4

select * from Reisija4 




insert into Lennujaam(Lennujaam_id, Lennujaamanimi, Linn)
values('Tallinn Airport', 'Tallinn')

insert into Lennujaam(Lennujaamanimi, Linn)
values('JFK international Airport', 'New York')

insert into Lennujaam(Lennujaamanimi, Linn)
values('Singapore Changi Airport', 'Singapore')


insert into lend4(Lennunumber, Väljumisaeg, Lennujaam_id)
values(123456, '10:15:00', 1); 

insert into lend4(Lennunumber, Väljumisaeg, Lennujaam_id)
values(654321, '19:30:00', 2); 

insert into lend4(Lennunumber, Väljumisaeg, Lennujaam_id)
values(190657, '17:00:00', 3); 




insert into Reisija4(Nimi, Piletinumber, lend_id)
values('Robert', 200890, 1); 

insert into Reisija4(Nimi, Piletinumber, lend_id)
values('Kristo', 370260, 2); 

insert into Reisija4(Nimi, Piletinumber, lend_id)
values('Nicolas', 650740, 1); 



select * from Lennujaam

select * from lend4

select * from Reisija4



------------------------------------------------------------------



--KASUTAJAÕIGUSED



GRANT CREATE TABLE TO reisijaRobert;
GRANT SELECT TO reisijaRobert;
GRANT INSERT, DELETE ON Reisija4 TO reisijaRobert;
GRANT INSERT, DELETE ON lend4 TO reisijaRobert;
GRANT SELECT ON logi2 TO ReisijaRobert;
DENY ALTER ON SCHEMA::dbo TO reisijaRobert;
DENY INSERT, DELETE ON Reisija4 TO reisijaRobert;




-------------------------------------------------------------------

--LOGI TABEL

create table logi2(
id int primary key identity(1,1),
kasutaja varchar(50),
kuupäev DATETIME, 
sisestatudandmed TEXT);

SELECT * FROM logi2 

------------------------------------------------------------------


SELECT * FROM lend4;
SELECT * FROM logi2;



--INSERT TRIGER 

CREATE TRIGGER lendInsert3
ON lend4
FOR INSERT 
AS
INSERT logi2(kasutaja, kuupäev, sisestatudAndmed)
SELECT 
SYSTEM_USER,
GETDATE(), 
CONCAT ('LISATUD: ',inserted.Lennunumber, ', ',
inserted.Väljumisaeg)
FROM inserted;



insert into lend4(Lennunumber, Väljumisaeg)
values(898711, '11:15:00')


SELECT * FROM lend4;
SELECT * FROM logi2;


--delete triger
CREATE TRIGGER lendkustutamine6
ON lend4
FOR DELETE 
AS
INSERT logi2(kasutaja, kuupäev, sisestatudAndmed)
SELECT 
SYSTEM_USER, --sisselogitud user 
GETDATE(), 
CONCAT ('KUSTUTATUD: ', 'Lennunumber ', deleted.Lennunumber, ' Väljumisaeg ',
deleted.Väljumisaeg)
FROM deleted;


DELETE FROM lend4 WHERE lend_Id = 1




SELECT * FROM lend4;
SELECT * FROM logi2;


------------------------------------------------------------------


--PROTSEDUURID



--1) DELETE PROTSEDUUR
Create procedure kustutaIdJargi2
@id int
AS
BEGIN
    SELECT * FROM lend4;
    DELETE FROM lend4 WHERE lend_id=@id;
	SELECT * FROM lend4;
END
--kutse
EXEC kustutaIdjargi 4;




--2) SEARCH PROTSEDUUR
CREATE PROCEDURE otsing1taht4
@taht char(1)
AS
BEGIN
    SELECT Lennujaamanimi, Linn FROM Lennujaam
	WHERE Lennujaamanimi LIKE @taht + '%'
END 

--kutse

SELECT * FROM Lennujaam
EXEC otsing1taht4 'T'



--3) UPDATE PROTSEDUUR BY ID 
CREATE PROCEDURE uuendaReisijaNimi2 
@id int,
@uuendatudNimi varchar(20)
AS 
BEGIN
    SELECT * FROM Reisija4;
    UPDATE Reisija4 SET Nimi=@uuendatudNimi 
	WHERE Reisija_id=@id;
	SELECT * FROM Reisija4;
END

--kutse 

EXEC uuendaReisijaNimi 2, 'Karel'






------------------------------------------------------------------




--VAADET 

--Lennujaamade vaade
CREATE VIEW vw_Lennujaamad
AS
SELECT Lennujaamanimi, Linn
FROM Lennujaam;

SELECT * FROM vw_Lennujaamad; 


--Lendude vaade
CREATE VIEW vw_Lennud2     
AS
SELECT Lennunumber, Väljumisaeg    
FROM lend4;     

SELECT * FROM vw_Lennud2; 

--Reisijate vaade
CREATE VIEW vw_Reisijad2     
AS
SELECT Nimi, Piletinumber   
FROM Reisija4;   

SELECT * FROM vw_Reisijad2; 
















-------------------------------------------------------------------------------------



--LISA TEGEVUS, FOREIGN KEY TABEL
--SELLES TABELIS ON PANDUD KÕIK FOREIGN KEY MIS ÜLDSE EKSISTEERUVAD, SELLE PEAMINE MÕTTE 
--ON LIHTSALT NÄIDATA KÕIK FOREIGN KEYD, ET KUI MIDAGI SIIS SA TEAD MIS FOREIGN KEYD 
--SUL ON LOODUD 


create table allFK1 (
allfk_id int primary key identity(1,1),
FK_Lennujaam varchar(20),
FK_Lend1 varchar(20),
FK_Reisija1 varchar(20),
Lennujaam_id int,
foreign key (Lennujaam_id) references Lennujaam(Lennujaam_id),
lend_id int,
foreign key (lend_id) references lend2(lend_id),
Reisija_id int,
foreign key (Reisija_id) references Reisija3(Reisija_id)
)


insert into allFk1(FK_Lennujaam, FK_Lend1, FK_Reisija1)
values('ForeignKeyLennujaam:', 'Foreign Key Lend1', 'Foreign Key Reisija1')


select * from allFK1

















