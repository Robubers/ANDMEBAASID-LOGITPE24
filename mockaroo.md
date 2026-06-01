# Teised Konspektid 
[PROTSEDUURID](PROTSEDUURID.md) | [Select_laused](mockaroo.md) | [Kasutajate_loomine SQL server](kasutaja.md) | [Triggerid](Trigerid.md) | [Kodutöö - keys](keys.md) | [Kasutaja loomine XAMPP-is](kasutajaXampp.md) |
[vaaded](vaade.md)

```sql

create database Petrosyan
use Petrosyan;
create table auto(
autonumber char(6) primary key,
mark varchar(30),
mudell varchar(50),
v_aasta int,
varv varchar(50),
hind money)

Select * from auto;

```
--mockaroo.com --kasutame andmete genereerimiseks
<img width="1539" height="498" alt="{4FCFBD70-8C92-4A71-9DB5-68BA10E56E88}" src="https://github.com/user-attachments/assets/4e3cd6cf-4e6a-4726-918f-dfb6ff89dfb3" />

```sql

insert into auto (autonumber, mark, mudell, v_aasta, varv, hind) values ('849SdL', 'Volvo', 'XC60', 2010, 'Blue', '€5338,95');
insert into auto (autonumber, mark, mudell, v_aasta, varv, hind) values ('659dhc', 'Lotus', 'Exige', 2008, 'Blue', '€4729,56');
insert into auto (autonumber, mark, mudell, v_aasta, varv, hind) values ('584NMm', 'BMW', 'M5', 1993, 'Orange', '€3810,23');
insert into auto (autonumber, mark, mudell, v_aasta, varv, hind) values ('227eE4', 'Buick', 'Coachbuilder', 1993, 'Puce', '€1844,32');
insert into auto (autonumber, mark, mudell, v_aasta, varv, hind) values ('427iDY', 'Jeep', 'Grand Cherokee', 2004, 'Yellow', '€8666,69');
insert into auto (autonumber, mark, mudell, v_aasta, varv, hind) values ('197CCh', 'Dodge', 'Stratus', 1999, 'Maroon', '€3167,27');
insert into auto (autonumber, mark, mudell, v_aasta, varv, hind) values ('3025wl', 'Dodge', 'Ram Van B350', 1993, 'Puce', '€90,81');
insert into auto (autonumber, mark, mudell, v_aasta, varv, hind) values ('317AOZ', 'Infiniti', 'G25', 2012, 'Puce', '€5809,67');
insert into auto (autonumber, mark, mudell, v_aasta, varv, hind) values ('192mVB', 'Plymouth', 'Voyager', 1995, 'Maroon', '€1421,96');
insert into auto (autonumber, mark, mudell, v_aasta, varv, hind) values ('250HzK', 'Chevrolet', 'Express 1500', 2010, 'Fuscia', '€3878,24');
insert into auto (autonumber, mark, mudell, v_aasta, varv, hind) values ('92288T', 'Mitsubishi', 'Galant', 1998, 'Pink', '€9102,09');
insert into auto (autonumber, mark, mudell, v_aasta, varv, hind) values ('002xF5', 'Chevrolet', 'HHR Panel', 2006, 'Aquamarine', '€9088,92');
insert into auto (autonumber, mark, mudell, v_aasta, varv, hind) values ('438ywk', 'Audi', 'S6', 2007, 'Fuscia', '€9098,92');
insert into auto (autonumber, mark, mudell, v_aasta, varv, hind) values ('454zKA', 'Chevrolet', 'Bel Air', 1967, 'Violet', '€9394,36');
insert into auto (autonumber, mark, mudell, v_aasta, varv, hind) values ('847cZg', 'Chrysler', 'Town & Country', 2010, 'Yellow', '€214,46');
insert into auto (autonumber, mark, mudell, v_aasta, varv, hind) values ('740cOZ', 'GMC', 'Vandura G3500', 1996, 'Pink', '€986,86');
insert into auto (autonumber, mark, mudell, v_aasta, varv, hind) values ('716jV9', 'Toyota', 'Tundra', 2000, 'Pink', '€4155,10');
insert into auto (autonumber, mark, mudell, v_aasta, varv, hind) values ('921yPx', 'Pontiac', 'GTO', 1964, 'Puce', '€7016,46');
insert into auto (autonumber, mark, mudell, v_aasta, varv, hind) values ('384VzD', 'Pontiac', 'Grand Prix', 1996, 'Violet', '€8222,55');
insert into auto (autonumber, mark, mudell, v_aasta, varv, hind) values ('715fkT', 'Chevrolet', 'Express', 2006, 'Pink', '€7434,21');
insert into auto (autonumber, mark, mudell, v_aasta, varv, hind) values ('136oQ8', 'Toyota', 'Solara', 2002, 'Crimson', '€7188,46');
insert into auto (autonumber, mark, mudell, v_aasta, varv, hind) values ('443wEP', 'Mitsubishi', 'Outlander', 2006, 'Orange', '€6810,36');
insert into auto (autonumber, mark, mudell, v_aasta, varv, hind) values ('021XF0', 'Lexus', 'IS F', 2009, 'Blue', '€3482,22');
insert into auto (autonumber, mark, mudell, v_aasta, varv, hind) values ('713NQs', 'Volkswagen', 'CC', 2013, 'Orange', '€4765,69');
insert into auto (autonumber, mark, mudell, v_aasta, varv, hind) values ('766a35', 'Audi', 'A8', 2005, 'Turquoise', '€5776,53');
insert into auto (autonumber, mark, mudell, v_aasta, varv, hind) values ('697TUs', 'Honda', 'CR-V', 2008, 'Pink', '€4575,76');
insert into auto (autonumber, mark, mudell, v_aasta, varv, hind) values ('774oGT', 'Toyota', 'Avalon', 1998, 'Puce', '€60,95');
insert into auto (autonumber, mark, mudell, v_aasta, varv, hind) values ('505Jnp', 'Pontiac', 'Sunfire', 2005, 'Blue', '€4061,31');
insert into auto (autonumber, mark, mudell, v_aasta, varv, hind) values ('612Apa', 'Volkswagen', 'Cabriolet', 1999, 'Puce', '€5201,17');
insert into auto (autonumber, mark, mudell, v_aasta, varv, hind) values ('899rKB', 'Dodge', 'Durango', 2005, 'Fuscia', '€1728,02');
insert into auto (autonumber, mark, mudell, v_aasta, varv, hind) values ('924dUc', 'Bentley', 'Continental GTC', 2011, 'Aquamarine', '€8876,48');
insert into auto (autonumber, mark, mudell, v_aasta, varv, hind) values ('888h1R', 'Mitsubishi', 'GTO', 1997, 'Crimson', '€9437,00');
insert into auto (autonumber, mark, mudell, v_aasta, varv, hind) values ('875FSS', 'Ford', 'Contour', 1998, 'Puce', '€1275,87');
insert into auto (autonumber, mark, mudell, v_aasta, varv, hind) values ('932ofw', 'Lexus', 'GX', 2008, 'Crimson', '€3993,88');
insert into auto (autonumber, mark, mudell, v_aasta, varv, hind) values ('574HrG', 'BMW', 'M', 2000, 'Purple', '€2978,01');
insert into auto (autonumber, mark, mudell, v_aasta, varv, hind) values ('717V81', 'Mercury', 'Mountaineer', 1997, 'Pink', '€2585,13');
insert into auto (autonumber, mark, mudell, v_aasta, varv, hind) values ('412Eug', 'Toyota', 'Highlander Hybrid', 2007, 'Aquamarine', '€4381,39');
insert into auto (autonumber, mark, mudell, v_aasta, varv, hind) values ('716mu1', 'Chevrolet', 'Tahoe', 1999, 'Aquamarine', '€1494,98');
insert into auto (autonumber, mark, mudell, v_aasta, varv, hind) values ('6085bM', 'Toyota', 'FJ Cruiser', 2009, 'Orange', '€3501,50');
insert into auto (autonumber, mark, mudell, v_aasta, varv, hind) values ('086LR9', 'Jaguar', 'X-Type', 2003, 'Teal', '€9965,15');
insert into auto (autonumber, mark, mudell, v_aasta, varv, hind) values ('946z2g', 'Scion', 'xA', 2005, 'Maroon', '€3725,59');
insert into auto (autonumber, mark, mudell, v_aasta, varv, hind) values ('819dOI', 'Maserati', 'Spyder', 1989, 'Teal', '€6408,81');
insert into auto (autonumber, mark, mudell, v_aasta, varv, hind) values ('090rhN', 'Lexus', 'HS', 2011, 'Maroon', '€1941,27');
insert into auto (autonumber, mark, mudell, v_aasta, varv, hind) values ('584K6N', 'Subaru', 'Forester', 2012, 'Pink', '€2976,35');
insert into auto (autonumber, mark, mudell, v_aasta, varv, hind) values ('192n2O', 'Toyota', 'Avalon', 2006, 'Blue', '€6899,17');
insert into auto (autonumber, mark, mudell, v_aasta, varv, hind) values ('423SZu', 'Holden', 'VS Commodore', 1996, 'Purple', '€3016,67');
insert into auto (autonumber, mark, mudell, v_aasta, varv, hind) values ('175HNv', 'Spyker', 'C8 Spyder Wide Body', 2004, 'Puce', '€5099,82');
insert into auto (autonumber, mark, mudell, v_aasta, varv, hind) values ('1225GU', 'Cadillac', 'Seville', 1992, 'Puce', '€328,46');
insert into auto (autonumber, mark, mudell, v_aasta, varv, hind) values ('041afa', 'Chevrolet', 'Colorado', 2004, 'Pink', '€5465,62');
insert into auto (autonumber, mark, mudell, v_aasta, varv, hind) values ('512Aak', 'Mercury', 'Sable', 2005, 'Turquoise', '€4143,32');
```

```sql
Select * from auto;

Select mark, mudell, hind from auto;
--tingimused 
--sorteerimine
--sorteerimine  -ORDER by -kasvavalt,  DESC - kahanevalt
Select mark, mudell, hind
from auto 
ORDER by hind;
ORDER hind by DESC;
```
<img width="598" height="569" alt="{1D68506B-7802-40E5-89D4-43E7C7884CDC}" src="https://github.com/user-attachments/assets/db32fb45-55bd-4def-ba72-36801d8915d8" />

```sql
Select mark  FROM auto 
WHERE mark LIKE 'C%';
```

```sql
--hind on vahemikus 500 kuni 1000 euro 
Select mark, autonumber, hind
From auto 
Where hind > 150000 AND hind < 300000;

--kombineeritud tingimused (AND, OR, NOT)

Select mark, autonumber, hind
FROM  auto 
Where mark LIKE 'Pontiac' OR hind <=100000

--vaade loomine - VIEW
CREATE VIEW pontiacAutod
AS
Select mark, autonumber, hind
FROM  auto 
Where mark LIKE 'Pontiac';


--view kasutamine
Select * from pontiacAutod;


--AgreegaatFunktsioon - SUM, MAX, MIN, AVG, COUNT- kogus 

--Leia mitu autod on tabelis 
SELECT COUNT(*) AS autodeArv FROM auto;

--leia keskmine autohind
SELECT mark, AVG(hind) AS 'autoKeskmineHind' FROM auto;

--leia keskmine autohind iga margi kohta
SELECT mark, AVG(hind) AS 'autoKeskmineHind'
FROM auto
GROUP by mark;
```
