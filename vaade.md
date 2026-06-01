## Vaade (inglise keeles view) on SQL-is sisuliselt „virtuaalne tabel“. Erinevalt tavalisest andmebaasi tabelist ei hoia vaade endas füüsilisi andmeid. Selle asemel sisaldab see salvestatud SQL-päringut (SELECT), mis käivitatakse dünaamiliselt iga kord, kui sa vaadet pärited.
Võid mõelda vaatest kui salvestatud aknast või filtrist, mille kaudu sa olemasolevaid andmeid vaatad.

## Kuidas vaade töötab?
Kui lood vaate, salvestab andmebaas ainult selle definitsiooni (päringu koodi). Kui teed päringu vaate vastu, siis andmebaasimootor kombineerib sinu päringu vaate algse päringuga ja küsib andmed otse alustabelitest (base tables).

## Lihtne näide
Kujutame ette, et sul on tabel tootajad, kus on kirjas töötajate nimed, osakonnad ja palgad. Turvakaalutlustel ei taha sa, et kõik näeksid palganumbreid.

1. Vaate loomine:

```sql
CREATE VIEW avalik_tootajad AS
SELECT id, eesnimi, perekonnanimi, osakond
FROM tootajad;
```

2. Vaate kasutamine:
Nüüd saavad kasutajad teha päringuid otse vaatest, nagu see oleks tavaline tabel:

```sql
SELECT * FROM avalik_tootajad WHERE osakond = 'Turundus';
```
Andmebaas tagastab turundusosakonna töötajad, kuid palgajoonis jääb täiesti varjatuks.


## Miks vaateid kasutatakse? (Peamised eelised)
Turvalisus (Andmete piiramine): Saad lubada kasutajatele ligipääsu vaatele, mitte otse algtabelitele. Nii näevad nad ainult neid veerge või ridu, mida nad tohivad näha (nagu eelnevas palga näites).

Keerukuse varjamine (Lihtsustamine): Kui sul on hiiglaslik päring, mis liidab kokku 5 erinevat tabelit (JOIN), saad selle salvestada vaatena. Edaspidi piisab vaid käsust SELECT * FROM minu_vaade.

Andmete konsistentsus: Kui äriloogika muutub (näiteks kuidas arvutatakse "aktiivse kliendi" staatust), muudad sa koodi ainult ühes kohas — vaate definitsioonis. Kõik rakendused ja raportid, mis seda vaadet kasutavad, töötavad automaatselt õigesti edasi.

Ruumi kokkuhoid: Kuna vaade ei kopeeri andmeid, ei võta see andmebaasis peaaegu üldse kettaruumi.


<img width="790" height="430" alt="{B1EEACD6-6DBD-4B1B-AB2E-50F4E94B52CD}" src="https://github.com/user-attachments/assets/524b59d7-2d5a-4e23-8b98-1e9923a3c6cc" />


## Lihtne näide:

```sql
CREATE TABLE tellimused (
    id INT PRIMARY KEY,
    kliendi_nimi VARCHAR(50),
    toode VARCHAR(50),
    summa DECIMAL(10, 2),
    krediitkaardi_nr VARCHAR(19) 
);

INSERT INTO tellimused VALUES (1, 'Mari Maasikas', 'Sülearvuti', 1200.00, '1234-5678-9012-3456');
INSERT INTO tellimused VALUES (2, 'Jüri Juurikas', 'Kõrvaklapid', 150.00, '9876-5432-1098-7654');
```

```sql
CREATE VIEW turvaline_myygi_raport AS
SELECT id, kliendi_nimi, toode, summa
FROM tellimused; -- Me meelega EI VALI siia krediitkaardi_nr veergu! 
```

Tulemus ekraanil näeb välja selline:
<img width="423" height="217" alt="{C81ED832-8460-49E4-B468-4E32A61DD453}" src="https://github.com/user-attachments/assets/07d3ad5e-7ee2-41ec-b707-f5e648ab4c8d" />
Märka, et krediitkaardi veergu pole olemaski! 


<img width="842" height="488" alt="{009460BD-E99A-4E79-8E7A-F59BBDDC1253}" src="https://github.com/user-attachments/assets/bd8e5681-b83e-480f-9c17-c1f8621bf0fe" />

