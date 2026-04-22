

# ANDMEBAASID-LOGITPE24

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








# !!!VOT SEE ASI SIIN ALL!!!







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

--protseduur mis kustutab tabelist id järgi 

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




<img width="777" height="370" alt="{CEDDBA03-9150-4A63-95E2-205BF1DF05CB}" src="https://github.com/user-attachments/assets/606eb955-583e-404a-b309-9fbc2671babe" />

