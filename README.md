# SQLBOLT-Hernandez
Solutions for the SQLBolt and SQLPD exercises
## SQLBolt

### SQL Review: Simple SELECT Queries

#### Task 1
List all the Canadian cities and their populations
```
SELECT City, Population 
FROM north_american_cities
WHERE Country LIKE "Canada";
```

#### Task 2
Order all the cities in the United States by their latitude from north to south
```
SELECT City, Latitude
FROM north_american_cities
WHERE Country LIKE "United States"
ORDER BY Latitude DESC;
```

#### Task 3
List all the cities west of Chicago, ordered from west to east
```
SELECT City, Longitude
FROM north_american_cities
WHERE Longitude < (SELECT Longitude
    FROM north_american_cities
    WHERE City LIKE "Chicago")
ORDER BY Longitude ASC;
```

#### Task 4
List the two largest cities in Mexico (by population)
```
SELECT City, Population
FROM north_american_cities
WHERE Country="Mexico"
ORDER BY Population Desc
LIMIT 2;
```

#### Task 5
List the third and fourth largest cities (by population) in the United States and their population
```
SELECT City, Population
FROM north_american_cities
WHERE Country="United States"
ORDER BY Population Desc
LIMIT 2 OFFSET 2;
```

### SQL Lesson 12: Order of execution of a Query

#### Task 1
Find the number of movies each director has directed
```
SELECT Director, Count(*) AS "Movies Directed"
FROM movies
GROUP BY Director;
```

#### Task 2
Find the total domestic and international sales that can be attributed to each director
```
SELECT Director, SUM(Domestic_sales + International_sales) AS "Total Sales"
FROM movies
INNER JOIN Boxoffice
ON movies.Id=Boxoffice.Movie_id
GROUP BY Director;
```
## SQLPD
### Task 1
An illegal site's servers were seized in a recept operation. Please submit all users' details.
```
SELECT *
FROM users;
```

### Task 2
A hacked site subscribers' details have surfaced on a darknet forum. Please submit all subscribers' details.
```
SELECT *
FROM subscribers
```

### Task 3
An illegal site's servers were seized in a recent operation. Please submit all users family names and access times' details.
```
SELECT FamilyName, AccessTime
FROM users
```

### Task 4
An illegal site's servers were seized in a recent operation. Please submit all users access times and number of downloads' details.
```
SELECT AccessTime, NumberOfDownloads
FROM users
```

### Task 5
A hacked site subscribers' details have surfaced on a darknet forum. Please submit all subscribers subscribed since dates' details. Please make sure there are no duplicates.
```
SELECT DISTINCT SubscribedSince
FROM subscribers
```

### Task 6
A mailing list of an illegal online service was sent to the SQLPD hot-line. Please submit all entries' details sorted by number of password changes in ascending order.
```
SELECT *
FROM mailing_list
ORDER BY PasswordChanges ASC
```

### Task 7
A mailing list of an illegal online service was sent to the SQLPD hot-line. Please submit all entries' details sorted by join dates in descending order.
```
SELECT *
FROM mailing_list
ORDER BY Joined DESC
```

### Task 8
A mailing list of an illegal online service was sent to the SQLPD hot-line. Please submit all records number of promotions sent, given names and last names' details sorted by number of promotions sent in descending order. Please make sure there are no duplicates.
```
SELECT DISTINCT PromotionsSent, GivenName, LastName
FROM mailing_list
ORDER BY PromotionsSent DESC
```

### Task 9
An illegal site's servers were seized in a recent operation. Please submit all users last access times and last names' details sorted by last access times in ascending order and then by last names in ascending order.
```
SELECT LastAccess, LastName
FROM users
ORDER BY LastAccess ASC, LastName ASC
```

### Task 10
A hacked site members' details have surfaced on a darknet forum. Please submit the top 20 members' details when sorted by member since dates in ascending order and then by addresses in descending order.
```
SELECT *
FROM members
ORDER BY MemberSince ASC, Address DESC
LIMIT 20
```
