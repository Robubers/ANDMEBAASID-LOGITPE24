

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
