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
6. [ CODERBYTE CHALLENGE ](#item6)

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
