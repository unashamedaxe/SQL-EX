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
