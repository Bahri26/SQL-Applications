# SQL-Uygulamalar

![PostgreSQL](https://upload.wikimedia.org/wikipedia/commons/2/29/Postgresql_elephant.svg) 

SQL çalışmalarımın uygulamalarını oluşturduğum bir sayfa ile karşınızdayım.
Buradan repository indirebilirsiniz ve kendiniz uygulamaları yapabilirsiniz.

### Uygualama içerikleri şu şekildedir:

1. [ SQL TEMELLERİ - I ](#item1)
2. [ SQL TEMELLERİ - II ](#item2)
3. [ TABLOLARLA ÇALIŞMAK ](#item3)
4. [ JOIN YAPILARI ](#item4)
5. [ ALT SORGULAR ](#item5)

<a name="item1">SQL TEMELLERİ - I</a>
## **SELECT**: Veritabanından verileri çekmek için kullanılır.
* `SELECT` * `FROM` table_name;

### ÖRNEK 1: film tablosunda bulunan title ve description sütunlarındaki verileri sıralayınız.

* `SELECT` title,description `FROM` film;

![alt text](https://github.com/Bahri26/SQL-Applications/blob/main/Results/picture1.PNG) 

## **WHERE**: Veritabanından verileri işlem yaparken şartlı ifadeler için kullanılır.
* `SELECT` * `FROM` table_name `WHERE` condition;

### ÖRNEK 2: film tablosunda bulunan tüm sütunlardaki verileri film uzunluğu (length) 60 dan büyük VE 75 ten küçük olma koşullarıyla sıralayınız.

* `SELECT` * `FROM` film `WHERE` length > 60 `AND` length < 75;

![alt text](https://github.com/Bahri26/SQL-Applications/blob/main/Results/picture2.PNG)![alt text](https://github.com/Bahri26/SQL-Applications/blob/main/Results/picture2-1.PNG)

### Örnek 3: film tablosunda bulunan tüm sütunlardaki verileri rental_rate 0.99 VE replacement_cost 12.99 VEYA 28.99 olma koşullarıyla sıralayınız.

* `SELECT` * `FROM` film `WHERE` rental_rate = 0.99 `AND` replacement_cost = 12.99 `OR` replacement_cost = 28.99;

![alt text](https://github.com/Bahri26/SQL-Applications/blob/main/Results/picture3.PNG)![alt text](https://github.com/Bahri26/SQL-Applications/blob/main/Results/picture3-1.PNG)

### Örnek 4: customer tablosunda bulunan first_name sütunundaki değeri 'Mary' olan müşterinin last_name sütunundaki değeri nedir?

* `SELECT` last_name `FROM` customer `WHERE` first_name = 'Mary'

![alt text](https://github.com/Bahri26/SQL-Applications/blob/main/Results/picture4.PNG)

### Örnek 5: film tablosundaki uzunluğu(length) 50 ten büyük OLMAYIP aynı zamanda rental_rate değeri 2.99 veya 4.99 OLMAYAN verileri sıralayınız.

* `SELECT` * `FROM` film `WHERE` length <= 50 `AND` rental_rate = 2.99 `OR` rental_rate = 4.99

![alt text](https://github.com/Bahri26/SQL-Applications/blob/main/Results/picture5.PNG)![alt text](https://github.com/Bahri26/SQL-Applications/blob/main/Results/picture5-1.PNG)

## BETWEEN AND : Bir sütunun istediğimiz iki değer aralıkta verileri döndürmek için WHERE ile kullanılır.
* `SELECT` * `FROM` table_name `WHERE` column_name `BETWEEN` value1 `AND` value2;

### Örnek 6: film tablosunda bulunan tüm sütunlardaki verileri replacement cost değeri 12.99 dan büyük eşit ve 16.99 küçük olma koşuluyla sıralayınız.
* `SELECT` * `FROM` film `WHERE` replacement_cost `BETWEEN` 12.99 `AND` 16.99;

![alt text](https://github.com/Bahri26/SQL-Applications/blob/main/Results/resim6.PNG)![alt text](https://github.com/Bahri26/SQL-Applications/blob/main/Results/resim6-1.PNG)

## IN : Kolon içerisinde istediğimiz değerleri döndürmek için WHERE sorgusunun içinde belirtilir.
* `SELECT` * `FROM` table_name `WHERE` column_name `IN`(value1,value2,.....);

### Örnek 7: tablosunda bulunan first_name ve last_name sütunlardaki verileri first_name 'Penelope' veya 'Nick' veya 'Ed' değerleri olması koşuluyla sıralayınız.

* `SELECT` first_name,last_name `FROM` actor `WHERE` first_name `IN`('Penelope','Nick','Ed')

![alt text](https://github.com/Bahri26/SQL-Applications/blob/main/Results/resim6.PNG)![alt text](https://github.com/Bahri26/SQL-Applications/blob/main/Results/resim7.PNG)

### Örnek 8: ilm tablosunda bulunan tüm sütunlardaki verileri rental_rate 0.99, 2.99, 4.99 VE replacement_cost 12.99, 15.99, 28.99 olma koşullarıyla sıralayınız.

* `SELECT` * `FROM` film `WHERE` rental_rate IN(0.99, 2.99, 4.99) `AND` replacement_cost `IN`(12.99, 15.99, 28.99)

![alt text](https://github.com/Bahri26/SQL-Applications/blob/main/Results/resim8.PNG)![alt text](https://github.com/Bahri26/SQL-Applications/blob/main/Results/resim8-1.PNG)

## LIKE : WHERE şart ifadesinin içinde filtreleme yani benzer ifadelerinin sonuçlarını getirmek istediğimiz zamana kullanırız. ILIKE operatörü LIKE operatörünün case - insensitive versiyonudur. Kullanılan % karakteri sıfır, bir veya daha fazla karakteri temsil eder ve Wildcard olarak isimlendirilir. Bir diğer wildcard karakteri _ karakteridir ve bir karekteri temsil eder.

* `SELECT` * `FROM` table_name `WHERE` column_name `LIKE` sablon

### Örnek 9: country tablosunda bulunan country sütunundaki ülke isimlerinden 'A' karakteri ile başlayıp 'a' karakteri ile sonlananları sıralayınız.

* `SELECT` country `FROM` country `WHERE` country `LIKE` 'A%%a'

![alt text](https://github.com/Bahri26/SQL-Applications/blob/main/Results/resim9.PNG)

### Örnek 10: country tablosunda bulunan country sütunundaki ülke isimlerinden en az 6 karakterden oluşan ve sonu 'n' karakteri ile sonlananları sıralayınız.

* `SELECT` country `FROM` country `WHERE` length(country)>6 `AND` country `LIKE` '%n'

![alt text](https://github.com/Bahri26/SQL-Applications/blob/main/Results/resim10.PNG)

### Örnek 11: film tablosunda bulunan title sütunundaki film isimlerinden en az 4 adet büyük ya da küçük harf farketmesizin 'T' karakteri içeren film isimlerini sıralayınız.

* `SELECT` title `FROM` film `WHERE` title `LIKE` '%__T_%'

![alt text](https://github.com/Bahri26/SQL-Applications/blob/main/Results/resim11.PNG)

### Örnek 12: film tablosunda bulunan tüm sütunlardaki verilerden title 'C' karakteri ile başlayan ve uzunluğu (length) 90 dan büyük olan ve rental_rate 2.99 olan verileri sıralayınız.

* `SELECT` * `FROM` film `WHERE` title `LIKE` 'C%' `AND` `length`(title)>90 `AND` rental_rate=2.99

![alt text](https://github.com/Bahri26/SQL-Applications/blob/main/Results/resim12.PNG)

## DISTINCT : Tablodaki eşsiz satırları getirmeye yarar.

*  `SELECT` `DISTINCT` column_name `FROM` table_name

## COUNT : Tablodaki verileri saymak için kullanılır.

* `SELECT` `COUNT(*)` column_name `FROM` table_name 
* `SELECT` `COUNT(*)` column_name `FROM` table_name `WHERE` condition
* `SELECT` `COUNT(column_name)` column_name `FROM` table_name `WHERE` condition

### Örnek 13: film tablosunda bulunan replacement_cost sütununda bulunan birbirinden farklı değerleri sıralayınız.

* `SELECT` `DISTINCT` replacement_cost `FROM` film

![alt text](https://github.com/Bahri26/SQL-Applications/blob/main/Results/resim13.PNG)

### Örnek 14: film tablosunda bulunan replacement_cost sütununda birbirinden farklı kaç tane veri vardır?

* `SELECT` `COUNT`(`DISTINCT` replacement_cost) `FROM` film

![alt text](https://github.com/Bahri26/SQL-Applications/blob/main/Results/resim14.PNG)

### Örnek 15: film tablosunda bulunan replacement_cost sütununda birbirinden farklı kaç tane veri vardır?

* `SELECT` `COUNT`(Title) `FROM` film `WHERE` TITLE `LIKE` 'T%' `AND` rating = 'G'

![alt text](https://github.com/Bahri26/SQL-Applications/blob/main/Results/resim15.PNG)

### Örnek 16: country tablosunda bulunan ülke isimlerinden (country) kaç tanesi 5 karakterden oluşmaktadır?

* `SELECT` `COUNT`(country) `FROM` country `WHERE` country `LENGTH`(country) = 5

![alt text](https://github.com/Bahri26/SQL-Applications/blob/main/Results/resim16.PNG)

### Örnek 17: city tablosundaki şehir isimlerinin kaçtanesi 'R' veya r karakteri ile biter?

* `SELECT` `COUNT`(CITY) `FROM` CITY `WHERE` CITY `LIKE` '%R' `OR` CITY `LIKE` '%r'

![alt text](https://github.com/Bahri26/SQL-Applications/blob/main/Results/resim17.PNG)

<a name="item2">SQL TEMELLERİ - II</a>
## `ORDER BY` : Verilerimizi herhangi bir sütunda bulunan değerlere göre azalan veya artan bir şekilde sıralayabiliriz.
* `SELECT` * `FROM` table_name `ORDER BY` ASC/DESC ;
* ASC : Verilerimizi A-Z sıralama yapar yani artağan bir şekilde sıralar.
* DESC : Verilerimizi Z-A sıralama yapar yani azalan bir şekilde sıralar.
* Order By ifadesinin varsayılan değeri `ASC` kullanımıdır.
* Limit : Verilerimizin sayısını sınırlamak için kullanılır. 
* Offset : Bazı veri grubunun pas geçilmesi için kullanılır.

### Örnek 18: film tablosunda bulunan ve film ismi (title) 'n' karakteri ile biten en uzun (length) 5 filmi sıralayınız.
* `SELECT` title `FROM` FILM `WHERE` TITLE `LIKE` '%n' `ORDER BY` LENGTH DESC LIMIT 5 ;

![alt text](https://github.com/Bahri26/SQL-Applications/blob/main/Results/resim18.PNG)

### Örnek 19: film tablosunda bulunan ve film ismi (title) 'n' karakteri ile biten en kısa (length) ikinci 5 filmi sıralayınız.
* `SELECT` title `FROM` FILM `WHERE` TITLE `LIKE` '%n' `ORDER BY` LENGTH `ASC` `Offset` 5 `Limit` 5 ;

![alt text](https://github.com/Bahri26/SQL-Applications/blob/main/Results/resim19.PNG)

### Örnek 20: customer tablosunda bulunan last_name sütununa göre azalan yapılan sıralamada store_id 1 olmak koşuluyla ilk 4 veriyi sıralayınız.
* `SELECT` * `FROM` CUSTOMER `Where` store_id = 1 `Order By` last_name `DESC` `Limit` 4

![alt text](https://github.com/Bahri26/SQL-Applications/blob/main/Results/resim20.PNG)![alt text](https://github.com/Bahri26/SQL-Applications/blob/main/Results/resim20-1.PNG)

## `Aggregate Fonksiyonlar`: Veri kümelerimizden tek sonuçlar çıkarabilmek için kullanılır.
* `AVG`: sayısal değerlerden oluşan sütunun ortalama değerini alırız.
* `SUM`: sayısal değerlerden oluşan sütunun toplam değerini alırız.
* `MAX`: sayısal değerlerden oluşan sütunun en yüksek değerini alırız.
* `MIN`: sayısal değerlerden oluşan sütunun en KÜÇÜK değerini alırız.

### Örnek 21: film tablosunda bulunan rental_rate sütunundaki değerlerin ortalaması nedir?
* `SELECT` `AVG`(rental_rate) `FROM` FILM

![alt text](https://github.com/Bahri26/SQL-Applications/blob/main/Results/resim21.PNG)

### Örnek 22: film tablosunda bulunan filmlerden kaçtanesi 'C' karekteri ile başlar?
* `SELECT` `COUNT`(rental_rate) `FROM` FILM `Where` title `LIKE` 'C%'

![alt text](https://github.com/Bahri26/SQL-Applications/blob/main/Results/resim22.PNG)

### Örnek 23: film tablosunda bulunan filmlerden rental_rate değeri 0.99 a eşit olan en uzun (length) film kaç dakikadır?
* `SELECT` `MAX`(LENGTH) `FROM` FILM `Where` rental_rate= 0.99

![alt text](https://github.com/Bahri26/SQL-Applications/blob/main/Results/resim23.PNG)

### Örnek 24: film tablosunda bulunan filmlerin uzunluğu 150 dakikadan büyük olanlarına ait kaç farklı replacement_cost değeri vardır?
* `SELECT` `COUNT`(`DISTINCT` replacement_cost) `FROM` FILM `Where` LENGTH > 150

![alt text](https://github.com/Bahri26/SQL-Applications/blob/main/Results/resim24.PNG)

## `Group By`: Birden fazla sütunları gruplama yapmak ve kümeleme fonksiyonları kullanmak için ihtiyaç duyarız.
* `SELECT` grouped_column| grouped_columns `FROM` table_name `Group By` grouped_column| grouped_columns
* `Having` : `Group By` ile kullanılan gruplanmış sütunlar üzerinde aggregate fonksiyonları kullanabildiğimiz ifadedir.

### Örnek 25: film tablosunda bulunan filmleri rating değerlerine göre gruplayınız.
* `SELECT` RATING `FROM` FILM `Group By` RATING

![alt text](https://github.com/Bahri26/SQL-Applications/blob/main/Results/resim25.PNG)

### Örnek 26: film tablosunda bulunan filmleri replacement_cost sütununa göre grupladığımızda film sayısı 50 den fazla olan replacement_cost değerini ve karşılık gelen film sayısını sıralayınız.
* `SELECT` replacement_cost,COUNT(FILM) `FROM` FILM `Group By` replacement_cost `HAVING` COUNT(FILM)

![alt text](https://github.com/Bahri26/SQL-Applications/blob/main/Results/resim26.PNG)

### Örnek 27: customer tablosunda bulunan store_id değerlerine karşılık gelen müşteri sayılarını nelerdir?
* `SELECT` store_id,COUNT(customer_id) `FROM` CUSTOMER `Group By` store_id

![alt text](https://github.com/Bahri26/SQL-Applications/blob/main/Results/resim27.PNG)

### Örnek 28: city tablosunda bulunan şehir verilerini country_id sütununa göre gruplandırdıktan sonra en fazla şehir sayısı barındıra country_id bilgisini ve şehir sayısını paylaşınız.
* `SELECT` country_id,COUNT(country_id) `FROM` CITY `Group By` country_id `ORDER BY` COUNT(country_id) `DESC` LIMIT 1

![alt text](https://github.com/Bahri26/SQL-Applications/blob/main/Results/resim28.PNG)

<a name="item3">TABLOLARLA ÇALIŞMAK</a>
## CREATE TABLE: Veritabanında tablo oluşturmak için kullanılan SQL ifadesidir.
CREATE TABLE table_name (
  column_name1 type_name1 constraint_name1,
  column_name2 type_name2 constraint_name2,
  ....
);

CREATE TABLE author (
  id SERIAL PRIMARY KEY,
  first_name VARCHAR(50) NOT NULL,
  last_name VARCHAR(50) NOT NULL,
  email VARCHAR(100)
  birthday DATE
);

## DROP TABLE: Veritabanında tablo silmek için kullanılır.
DROP TABLE (IF EXISTS) table_name;

DROP TABLE IF EXISTS test;

## Update: Veritabanı sütunlarındaki verileri değiştirmek için kullanabiliriz.
UPDATE table_name SET column_name = value,..... Where condition

UPDATE my_apps
SET name = 'Mayak',
	price = '$5.22'
WHERE id = 2;

## Insert Into: Veritabanı sütunlarına veri eklemek için kullanılır.
INSERT INTO tbale_name (column_name) | empty (values)

INSERT INTO my_apps (id, name, price) values (1, 'Ronstring', '$0.96');
INSERT INTO my_apps (id, name, price) values (2, 'Duobam', '$3.44');
INSERT INTO my_apps (id, name, price) values (3, 'Tresom', '$2.21');
INSERT INTO my_apps (id, name, price) values (4, 'Redhold', '$2.52');
INSERT INTO my_apps (id, name, price) values (5, 'Y-find', '$9.14');

## Delete: Veritabanından koşula göre veritabanından değer silmek için kullanılır.
DELETE FROM table_name Where condition

DELETE FROM my_apps
WHERE name = 'Tresom';

### Örnek 29: test veritabanınızda employee isimli sütun bilgileri id(INTEGER), name VARCHAR(50), birthday DATE, email VARCHAR(100) olan bir tablo oluşturalım.

![alt text](https://github.com/Bahri26/SQL-Applications/blob/main/Results/resim30.PNG)

### Örnek 30: Oluşturduğumuz employee tablosuna 'Mockaroo' servisini kullanarak 50 adet veri ekleyelim.

![alt text](https://github.com/Bahri26/SQL-Applications/blob/main/Results/resim31.PNG)![alt text](https://github.com/Bahri26/SQL-Applications/blob/main/Results/resim31-1.PNG)

### Örnek 31: Sütunların her birine göre diğer sütunları güncelleyecek 5 adet UPDATE işlemi yapalım.

![alt text](https://github.com/Bahri26/SQL-Applications/blob/main/Results/resim32.PNG)!

### Örnek 32: Sütunların her birine göre ilgili satırı silecek 5 adet DELETE işlemi yapalım.

![alt text](https://github.com/Bahri26/SQL-Applications/blob/main/Results/resim33.PNG)!

## Primary Key(Birincil Anahtar): bir tabloda bulunan veri sıralarını birbirinden ayırmamızı sağlayan bir kısıtlama (constraint) yapısıdır. O tabloda bulunan veri sıralarına ait bir "benzersiz tanımlayıcıdır".

*  Benzersiz (Unique) olmalıdır.
*  NULL değerine sahip olamaz.
*  Bir tabloda en fazla 1 tane bulunur

## FOREIGN KEY: bir tabloda bulunan herhangi bir sütundaki verilerin genelde başka bir tablo sütununa referans vermesi durumudur, tablolar arası ilişki kurulmasını sağlar.

* Bir tabloda birden fazla sütun FK olarak tanımlanabilir.
* Aynı sütunun içerisinde aynı değerler bulunabilir.

## Veri Tipleri - I

![alt text](https://github.com/Bahri26/SQL-Applications/blob/main/Results/veri-tipleri.png)!

## Veri Tipleri - II

### Karakter Veri Tipleri

![alt text](https://github.com/Bahri26/SQL-Applications/blob/main/Results/character_type.png)!

### Tarih ve Zaman Tipleri

![alt text](https://github.com/Bahri26/SQL-Applications/blob/main/Results/date-time.png)!

<a name="item4">JOIN YAPILARI</a>
-- Veraitabanları çoğunlukla birbiri ile ilşkili olan tablolardan oluşur. Bu birbiri ile ilişkili olan tablardaki verileri farklı JOIN yapıları kullanarak sanal olarak birleştirip daha anlamlı veriler haline getirebiliriz.

## INNER JOIN : İki farklı tablodaki verilerin ortak sütunları kesişen tüm verileri getirir.

![alt text](https://github.com/Bahri26/SQL-Applications/blob/main/Results/InnerJoin.png)!

`SELECT` column_name `FROM` table_1 `INNER JOIN` table_2 `ON` table_1.column_name = table_2.column_name

### Örnek 33: city tablosu ile country tablosunda bulunan şehir (city) ve ülke (country) isimlerini birlikte görebileceğimiz INNER JOIN sorgusunu yazınız.

* SELECT city,country FROM CITY INNER JOIN COUNTRY ON CITY.country_id = COUNTRY.country_id LIMIT 10

![alt text](https://github.com/Bahri26/SQL-Applications/blob/main/Results/resim34.PNG)!

### Örnek 34: customer tablosu ile payment tablosunda bulunan payment_id ile customer tablosundaki first_name ve last_name isimlerini birlikte görebileceğimiz INNER JOIN sorgusunu yazınız.

* SELECT first_name,last_name FROM CUSTOMER INNER JOIN PAYMENT ON CUSTOMER.customer_id = PAYMENT.customer_id LIMIT 10

![alt text](https://github.com/Bahri26/SQL-Applications/blob/main/Results/resim35.PNG)!

### Örnek 35: customer tablosu ile rental tablosunda bulunan rental_id ile customer tablosundaki first_name ve last_name isimlerini birlikte görebileceğimiz INNER JOIN sorgusunu yazınız.

* SELECT first_name,last_name FROM CUSTOMER INNER JOIN RENTAL ON CUSTOMER.customer_id = RENTAL.customer_id LIMIT 10

![alt text](https://github.com/Bahri26/SQL-Applications/blob/main/Results/resim36.PNG)!

## LEFT JOIN: yapısındaki tablo birleştirmesinde, birleştirme işlemi tablo 1 (soldaki tablo) üzerinden gerçekleştirilir. Tablo 2 null değer bile olsa her ne olursa olsun değerler getirilir. 

![alt text](https://github.com/Bahri26/SQL-Applications/blob/main/Results/LeftJoin.png)!

`SELECT` column_name `FROM` table_1 `LEFT JOIN` table_2 `ON` table_1.column_name = table_2.column_name

## RIGHT JOIN: RIGHT JOIN yapısındaki tablo birleştirmesinde, birleştirme işlemi tablo 2 (sağdaki tablo) üzerinden gerçekleştirilir. Tablo 1 null değer bile olsa her ne olursa olsun değerler getirilir. 

![alt text](https://github.com/Bahri26/SQL-Applications/blob/main/Results/RightJoin.png)!

`SELECT` column_name `FROM` table_1 `RIGHT JOIN` table_2 `ON` table_1.column_name = table_2.column_name

## FULL JOIN : LEFT JOIN yapısındaki tablo birleştirmesinde, birleştirme işlemi her iki tablo üzerinden gerçekleştirilir. Fakat kesişen değerler ile tablo1 ve tablo2 özgü değerler de getirilir.

![alt text](https://github.com/Bahri26/SQL-Applications/blob/main/Results/FullJoin.png)!

`SELECT` column_name `FROM` table_1 `FULL JOIN` table_2 `ON` table_1.column_name = table_2.column_name

### Örnek36: city tablosu ile country tablosunda bulunan şehir (city) ve ülke (country) isimlerini birlikte görebileceğimiz LEFT JOIN sorgusunu yazınız.

* SELECT city,country FROM CITY LEFT JOIN COUNTRY ON CITY.country_id = COUNTRY.country_id LIMIT 10

![alt text](https://github.com/Bahri26/SQL-Applications/blob/main/Results/resim37.PNG)!

 ### Örnek37: customer tablosu ile payment tablosunda bulunan payment_id ile customer tablosundaki first_name ve last_name isimlerini birlikte görebileceğimiz RIGHT JOIN sorgusunu yazınız.
 
* SELECT first_name,last_name FROM CUSTOMER RIGHT JOIN PAYMENT ON CUSTOMER.customer_id = PAYMENT.customer_id LIMIT 10

![alt text](https://github.com/Bahri26/SQL-Applications/blob/main/Results/resim38.PNG)!

### Örnek38: customer tablosu ile rental tablosunda bulunan rental_id ile customer tablosundaki first_name ve last_name isimlerini birlikte görebileceğimiz FULL JOIN sorgusunu yazınız.

* SELECT first_name,last_name FROM CUSTOMER FULL JOIN RENTAL ON CUSTOMER.customer_id = RENTAL.customer_id LIMIT 10

![alt text](https://github.com/Bahri26/SQL-Applications/blob/main/Results/resim39.PNG)!

<a name="item5">ALT SORGULAR</a>
-- Bir sorgu içerisinde, o sorgunun ihtiyaç duyduğu veri veya verileri getiren sorgulardır.

### Örnek40: bookstore veritabanında "Gülün Adı" isimli kitabımızın sayfa sayısı 466 dır. Bu kitaptan daha fazla sayıda sayfası bulunan kitapları aşağıdaki sorgu yardımıyla ve 466 rakamını aşağıdaki sorgu yardımıyla bulabiliriz.

* SELECT * FROM book WHERE page_number > 466;
* SELECT page_number FROM book  WHERE title = 'Gülün Adı'

* SELECT * FROM book WHERE page_number > ( SELECT page_number FROM book WHERE title = 'Gülün Adı' );

## Any Operatörü: Alt sorgudan gelen herhangi bir değer koşulu sağlaması durumunda TRUE olarak ilgili değerin koşu sağlamasını sağlar. 

* SELECT first_name, last_name
* FROM author
* WHERE id = ANY
* (
* SELECT id
* FROM book
* WHERE title = 'Abe Lincoln in Illinois' OR title = 'Saving Shiloh'
* );

## All Operatörü: Alt sorgudan gelen tüm değerlerin koşulu sağlaması durumunda TRUE olarak döner.

* SELECT first_name, last_name
* FROM author
* WHERE id = ALL
* (
* SELECT id
* FROM book
* WHERE title = 'Abe Lincoln in Illinois' OR title = 'Saving Shiloh'
* );

### Örnek39: film tablosunda film uzunluğu length sütununda gösterilmektedir. Uzunluğu ortalama film uzunluğundan fazla kaç tane film vardır?

* SELECT COUNT(*) AS FILIMSAYISI FROM FILM WHERE LENGTH > (SELECT ROUND(AVG(LENGTH)) FROM FILM)

![alt text](https://github.com/Bahri26/SQL-Applications/blob/main/Results/resim40.PNG)!

### Örnek40: film tablosunda en yüksek rental_rate değerine sahip kaç tane film vardır?

* SELECT COUNT(*) AS filmSayısı FROM film WHERE rental_rate = (SELECT MAX(rental_rate) FROM FILM)

![alt text](https://github.com/Bahri26/SQL-Applications/blob/main/Results/resim41.PNG)!

### Örnek41: film tablosunda en düşük rental_rate ve en düşün replacement_cost değerlerine sahip filmleri sıralayınız.

* SELECT title FROM film WHERE rental_rate = (SELECT MIN(rental_rate) FROM FILM) AND replacement_cost = (SELECT MIN(replacement_cost) FROM FILM) LIMIT 10

![alt text](https://github.com/Bahri26/SQL-Applications/blob/main/Results/resim42.PNG)!

### Örnek42: payment tablosunda en fazla sayıda alışveriş yapan müşterileri(customer) sıralayınız.

* SELECT * FROM customer WHERE customer_id IN (SELECT customer_id FROM payment WHERE amount = (SELECT max(amount) from payment))

![alt text](https://github.com/Bahri26/SQL-Applications/blob/main/Results/resim43.PNG)! ![alt text](https://github.com/Bahri26/SQL-Applications/blob/main/Results/resim43-1.PNG)!

## Alt Sorgular ve Join Kullanımı

### Örnek42: bookstore veri tabanında kitap sayfası sayısı ortalama kitap sayfası sayısından fazla olan kitapların isimlerini, bu kitapların yazarlarına ait isim ve soyisim bilgileriyle birlikte sıralayınız.

* SELECT author.first_name, author.last_name, book.title
* FROM author
* INNER JOIN book ON book.author_id = author.id
* WHERE page_number >
* (
* SELECT AVG(page_number) FROM book
* );

### Örnek43: film tablosundan 'K' karakteri ile başlayan en uzun ve replacenet_cost u en düşük 4 filmi sıralayınız.

* SELECT TITLE FROM FILM WHERE TITLE LIKE 'K%' ORDER BY LENGTH(TITLE) DESC,replacement_cost ASC LIMIT 4

![alt text](https://github.com/Bahri26/SQL-Applications/blob/main/Results/resim44.PNG)!

### Örnek44: film tablosunda içerisinden en fazla sayıda film bulunduran rating kategorisi hangisidir?

* SELECT rating,count(rating) FROM FILM GROUP BY rating ORDER BY count(rating) LIMIT 1

![alt text](https://github.com/Bahri26/SQL-Applications/blob/main/Results/resim45.PNG)!

### Örnek45: cutomer tablosunda en çok alışveriş yapan müşterinin adı nedir?

* SELECT first_name FROM customer WHERE customer_id IN (SELECT customer_id FROM payment WHERE amount = (SELECT max(amount) from payment)) LIMIT 1

![alt text](https://github.com/Bahri26/SQL-Applications/blob/main/Results/resim46.PNG)!

### Örnek46: category tablosundan kategori isimlerini ve kategori başına düşen film sayılarını sıralayınız.

* SELECT CATEGORY.NAME,COUNT(CATEGORY.category_id) FROM FILM_CATEGORY 
* INNER JOIN CATEGORY 
* ON FILM_CATEGORY.category_id = CATEGORY.category_id
* GROUP BY CATEGORY.NAME

![alt text](https://github.com/Bahri26/SQL-Applications/blob/main/Results/resim47.PNG)!

