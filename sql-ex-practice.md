+ [1](#1)
+ [2](#2)
+ [3](#3)
+ [4](#4)
+ [5](#5)
+ [6](#6)
+ [7](#7)
+ [8](#8)
+ [9](#9)
+ [10](#10)
+ [11](#11)
+ [12](#12)
+ [13](#13)
+ [14](#14)
+ [15](#15)
+ [16](#16)
+ [17](#17)
+ [18](#18)
+ [19](#19)
+ [20](#20)
+ [21](#21)
+ [22](#22)
+ [23](#23)
+ [24](#24)
+ [25](#25)
+ [26](#26)
+ [27](#27)
+ [28](#28)
+ [29](#29)
+ [30](#30)
+ [31](#31)
+ [32](#32)
+ [33](#33)
+ [34](#34)
+ [35](#35)
+ [36](#36)
+ [37](#37)
+ [38](#38)
+ [39](#39)
+ [40](#40)
+ [41](#41)
+ [42](#42)
+ [43](#43)
+ [44](#44)
+ [45](#45)
+ [46](#46)
+ [47](#47)
+ [48](#48)
+ [49](#49)
+ [50](#50)


## 1

https://www.sql-ex.ru/learn_exercises.php?LN=1

```sql
SELECT model, speed, hd   
FROM PC
WHERE price < 500
```

## 2

https://www.sql-ex.ru/learn_exercises.php?LN=2

```sql
SELECT DISTINCT maker 
FROM Product
WHERE type = 'Printer'
```

## 3

https://www.sql-ex.ru/learn_exercises.php?LN=3

```sql
SELECT DISTINCT model, ram, screen
FROM Laptop
WHERE price > 1000
```

## 4

https://www.sql-ex.ru/learn_exercises.php?LN=4

```sql
SELECT code, model, color, type, price
FROM Printer
WHERE color = 'y'
```

## 5

https://www.sql-ex.ru/learn_exercises.php?LN=5

```sql
SELECT DISTINCT model, speed, hd
FROM PC
WHERE price < 600 and cd = '12x' or price < 600 and cd = '24x'
```

## 6

https://www.sql-ex.ru/learn_exercises.php?LN=6

```sql
SELECT DISTINCT Product.maker, Laptop.speed
FROM Product 
JOIN Laptop 
ON Product.model = Laptop.model
WHERE hd >= 10
```

## 7

https://www.sql-ex.ru/learn_exercises.php?LN=7

```sql
SELECT model, price 
FROM PC 
WHERE model IN (SELECT model 
 FROM Product 
 WHERE maker = 'B' AND 
 type = 'PC'
 )
UNION
SELECT model, price 
FROM Laptop 
WHERE model IN (SELECT model 
 FROM Product 
 WHERE maker = 'B' AND 
 type = 'Laptop'
 )
UNION
SELECT model, price 
FROM Printer 
WHERE model IN (SELECT model 
 FROM Product 
 WHERE maker = 'B' AND 
 type = 'Printer'
)
```

## 8
https://www.sql-ex.ru/learn_exercises.php?LN=8

```sql
SELECT DISTINCT maker
FROM Product
WHERE type = 'PC'
EXCEPT
SELECT DISTINCT maker
FROM Product
WHERE type = 'Laptop'
```

## 9

https://www.sql-ex.ru/learn_exercises.php?LN=9

```sql
SELECT DISTINCT Maker
FROM Product JOIN
    PC ON PC.model = Product.model
WHERE PC.speed >= 450
```

## 10

https://www.sql-ex.ru/learn_exercises.php?LN=10

```sql
SELECT DISTINCT model, price
FROM Printer
WHERE price = (SELECT MAX(price) 
 FROM Printer
 )
```

## 11

https://www.sql-ex.ru/learn_exercises.php?LN=11

```sql
SELECT AVG(speed)
FROM PC
```

## 12

https://www.sql-ex.ru/learn_exercises.php?LN=12

```sql
SELECT AVG(speed)
FROM Laptop
WHERE price > 1000
```

## 13

https://www.sql-ex.ru/learn_exercises.php?LN=13

```sql
SELECT AVG(speed)
FROM PC JOIN
Product ON Product.model = PC.model
WHERE Product.maker = 'A'
```
## 14

https://www.sql-ex.ru/learn_exercises.php?LN=14

```sql
SELECT Ships.class, name, country
FROM Ships JOIN
Classes ON Classes.class = Ships.class
WHERE Classes.numGuns >= 10
```

## 15

https://www.sql-ex.ru/learn_exercises.php?LN=15

```sql
SELECT hd
FROM PC
GROUP BY hd
HAVING COUNT(hd) >= 2
```

## 16

https://www.sql-ex.ru/learn_exercises.php?LN=16

```sql
SELECT DISTINCT A.model AS model, B.model AS model, A.speed As speed, A.ram As ram 
FROM PC AS A, PC B 
WHERE A.speed = B.speed AND A.ram = B.ram AND A.model > B.model
```

## 17

https://www.sql-ex.ru/learn_exercises.php?LN=17

```sql
SELECT DISTINCT type, model, speed
FROM Laptop, (SELECT type FROM Product) AS ProductType
WHERE speed < ALL (SELECT speed FROM PC) and type = 'laptop'
```

## 18

https://www.sql-ex.ru/learn_exercises.php?LN=18

```sql
SELECT DISTINCT A.maker, B.price
FROM Product A JOIN
 Printer B on A.model = B.model 
WHERE B.price = (SELECT MIN(price)
 FROM Printer 
 WHERE color = 'y') and B.color = 'y'
```

## 19

https://www.sql-ex.ru/learn_exercises.php?LN=19

```sql
SELECT A.maker, AVG(B.screen)
FROM Product as A JOIN Laptop as B ON A.model = B.model
GROUP BY maker
```

## 20

https://www.sql-ex.ru/learn_exercises.php?LN=20

```sql
SELECT DISTINCT Maker, COUNT(model)
FROM Product
WHERE type = 'PC'
GROUP BY Maker
HAVING COUNT(model)>=3
```

## 21

https://www.sql-ex.ru/learn_exercises.php?LN=21

```sql
SELECT Product.maker, MAX(PC.price)
FROM Product JOIN PC ON Product.model = PC.model
GROUP BY Product.maker
```

## 22

https://www.sql-ex.ru/learn_exercises.php?LN=22

```sql
SELECT speed, AVG(price)
FROM PC
WHERE speed > 600
GROUP BY speed
```

## 23

https://www.sql-ex.ru/learn_exercises.php?LN=23

```sql

```

## 24

https://www.sql-ex.ru/learn_exercises.php?LN=24

```sql

```

## 25

https://www.sql-ex.ru/learn_exercises.php?LN=25

```sql

```

## 26

https://www.sql-ex.ru/learn_exercises.php?LN=26

```sql

```

## 27

https://www.sql-ex.ru/learn_exercises.php?LN=27

```sql

```

## 28

https://www.sql-ex.ru/learn_exercises.php?LN=28

```sql

```

## 29

https://www.sql-ex.ru/learn_exercises.php?LN=29

```sql

```

## 30

https://www.sql-ex.ru/learn_exercises.php?LN=30

```sql

```
