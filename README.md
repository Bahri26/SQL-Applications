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

<a name="item1"></a>
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
