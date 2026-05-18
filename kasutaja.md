create database kasutajaBaas
use kasutajaBaas


create table test( id int)

--grant - õiguste määramine
--deny - õiguste keelamine

--db_datareader -SELECT
--db_datawriter - INSERT, DELETE, UPDATE

--anname kasutajale directorIrina õigus 
--ainult kustutada ja uuendada tabelit 
--(DELETE, UPDATE, SELECT)

grant delete on puhkus to directorIrina;
grant update on puhkus to directorIrina;
grant select on puhkus to directorIrina;

--keelame insert
deny insert on puhkus to directorIrina;
