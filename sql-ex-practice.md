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
SELECT prod.maker 
FROM Product AS prod JOIN PC ON prod.model = PC.model 
WHERE PC.speed >= '750' 
INTERSECT
SELECT prod.maker from Product prod JOIN
Laptop AS l on prod.model = l.model
WHERE l.speed >= '750'
```

## 24

https://www.sql-ex.ru/learn_exercises.php?LN=24

```sql
WITH modelsprice AS (
SELECT model, price FROM pc
UNION ALL
SELECT model, price FROM printer
UNION ALL
SELECT model, price FROM laptop )
SELECT DISTINCT model
FROM modelsprice WHERE price = ALL (SELECT max(price) FROM modelsprice)
```

## 25

https://www.sql-ex.ru/learn_exercises.php?LN=25

```sql
SELECT DISTINCT prod.maker
FROM product prod JOIN pc ON prod.model = pc.model 
WHERE pc.ram = (
	SELECT MIN(ram) FROM pc
) 
AND pc.speed = (
SELECT MAX(speed) FROM pc 
WHERE ram = (
SELECT MIN(ram) FROM pc
)) 
AND prod.maker IN (
SELECT maker FROM product WHERE type = 'printer'
)
```

## 26

https://www.sql-ex.ru/learn_exercises.php?LN=26

```sql
SELECT AVG(price) as AVG_price 
FROM (
	SELECT price
	FROM PC 
	WHERE model IN (
		SELECT model 
		FROM product 
		WHERE maker='A' AND type='PC'
) 
UNION ALL 
SELECT price
FROM Laptop
WHERE model IN (
	SELECT model 
	FROM product
	WHERE maker='A' AND type='Laptop')
) AS prices
```

## 27

https://www.sql-ex.ru/learn_exercises.php?LN=27

```sql
SELECT prod.maker, avg(pc.hd) 
FROM product prod JOIN pc on prod.model = pc.model
WHERE pc.model IN (
	SELECT model
	FROM pc
) AND maker IN (
	SELECT maker 
	FROM product 
	WHERE type='printer'
) 
GROUP BY maker
```

## 28

https://www.sql-ex.ru/learn_exercises.php?LN=28

```sql
SELECT COUNT(onemaker) as qty
FROM (
	SELECT maker as onemaker
	FROM product
	GROUP BY maker
	HAVING COUNT(model) = 1
) as name
```

## 29

https://www.sql-ex.ru/learn_exercises.php?LN=29

```sql
SELECT inct.point, inct.date, inc, out 
FROM income_o inct LEFT JOIN outcome_o outt ON inct.point = outt.point AND inct.date = outt.date
UNION
SELECT outt.point, outt.date, inc, out from income_o inct RIGHT JOIN outcome_o outt on inct.point = outt.point and inct.date = outt.date
```

## 30

https://www.sql-ex.ru/learn_exercises.php?LN=30

```sql
SELECT point, date, SUM(sum_out), SUM(sum_inc)
FROM( 
	SELECT point, date, SUM(inc) AS sum_inc, NULL AS sum_out
	FROM income 
	GROUP BY point, date
	UNION
	SELECT point, date, NULL AS sum_inc, SUM(out) AS sum_out 
	FROM outcome 
	GROUP BY point, date 
) AS inout
GROUP BY point, date ORDER BY point
```

## 31

https://www.sql-ex.ru/learn_exercises.php?LN=31

```sql
SELECT class, country
FROM classes
WHERE bore >= 16
```

## 32

https://www.sql-ex.ru/learn_exercises.php?LN=32

```sql
SELECT country, CAST(AVG((power(bore,3)/2)) AS numeric(6,2)) AS weight
FROM (
	SELECT country, classes.class, bore, name 
	FROM classes LEFT JOIN ships ON classes.class=ships.class
	UNION ALL
	SELECT DISTINCT country, class, bore, ship 
	FROM classes t1 LEFT JOIN outcomes t2 on t1.class=t2.ship
	WHERE ship=class AND ship NOT IN (
		SELECT name 
		FROM ships
	) 
) A
WHERE name!='null' 
GROUP BY country
```

## 33

https://www.sql-ex.ru/learn_exercises.php?LN=33

```sql
SELECT ship
FROM outcomes
WHERE battle = 'North Atlantic' AND result = 'sunk'
```

## 34

https://www.sql-ex.ru/learn_exercises.php?LN=34

```sql
SELECT DISTINCT name 
FROM classes, ships 
WHERE launched >=1922 AND displacement>35000 AND type='bb' and ships.class = classes.class
```

## 35

https://www.sql-ex.ru/learn_exercises.php?LN=35

```sql
SELECT model, type 
FROM product 
WHERE model NOT LIKE '%[^0-9]%' OR model NOT LIKE '%[^a-z]%'
```

## 36

https://www.sql-ex.ru/learn_exercises.php?LN=36

```sql
SELECT DISTINCT c.class 
FROM classes c JOIN outcomes o ON c.class = o.ship
UNION
SELECT DISTINCT c.class 
FROM classes c JOIN ships s ON c.class = s.class 
WHERE s.class = s.name
```

## 37

https://www.sql-ex.ru/learn_exercises.php?LN=37

```sql
SELECT class 
FROM(
	SELECT class, name 
	FROM ships
	UNION
	SELECT class, ship AS name 
	FROM outcomes JOIN classes ON classes.class = outcomes.ship
) as A
GROUP BY class 
HAVING COUNT(A.name)=1
```

## 38

https://www.sql-ex.ru/learn_exercises.php?LN=38

```sql
SELECT country 
FROM classes 
WHERE type = 'bb'
INTERSECT
SELECT country 
FROM classes 
WHERE type = 'bc'
```

## 39

https://www.sql-ex.ru/learn_exercises.php?LN=39

```sql
SELECT distinct o.ship 
FROM outcomes o JOIN battles b ON o.battle = b.name 
WHERE o.result = 'damaged' AND EXISTS (
	SELECT battles.date
	FROM battles JOIN outcomes ON outcomes.battle = battles.name
	WHERE battles.date > b.date and outcomes.ship = o.ship)
```

## 40

https://www.sql-ex.ru/learn_exercises.php?LN=40

```sql
SELECT maker, type 
FROM product
WHERE maker IN (
	SELECT maker 
	FROM (
		SELECT maker, type 
		FROM Product 
		GROUP BY maker, type
	) A
	GROUP BY maker 
	HAVING COUNT(maker) = 1
) 
GROUP BY maker, type 
HAVING COUNT(type)>1
```

## 41

https://www.sql-ex.ru/learn_exercises.php?LN=41

```sql
WITH A AS (
	SELECT model, price 
	FROM PC
	UNION
	SELECT model, price 
	FROM Laptop
	UNION
	SELECT model, price 
	FROM Printer
)
SELECT distinct P.maker, CASE WHEN MAX(
	CASE WHEN A.price IS NULL THEN 1 ELSE 0 END
) = 0 THEN MAX(A.price) 
END
FROM Product P RIGHT JOIN A on P.model=A.model
GROUP BY P.maker
```

## 42

https://www.sql-ex.ru/learn_exercises.php?LN=42

```sql
SELECT ship, battle 
FROM outcomes 
WHERE result = 'sunk'
```

## 43

https://www.sql-ex.ru/learn_exercises.php?LN=43

```sql
SELECT name 
FROM battles 
WHERE DATEPART(yy, date) NOT IN (
	SELECT DATEPART(yy, date)
	FROM battles JOIN ships ON DATEPART(yy, date)=launched
)
```

## 44

https://www.sql-ex.ru/learn_exercises.php?LN=44

```sql
SELECT name 
FROM ships 
WHERE name LIKE 'R%'
UNION
SELECT ship 
FROM outcomes 
WHERE ship LIKE 'R%'
```

## 45

https://www.sql-ex.ru/learn_exercises.php?LN=45

```sql
SELECT name 
FROM ships 
WHERE name LIKE '% % %'
UNION
SELECT ship 
FROM outcomes 
WHERE ship LIKE '% % %'
```

## 46

https://www.sql-ex.ru/learn_exercises.php?LN=46

```sql
SELECT DISTINCT ship, displacement, numguns
FROM classes LEFT JOIN ships ON classes.class=ships.class RIGHT JOIN outcomes ON classes.class=ship OR ships.name=ship
WHERE battle='Guadalcanal'
```

## 47

https://www.sql-ex.ru/learn_exercises.php?LN=47

```sql
WITH out AS (SELECT *
FROM outcomes JOIN (SELECT ships.name s_name, classes.class s_class, classes.country s_country
FROM ships FULL JOIN classes
ON ships.class = classes.class
) u
ON outcomes.ship=u.s_class
UNION
SELECT *
FROM outcomes JOIN (SELECT ships.name s_name, classes.class s_class, classes.country s_country
FROM ships FULL JOIN classes
ON ships.class = classes.class
) u
ON outcomes.ship=u.s_name)
SELECT fin.country
FROM (
SELECT DISTINCT t.country, COUNT(t.name) AS num_ships
FROM (
select distinct c.country, s.name
from classes c
inner join Ships s on s.class= c.class
union
select distinct c.country, o.ship
from classes c
inner join Outcomes o on o.ship= c.class) t
GROUP BY t.country
INTERSECT
SELECT out.s_country, COUNT(out.ship) AS num_ships
FROM out
WHERE out.result='sunk'
GROUP BY out.s_country) fin
```

## 48

https://www.sql-ex.ru/learn_exercises.php?LN=48

```sql
SELECT class
FROM classes t1 LEFT JOIN outcomes t2 ON t1.class=t2.ship 
WHERE result='sunk'
UNION
SELECT class
FROM ships LEFT JOIN outcomes ON ships.name=outcomes.ship 
WHERE result='sunk'
```

## 49

https://www.sql-ex.ru/learn_exercises.php?LN=49

```sql
SELECT s.name FROM ships s JOIN classes c on s.name=c.class OR s.class = c.class WHERE c.bore = 16
UNION
SELECT o.ship 
FROM outcomes o JOIN classes c ON o.ship=c.class
WHERE c.bore = 16
```

## 50

https://www.sql-ex.ru/learn_exercises.php?LN=50

```sql
SELECT distinct o.battle 
FROM ships s JOIN outcomes o ON s.name = o.ship 
WHERE s.class = 'kongo'
```

## 51

https://www.sql-ex.ru/learn_exercises.php?LN=51

```sql
SELECT NAME 
FROM (
	SELECT name AS NAME, displacement, numguns 
	FROM ships INNER JOIN classes ON ships.class = classes.class 
	UNION 
	SELECT ship AS NAME, displacement, numguns 
	FROM outcomes INNER JOIN classes ON outcomes.ship= classes.class
) as d1 INNER JOIN (
	SELECT displacement, max(numGuns) AS numguns 
	FROM ( 
		SELECT displacement, numguns 
		FROM ships INNER JOIN classes ON ships.class = classes.class 								 
		UNION 
		SELECT displacement, numguns 
		FROM outcomes INNER JOIN classes ON outcomes.ship= classes.class
	) AS f 
	GROUP BY displacement
) AS d2 ON d1.displacement=d2.displacement AND d1.numguns =d2.numguns
```

## 52

https://www.sql-ex.ru/learn_exercises.php?LN=52

```sql
SELECT s.name 
FROM ships s JOIN classes c on s.class = c.class 
WHERE country = 'japan' AND (
	numGuns >= '9' or numGuns is null
) AND (
	bore < '19' or bore is null
) AND (
	displacement <= '65000' or displacement is null
) AND type='bb';
  
```

## 53

https://www.sql-ex.ru/learn_exercises.php?LN=53

```sql
SELECT CAST(AVG(numguns*1.0) AS NUMERIC(6,2)) AS Avg_nmg 
FROM classes 
WHERE type = 'bb'
```

## 54

https://www.sql-ex.ru/learn_exercises.php?LN=54

```sql
SELECT CAST(AVG(numguns*1.0) AS NUMERIC(6,2)) AS AVG_nmg 
FROM (
	SELECT ship, numguns, type 
	FROM Outcomes JOIN classes ON ship = class
	UNION
	SELECT name, numguns, type 
	FROM ships s join classes c ON c.class = s.class
) AS A 
WHERE type = 'bb'
```

## 55

https://www.sql-ex.ru/learn_exercises.php?LN=55

```sql
SELECT c.class, MIN(s.launched) 
FROM classes c LEFT JOIN ships s ON c.class = s.class 
GROUP BY c.class
```

## 56

https://www.sql-ex.ru/learn_exercises.php?LN=56

```sql
SELECT c.class, COUNT(s.ship)
FROM classes c
LEFT JOIN (
	SELECT o.ship, sh.class
	FROM outcomes o LEFT JOIN ships sh ON sh.name = o.ship
	WHERE o.result = 'sunk'
) AS s ON s.class = c.class OR s.ship = c.class
GROUP BY c.class;
```

## 50

https://www.sql-ex.ru/learn_exercises.php?LN=50

```sql

```

## 50

https://www.sql-ex.ru/learn_exercises.php?LN=50

```sql

```

## 50

https://www.sql-ex.ru/learn_exercises.php?LN=50

```sql

```

## 50

https://www.sql-ex.ru/learn_exercises.php?LN=50

```sql

```

## 50

https://www.sql-ex.ru/learn_exercises.php?LN=50

```sql

```

## 50

https://www.sql-ex.ru/learn_exercises.php?LN=50

```sql

```

## 50

https://www.sql-ex.ru/learn_exercises.php?LN=50

```sql

```

## 50

https://www.sql-ex.ru/learn_exercises.php?LN=50

```sql

```

## 50

https://www.sql-ex.ru/learn_exercises.php?LN=50

```sql

```

## 50

https://www.sql-ex.ru/learn_exercises.php?LN=50

```sql

```

## 50

https://www.sql-ex.ru/learn_exercises.php?LN=50

```sql

```

## 50

https://www.sql-ex.ru/learn_exercises.php?LN=50

```sql

```

## 50

https://www.sql-ex.ru/learn_exercises.php?LN=50

```sql

```

## 50

https://www.sql-ex.ru/learn_exercises.php?LN=50

```sql

```

## 50

https://www.sql-ex.ru/learn_exercises.php?LN=50

```sql

```

## 50

https://www.sql-ex.ru/learn_exercises.php?LN=50

```sql

```

## 50

https://www.sql-ex.ru/learn_exercises.php?LN=50

```sql

```

## 50

https://www.sql-ex.ru/learn_exercises.php?LN=50

```sql

```

## 50

https://www.sql-ex.ru/learn_exercises.php?LN=50

```sql

```

## 50

https://www.sql-ex.ru/learn_exercises.php?LN=50

```sql

```

## 50

https://www.sql-ex.ru/learn_exercises.php?LN=50

```sql

```

## 50

https://www.sql-ex.ru/learn_exercises.php?LN=50

```sql

```
