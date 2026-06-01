## Vaade (inglise keeles view) on SQL-is sisuliselt „virtuaalne tabel“. Erinevalt tavalisest andmebaasi tabelist ei hoia vaade endas füüsilisi andmeid. Selle asemel sisaldab see salvestatud SQL-päringut (SELECT), mis käivitatakse dünaamiliselt iga kord, kui sa vaadet pärited.
Võid mõelda vaatest kui salvestatud aknast või filtrist, mille kaudu sa olemasolevaid andmeid vaatad.

## Kuidas vaade töötab?
Kui lood vaate, salvestab andmebaas ainult selle definitsiooni (päringu koodi). Kui teed päringu vaate vastu, siis andmebaasimootor kombineerib sinu päringu vaate algse päringuga ja küsib andmed otse alustabelitest (base tables).

## Lihtne näide
Kujutame ette, et sul on tabel tootajad, kus on kirjas töötajate nimed, osakonnad ja palgad. Turvakaalutlustel ei taha sa, et kõik näeksid palganumbreid.

1. Vaate loomine:

```sql
