# TEISED KONSPEKTID
[PROTSEDUURID](PROTSEDUURID.md) | [Select_laused](mockaroo.md) | [Kasutajate_loomine SQL server](kasutaja.md) | [Triggerid](trigerid.md) | [Kodutöö - keys](keys.md) | [Kasutaja loomine XAMPP-is](kasutajaXampp.md) |
[vaaded](vaade.md)




```sql
select * from categories
--proceduur, mis täidab tabeli
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

# protseduur mis kustutab tabelist id järgi 

```sql
Create procedure kustutaIdJargi
@id int
AS
BEGIN
    SELECT * FROM categories;
    DELETE FROM categories WHERE category_id=@id;
	SELECT * FROM categories;
END
--kutse
EXEC kustutaIdjargi 6;
```

--otsing 
--protseduur mis otsib kõik kategooriad sisestatud 1 tähte 

```sql
CREATE PROCEDURE otsing1taht
@taht char(1)
AS
BEGIN
    SELECT category_name FROM categories 
	WHERE category_name LIKE @taht + '%'
END

--kutse

SELECT * FROM categories
EXEC otsing1taht 'r'

```


# proceduur, mis uuendab nimed sisestatud id järgi

```sql
CREATE PROCEDURE uuendaKategooria 
@id int,
@uuendatudNimi varchar(20)
AS 
BEGIN
    SELECT * FROM categories;
    UPDATE categories SET category_name=@uuendatudNimi 
	WHERE category_id=@id;
	SELECT * FROM categories;
END

--kutse 

EXEC uuendaKategooria 8, 'jope'

```

---

### PROTSEDUURID NR.2


# Protseduur andmete lisamiseks 

```sql
CREATE PROCEDURE lisaToode
    @nimetus varchar(20),
    @tootja varchar(20),
    @kogus int,
    @hind money
AS
BEGIN
    INSERT INTO toode(toodeNimi, tootja, toodeHind, toodeKogus)
    VALUES (@nimetus, @tootja, @hind, @kogus);

    SELECT * FROM toode;
END;
```

# OUTPUT parameetrid (min ja max väärtus)

```sql
CREATE PROCEDURE minmaxHind
    @minHind MONEY OUTPUT,
    @maxHind MONEY OUTPUT
AS
BEGIN
    SELECT 
        @minHind = MIN(toodeHind),
        @maxHind = MAX(toodeHind)
    FROM toode;
END;
```

# Dünaamiline SQL protseduuris (ALTER TABLE)
# Protseduur veeru lisamiseks või kustutamiseks 

```sql
CREATE PROCEDURE muudatus
    @tegevus varchar(10),
    @tabelinimi varchar(25),
    @veerunimi varchar(25),
    @tyyp varchar(25) = NULL
AS
BEGIN
    DECLARE @sqltegevus varchar(max);

    SET @sqltegevus = CASE 
        WHEN @tegevus = 'add' THEN 
            CONCAT('ALTER TABLE ', @tabelinimi, ' ADD ', @veerunimi, ' ', @tyyp)

        WHEN @tegevus = 'drop' THEN 
            CONCAT('ALTER TABLE ', @tabelinimi, ' DROP COLUMN ', @veerunimi)
    END;

    PRINT @sqltegevus;
    EXEC (@sqltegevus);
END;
```

# Protseduur, mis kuvab toodete nime, hinna ja lisab automaatselt hinnangu

kui hind < 2 → "soodne"
muidu → "kallis"

```sql
CREATE PROCEDURE kuvaTootedHinnaKategooriaga
AS
BEGIN
    SELECT 
        toodeNimi,
        toodeHind,
        CASE 
            WHEN toodeHind < 2 THEN 'soodne'
            ELSE 'kallis'
        END AS hinnaKategooria
    FROM toode;
END;
```
