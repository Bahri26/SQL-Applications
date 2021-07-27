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
