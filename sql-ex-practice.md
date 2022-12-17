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
+ [51](#51)
+ [52](#52)
+ [53](#53)
+ [54](#54)
+ [55](#55)
+ [56](#56)
+ [57](#57)
+ [58](#58)
+ [59](#59)
+ [60](#60)
+ [61](#61)
+ [62](#62)
+ [63](#63)
+ [64](#64)
+ [65](#65)
+ [66](#66)
+ [67](#67)
+ [68](#68)
+ [69](#69)
+ [70](#70)
+ [71](#71)
+ [72](#72)
+ [73](#73)
+ [74](#74)
+ [75](#75)
+ [76](#76)
+ [77](#77)
+ [78](#78)
+ [79](#79)
+ [80](#80)
+ [81](#81)
+ [82](#82)
+ [83](#83)
+ [84](#84)
+ [85](#85)
+ [86](#86)
+ [87](#87)
+ [88](#88)
+ [89](#89)
+ [90](#90)
+ [91](#91)
+ [92](#92)
+ [93](#93)
+ [94](#94)
+ [95](#95)
+ [96](#96)
+ [97](#97)
+ [98](#98)
+ [99](#99)
+ [100](#100)


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

## 57

https://www.sql-ex.ru/learn_exercises.php?LN=57

```sql
SELECT class, COUNT(ship) count_sunked
FROM (
	SELECT name, class 
	FROM ships
	UNION
	SELECT ship, ship
	FROM outcomes
) t LEFT JOIN outcomes ON name = ship AND result = 'sunk'
GROUP BY class
HAVING COUNT(ship) > 0 AND COUNT(*) > 2
```

## 58

https://www.sql-ex.ru/learn_exercises.php?LN=58

```sql
SELECT m, t,
CAST(100.0*cc/cc1 AS NUMERIC(5,2))
FROM (
	SELECT m, t, sum(c) cc 
	FROM (
		SELECT distinct maker m, 'PC' t, 0 c 
		FROM product
		UNION ALL
		SELECT distinct maker, 'Laptop', 0 
		FROM product
		UNION ALL
		SELECT distinct maker, 'Printer', 0 
		FROM product
		UNION ALL
		SELECT maker, type, count(*) 
		FROM product
		GROUP BY maker, type
	) AS tt
	GROUP BY m, t
) tt1 JOIN (
	SELECT maker, count(*) cc1 
	FROM product 
	GROUP BY maker
) tt2 ON m=maker
```

## 59

https://www.sql-ex.ru/learn_exercises.php?LN=59

```sql
SELECT c1, c2- (
	CASE WHEN o2 is null 
	THEN 0
	ELSE o2
	END
)
FROM (
	SELECT point c1, sum(inc) c2 
	FROM income_o
	GROUP BY point
) AS t1 LEFT JOIN (
	SELECT point o1, sum(out) o2 
	FROM outcome_o
	GROUP BY point
) as t2
on c1=o1
```

## 60

https://www.sql-ex.ru/learn_exercises.php?LN=60

```sql
SELECT c1, c2- (
	CASE WHEN o2 is null 
	THEN 0
	ELSE o2
	END
)
FROM (
	SELECT point c1, sum(inc) c2 
	FROM income_o
	WHERE date<'2001-04-15'
	GROUP BY point
) AS t1 LEFT JOIN (
	SELECT point o1, sum(out) o2 
	FROM outcome_o
	WHERE date<'2001-04-15'
	GROUP BY point
) AS t2 ON c1=o1
```

## 61

https://www.sql-ex.ru/learn_exercises.php?LN=61

```sql
SELECT sum(i) 
FROM (
	SELECT point, sum(inc) as i 
	FROM income_o
	GROUP BY point
	UNION
	SELECT point, -sum(out) as i 
	FROM outcome_o
	GROUP BY point
) AS t
```

## 62

https://www.sql-ex.ru/learn_exercises.php?LN=62

```sql
SELECT (
	SELECT sum(inc) 
	FROM Income_o 
	WHERE date<'2001-04-15'
)
- (
	SELECT sum(out) 
	FROM Outcome_o 
	WHERE date<'2001-04-15'
) AS remain
```

## 63

https://www.sql-ex.ru/learn_exercises.php?LN=63

```sql
SELECT name 
FROM Passenger
WHERE ID_psg in
(SELECT ID_psg 
FROM Pass_in_trip
GROUP BY place, ID_psg
HAVING count(*)>1)
```

## 64

https://www.sql-ex.ru/learn_exercises.php?LN=64

```sql
SELECT i1.point, i1.date, 'inc', sum(inc) 
FROM Income, (
	SELECT point, date 
	FROM Income
	EXCEPT
	SELECT Income.point, Income.date 
	FROM Income
	JOIN Outcome ON (Income.point=Outcome.point) AND (Income.date=Outcome.date)
) AS i1
WHERE i1.point=Income.point AND i1.date=Income.date
GROUP BY i1.point, i1.date
UNION
SELECT o1.point, o1.date, 'out', sum(out) 
FROM Outcome, (
	SELECT point, date 
	FROM Outcome
	EXCEPT
	SELECT Income.point, Income.date 
	FROM Income
	JOIN Outcome ON (Income.point=Outcome.point) AND
(Income.date=Outcome.date)
) AS o1
WHERE o1.point=Outcome.point AND o1.date=Outcome.date
GROUP BY o1.point, o1.date
```

## 65

https://www.sql-ex.ru/learn_exercises.php?LN=65

```sql
SELECT row_number() over(ORDER BY maker,s),t, type 
FROM (
	SELECT maker,type,
	CASE
	WHEN type='PC'
	THEN 0
	WHEN type='Laptop'
	THEN 1
	ELSE 2
	END AS s,
	CASE
	WHEN type='Laptop' AND (maker in (
		SELECT maker 
		FROM Product 
		WHERE type='PC')
	)
	THEN ''
	WHEN type='Printer' AND ((maker in (
		SELECT maker 
		FROM Product 
		WHERE type='PC'
	)) OR (maker in (
		SELECT maker 
		FROM Product 
		WHERE type='Laptop'
)))
THEN ''
ELSE maker
END AS t
FROM Product
GROUP BY maker,type) AS t1
ORDER BY maker, s
```

## 66

https://www.sql-ex.ru/learn_exercises.php?LN=66

```sql
SELECT date, max(c) 
FROM (
	SELECT date,count(*) AS c 
	FROM Trip, (
		SELECT trip_no,date 
		FROM Pass_in_trip 
		WHERE date>='2003-04-01' AND date<='2003-04-07' 
		GROUP BY trip_no, date
	) AS t1
	WHERE Trip.trip_no=t1.trip_no AND town_from='Rostov'
	GROUP BY date
	UNION ALL
	SELECT '2003-04-01',0
	UNION ALL
	SELECT '2003-04-02',0
	UNION ALL
	SELECT '2003-04-03',0
	UNION ALL
	SELECT '2003-04-04',0
	UNION ALL
	SELECT '2003-04-05',0
	UNION ALL
	SELECT '2003-04-06',0
	UNION ALL
	SELECT '2003-04-07',0
) AS t2
GROUP BY date
```

## 67

https://www.sql-ex.ru/learn_exercises.php?LN=67

```sql
SELECT count(*) 
FROM (
	SELECT TOP 1 WITH TIES count(*) c, town_from, town_to 
	FROM trip
	GROUP BY town_from, town_to
	ORDER BY c desc
) AS t
```

## 68

https://www.sql-ex.ru/learn_exercises.php?LN=68

```sql
SELECT count(*) 
FROM (
	SELECT TOP 1 WITH TIES sum(c) cc, c1, c2 
	FROM (
		SELECT count(*) c, town_from c1, town_to c2 
		FROM trip
		WHERE town_from>=town_to
		GROUP BY town_from, town_to
		UNION ALL
		SELECT count(*) c,town_to, town_from 
		FROM trip
		WHERE town_to>town_from
		GROUP BY town_from, town_to
	) AS t
	GROUP BY c1,c2
	ORDER BY cc desc
) AS tt
```

## 69

https://www.sql-ex.ru/learn_exercises.php?LN=69

```sql
WITH t1 AS (
	SELECT point, date, sum(out) out
	FROM Outcome o 
	GROUP BY point, date
), 
t2 AS (
	SELECT point, date, sum(inc) inc
	FROM Income i
	GROUP BY point, date
),
t3 as (
	SELECT COALESCE(t2.point, t1.point) point, COALESCE(t2.date, t1.date) day, (isnull(t2.inc, 0) - isnull(t1.out, 0)) dsum
	FROM t2 FULL JOIN t1 on t2.point = t1.point and t2.date = t1.date
)
SELECT point, format(day, 'dd/MM/yyyy'), sum(dsum) over(partition by point order by day) ans
FROM t3
```

## 70

https://www.sql-ex.ru/learn_exercises.php?LN=70

```sql
SELECT DISTINCT o.battle
FROM outcomes o LEFT JOIN ships s ON s.name = o.ship LEFT JOIN classes c ON o.ship = c.class OR s.class = c.class
WHERE c.country IS NOT NULL
GROUP BY c.country, o.battle
HAVING COUNT(o.ship) >= 3
```

## 71

https://www.sql-ex.ru/learn_exercises.php?LN=71

```sql
SELECT p.maker
FROM product p LEFT JOIN pc ON pc.model = p.model
WHERE p.type = 'PC'
GROUP BY p.maker
HAVING COUNT(p.model) = COUNT(pc.model)
```

## 72

https://www.sql-ex.ru/learn_exercises.php?LN=72

```sql
SELECT TOP 1 WITH TIES name, c3 
FROM passenger JOIN (
	SELECT c1, max(c3) c3 
	FROM (
		SELECT pass_in_trip.ID_psg c1, Trip.ID_comp c2, count(*) c3 
		FROM pass_in_trip JOIN trip on trip.trip_no=pass_in_trip.trip_no
		GROUP BY pass_in_trip.ID_psg, Trip.ID_comp
	) AS t
	GROUP BY c1
	HAVING count(*)=1
) as tt ON ID_psg=c1
ORDER BY c3 desc
```

## 73

https://www.sql-ex.ru/learn_exercises.php?LN=73

```sql
SELECT distinct country, b.name
FROM Classes c, Battles b
EXCEPT (
	SELECT country, battle
	FROM Outcomes o
	LEFT JOIN Ships s ON s.name = o.ship
	LEFT JOIN Classes c ON c.class = s.class or o.ship = c.class
	WHERE country IS NOT null
	GROUP BY country, battle
)
```

## 74

https://www.sql-ex.ru/learn_exercises.php?LN=74

```sql
SELECT c.country, c.class
FROM classes c
WHERE UPPER(c.country) = 'RUSSIA' AND EXISTS (
	SELECT c.country, c.class
	FROM classes c
	WHERE UPPER(c.country) = 'RUSSIA' 
)
UNION ALL
SELECT c.country, c.class
FROM classes c
WHERE NOT EXISTS (
	SELECT c.country, c.class
	FROM classes c
	WHERE UPPER(c.country) = 'RUSSIA' 
)
```

## 75

https://www.sql-ex.ru/learn_exercises.php?LN=75

```sql
SELECT maker, max(l.price), max(pc.price), max(pr.price)
FROM laptop l 
RIGHT JOIN product p on l.model = p.model 
LEFT JOIN pc on pc.model = p.model 
LEFT JOIN printer pr on p.model = pr.model
WHERE maker in (
	SELECT maker 
	FROM product 
	WHERE model in (
		SELECT model 
		FROM pc 
		WHERE price is not null 
		UNION ALL
		SELECT model 
		FROM printer 
		WHERE price is not null 
		UNION ALL
		SELECT model 
		FROM laptop 
		WHERE price is not null
	)
) GROUP BY maker
```

## 76

https://www.sql-ex.ru/learn_exercises.php?LN=76

```sql
WITH t1 as (
	SELECT row_number() over(partition by pt.id_psg, place order by date) c1, 
	CASE 
	WHEN time_out > time_in 
	THEN (datediff(mi, time_out, dateadd(day, 1, time_in))) 
	ELSE datediff(mi, time_out, time_in) end c2, pt.id_psg, p.name
	FROM pass_in_trip pt inner join trip t on pt.trip_no = t.trip_no
	INNER JOIN passenger p on pt.id_psg = p.id_psg
)
SELECT max(name), sum(c2) 
FROM t1
GROUP BY id_psg
HAVING max(c1) = 1
```

## 77

https://www.sql-ex.ru/learn_exercises.php?LN=77

```sql
WITH t1 as (
	SELECT count(distinct t.trip_no) c1, date c2
	FROM Trip t INNER JOIN pass_in_trip pt on pt.trip_no = t.trip_no
	WHERE town_from = 'Rostov'
	GROUP BY date
)
SELECT c1, c2 
FROM t1
WHERE c1 = (
	SELECT max(c1) 
	FROM t1
)
```

## 78

https://www.sql-ex.ru/learn_exercises.php?LN=78

```sql
SELECT name, REPLACE(CONVERT(CHAR(12), DATEADD(m, DATEDIFF(m,0,date),0), 102),'.','-') AS first_day, REPLACE(CONVERT(CHAR(12), DATEADD(s,-1,DATEADD(m, DATEDIFF(m,0,date)+1,0)), 102),'.','-') AS last_day
FROM Battles
```

## 79

https://www.sql-ex.ru/learn_exercises.php?LN=79

```sql
SELECT Passenger.name, A.minutes
FROM (
	SELECT P.ID_psg,
	SUM((DATEDIFF(minute, time_out, time_in) + 1440)%1440) AS minutes,
	MAX(SUM((DATEDIFF(minute, time_out, time_in) + 1440)%1440)) OVER() AS MaxMinutes
	FROM Pass_in_trip P JOIN
	Trip AS T ON P.trip_no = T.trip_no
	GROUP BY P.ID_psg
) AS A JOIN
Passenger ON Passenger.ID_psg = A.ID_psg
WHERE A.minutes = A.MaxMinutes
```

## 80

https://www.sql-ex.ru/learn_exercises.php?LN=80

```sql
SELECT DISTINCT maker
FROM product
WHERE maker NOT IN (
	SELECT maker
	FROM product
	WHERE type='PC' AND model NOT IN (
		SELECT model
		FROM PC)
)
```

## 81

https://www.sql-ex.ru/learn_exercises.php?LN=81

```sql
SELECT O.*
FROM outcome O
INNER JOIN (
	SELECT TOP 1 WITH TIES YEAR(date) AS Y, MONTH(date) AS M, SUM(out) AS ALL_TOTAL
FROM outcome
GROUP BY YEAR(date), MONTH(date)
ORDER BY ALL_TOTAL DESC
) R ON YEAR(O.date) = R.Y AND MONTH(O.date) = R.M
```

## 82

https://www.sql-ex.ru/learn_exercises.php?LN=82

```sql
WITH CTE(code,price,number)
AS (
	SELECT PC.code,PC.price, number= ROW_NUMBER() OVER (ORDER BY PC.code)
	FROM PC
)
SELECT CTE.code, AVG(C.price)
FROM CTE
JOIN CTE C ON (C.number-CTE.number)<6 AND (C.number-CTE.number)> =0
GROUP BY CTE.number,CTE.code
HAVING COUNT(CTE.number)=6
```

## 83

https://www.sql-ex.ru/learn_exercises.php?LN=83

```sql
SELECT name
FROM Ships AS s JOIN Classes AS cl1 ON s.class = cl1.class
WHERE
CASE WHEN numGuns = 8 THEN 1 ELSE 0 END +
CASE WHEN bore = 15 THEN 1 ELSE 0 END +
CASE WHEN displacement = 32000 THEN 1 ELSE 0 END +
CASE WHEN type = 'bb' THEN 1 ELSE 0 END +
CASE WHEN launched = 1915 THEN 1 ELSE 0 END +
CASE WHEN s.class = 'Kongo' THEN 1 ELSE 0 END +
CASE WHEN country = 'USA' THEN 1 ELSE 0 END > = 4
```

## 84

https://www.sql-ex.ru/learn_exercises.php?LN=84

```sql
SELECT C.name, A.N_1_10, A.N_11_21, A.N_21_30
FROM (
	SELECT T.ID_comp,
	SUM(CASE WHEN DAY(P.date) < 11 THEN 1 ELSE 0 END) AS N_1_10,
	SUM(CASE WHEN (DAY(P.date) > 10 AND DAY(P.date) < 21) THEN 1 ELSE 0 END) AS N_11_21,
	SUM(CASE WHEN DAY(P.date) > 20 THEN 1 ELSE 0 END) AS N_21_30
	FROM Trip AS T JOIN
	Pass_in_trip AS P ON T.trip_no = P.trip_no AND CONVERT(char(6), P.date, 112) = '200304'
	GROUP BY T.ID_comp
) AS A JOIN
Company AS C ON A.ID_comp = C.ID_comp
```

## 85

https://www.sql-ex.ru/learn_exercises.php?LN=85

```sql
SELECT maker
FROM product where type = 'printer'
EXCEPT (
	SELECT maker 
	FROM product 
	WHERE type != 'printer'
)
UNION 
(
SELECT maker
FROM product 
WHERE type = 'pc'
GROUP BY maker
HAVING count(*) >= 3
EXCEPT 
SELECT maker 
FROM product 
WHERE type != 'pc'
)
```

## 86

https://www.sql-ex.ru/learn_exercises.php?LN=86

```sql
SELECT maker,
CASE count(distinct type) when 2 then MIN(type) + '/' + MAX(type)
WHEN 1 
THEN MAX(type)
WHEN 3 
THEN 'Laptop/PC/Printer' END
FROM Product
GROUP BY maker
```

## 87

https://www.sql-ex.ru/learn_exercises.php?LN=87

```sql
SELECT DISTINCT name, COUNT(town_to) Qty
FROM Trip tr JOIN Pass_in_trip pit ON tr.trip_no = pit.trip_no JOIN Passenger psg ON pit.ID_psg = psg.ID_psg
WHERE town_to = 'Moscow' AND pit.ID_psg NOT IN(SELECT DISTINCT ID_psg
FROM Trip tr JOIN Pass_in_trip pit ON tr.trip_no = pit.trip_no
WHERE date+time_out = (
	SELECT MIN (date+time_out)
	FROM Trip tr1 JOIN Pass_in_trip pit1 ON tr1.trip_no = pit1.trip_no
	WHERE pit.ID_psg = pit1.ID_psg
) AND town_from = 'Moscow')
GROUP BY pit.ID_psg, name
HAVING COUNT(town_to) > 1
```

## 88

https://www.sql-ex.ru/learn_exercises.php?LN=88

```sql
SELECT (
	SELECT name 
	FROM Passenger 
	WHERE ID_psg = B.ID_psg
) AS name, B.trip_Qty, (	
	SELECT name 
	FROM Company 
	WHERE ID_comp = B.ID_comp
) AS Company
FROM (
	SELECT P.ID_psg, MIN(T.ID_comp) AS ID_comp, COUNT(*) AS trip_Qty, MAX(COUNT(*)) OVER() AS Max_Qty
	FROM Pass_in_trip AS P JOIN Trip AS T ON P.trip_no = T.trip_no
	GROUP BY P.ID_psg
	HAVING MIN(T.ID_comp) = MAX(T.ID_comp)
) AS B
WHERE B.trip_Qty = B.Max_Qty
```

## 89

https://www.sql-ex.ru/learn_exercises.php?LN=89

```sql
SELECT Maker , count(distinct model) Qty 
FROM Product
GROUP BY maker
HAVING COUNT(distinct model) > = ALL (
	SELECT COUNT(distinct model) 
	FROM Product
	GROUP BY maker
)
OR COUNT(distinct model) <= ALL (
	SELECT count(distinct model) 
	FROM Product
	GROUP BY maker
)
```

## 90

https://www.sql-ex.ru/learn_exercises.php?LN=90

```sql
WITH t1 as (
	SELECT row_number() over(order by model) c1, model
	FROM product
),
t2 as (
	SELECT row_number() over(order by model DESC) c1, model
	FROM product
) 
SELECT * 
FROM product
WHERE model not in (
	SELECT model
	FROM t1 
	WHERE c1 <= 3
	UNION
	SELECT model 
	FROM t2 where c1 <= 3
)
```

## 91

https://www.sql-ex.ru/learn_exercises.php?LN=91

```sql
SELECT CAST(sum(c2)/count(c2) as decimal(6, 2))
FROM (
	SELECT distinct q_name, sum(cast(isnull(b_vol, 0) as decimal(6, 2))) c2
	FROM utq LEFT JOIN utb on utq.q_id = utb.b_q_id
	GROUP BY q_name
)t1
```

## 92

https://www.sql-ex.ru/learn_exercises.php?LN=92

```sql
SELECT distinct q_name 
FROM utq
WHERE q_id in (
	SELECT distinct t1.b_q_id
	FROM (
		SELECT b_q_id
		FROM utb
		GROUP BY b_q_id having(sum(b_vol)) = 765)t1
		WHERE t1.b_q_id not in (
			SELECT b_q_id 
			FROM utb 
			WHERE b_v_id in (
				SELECT b_v_id 
				FROM utb 
				GROUP BY b_v_id 
				HAVING sum(b_vol) < 255))
)
```

## 93

https://www.sql-ex.ru/learn_exercises.php?LN=93

```sql
SELECT name, sum(ans)
FROM (
	SELECT distinct id_comp, pt.trip_no, date, time_in, time_out, --id_psg,
	CASE WHEN time_out > time_in then datediff(mi, time_out, time_in + 1) 
	ELSE datediff(mi, time_out, time_in) END ans
	FROM pass_in_trip pt INNER JOIN trip t on pt.trip_no = t.trip_no
)t1 INNER JOIN company c on t1.id_comp = c.id_comp
GROUP BY name
```

## 94

https://www.sql-ex.ru/learn_exercises.php?LN=94

```sql
WITH t1 as (
	SELECT date, COUNT(distinct pt.trip_no) c1, MAX(COUNT(distinct pt.trip_no)) over() c2
	FROM pass_in_trip pt LEFT JOIN trip t on pt.trip_no = t.trip_no
	WHERE town_from = 'Rostov'
	GROUP BY date
),
t2 as (
	SELECT top 1 (date), numday=1
	FROM t1 
	WHERE c1 = c2
	ORDER BY date
	UNION ALL
	SELECT date + 1, numday+1 
	FROM t2 
	WHERE numday <= 6
)
SELECT t2.date, isnull(c1, 0)
FROM t2 LEFT JOIN t1 on t2.date = t1.date
```

## 95

https://www.sql-ex.ru/learn_exercises.php?LN=95

```sql
WITH t1 as (
	SELECT id_comp, row_number() over(partition by id_comp, date, t.trip_no order by date) c1, row_number() over(partition by id_comp, plane order by plane) c2, row_number() over(partition by id_comp, id_psg order by id_psg) c3
	FROM pass_in_trip pt INNER JOIN trip t on pt.trip_no = t.trip_no
)
SELECT (
	SELECT name 
	FROM Company 
	WHERE id_comp = t1.id_comp
) a1,
SUM(
	CASE 
	WHEN c1 = 1 
	THEN 1 
	ELSE 0 
	END
) a2,
SUM(
	CASE
	WHEN c2 = 1 
	THEN 1 
	ELSE 0 
	END
) a3,
SUM(
	CASE 
	WHEN c3 = 1 
	THEN 1 
	ELSE 0 
	END
) a4,
COUNT(c3) a5
FROM t1
GROUP BY id_comp
```

## 96

https://www.sql-ex.ru/learn_exercises.php?LN=96

```sql
WITH t1 as (
	SELECT v_name, b_q_id q
	FROM utv, utb
	WHERE v_color = 'r' and v_id in (
		SELECT b_v_id 
		FROM utb 
		GROUP BY b_v_id 
		HAVING count(*) > 1
	) and v_id = b_v_id
),
t2 as (
	SELECT b_q_id q 
	FROM utb b, utv v 
	WHERE v.v_color = 'b' and v.v_id = b.b_v_id
)
SELECT distinct t1.v_name
FROM t2, t1
WHERE t2.q = t1.q
```

## 97

https://www.sql-ex.ru/learn_exercises.php?LN=97

```sql
WITH t1 as (
	SELECT code, spec, data,  row_number() over(partition by code order by data) c1
	FROM (
		SELECT code, cast(speed as real) speed, 
		CAST(ram as real) ram, 
		CAST(price as real) price, 
		CAST(screen as real) screen 
		FROM Laptop
	)tt1
	unpivot(data for spec in (speed, ram, price, screen))tt2
),
t3 as (
	SELECT t1.code
	FROM t1, t1 as t2 
	WHERE t1.code = t2.code and t1.c1 < 4 and t1.c1+1 = t2.c1 and t1.data * 2 <= t2.data
	GROUP BY t1.code
	HAVING count(*) = 3
)
SELECT code, speed, ram, price, screen
FROM Laptop 
WHERE code in (
	SELECT * 
	FROM t3
)
```

## 98

https://www.sql-ex.ru/learn_exercises.php?LN=98

```sql
WITH t1 as (
	SELECT code, (speed | ram) c1
	FROM pc
),
t2 as (
	SELECT code, c1, cast(c1 as int) a1, cast('' as varchar(max)) a2
	FROM t1
	UNION ALL
	SELECT code, c1, t2.a1 / 2, cast(t2.a1 % 2 as varchar(35)) + t2.a2
	FROM t2 
	WHERE t2.a1 > 0
),
t3 as (
	SELECT * 
	FROM t2 
	WHERE a1 = 0 and a2 like '%1111%'
)
SELECT pc.code, speed, ram
FROM pc, t3 
WHERE pc.code = t3.code
```

## 99

https://www.sql-ex.ru/learn_exercises.php?LN=99

```sql
WITH t1 as (
	SELECT point, date, date nD
	FROM Income_o io
	UNION ALL
	SELECT point, date, nD + 1
	FROM t1 
	WHERE nD in (
		SELECT date 
		FROM Outcome_o oo 
		WHERE point = t1.point
	) or datepart(dw, nD) = 1
),
t2 as (
SELECT point, date, max(nD) mD
FROM t1 
GROUP BY point, date
)
SELECT point, date D, iif(date = mD, date, mD) ans
FROM t2
```

## 100

https://www.sql-ex.ru/learn_exercises.php?LN=100

```sql
WITH t1 as (
	SELECT row_number() over(partition by date order by code) c1, *
	FROM outcome
),
t2 as (
	SELECT row_number() over(partition by date order by code) c1, *
	FROM income
)
SELECT coalesce(t2.date, t1.date) a1, coalesce(t2.c1, t1.c1) a2, t2.point, inc, t1.point, out
FROM t2 FULL JOIN t1 on t2.date = t1.date and t2.c1 = t1.c1
```
