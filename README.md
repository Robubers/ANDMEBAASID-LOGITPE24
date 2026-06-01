

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

<img width="480" height="163" alt="{5E84B98D-794C-469A-83A3-8823ED9A335D}" src="https://github.com/user-attachments/assets/1fb4ad5d-9448-430d-8784-ecbf0d07363a" />

<img width="590" height="209" alt="{4CF64057-4FC9-4797-818F-39119A1B1D01}" src="https://github.com/user-attachments/assets/55255cfd-52b6-44c7-b8d0-3d03ef64db9b" />




# PORTFOOLIO

[Select_laused](mockaroo.md) | [Kasutajate_loomine SQL server](kasutaja.md) | [Triggerid](Trigerid.md) | [Kodutöö - keys](keys.md)
