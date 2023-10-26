# LAB | SQL Joins

#This lab allows you to practice and apply the concepts and techniques taught in class. 

#Before this starting this lab, you should have learnt about:

- #SELECT, FROM, ORDER BY, LIMIT, WHERE, GROUP BY, and HAVING clauses. DISTINCT, AS keywords.
- #Built-in SQL functions such as COUNT, MAX, MIN, AVG, ROUND, DATEDIFF, or DATE_FORMAT.
- #Using JOIN to combine data from multiple tables.
 

## Introduction



## Challenge - Joining on multiple tables

#Write SQL queries to perform the following tasks using the Sakila database:


##1. List the number of films per category.
# Retrieve the store ID, city, and country for each store.
##3.  Calculate the total revenue generated by each store in dollars.
#4.  Determine the average running time of films for each category.


#**Bonus**:

#5.  Identify the film categories with the longest average running time.
#6.  Display the top 10 most frequently rented movies in descending order.
#7. Determine if "Academy Dinosaur" can be rented from Store 1.
#8. Provide a list of all distinct film titles, along with their availability status in the inventory. Include a column indicating whether each title is 'Available' or 'NOT available.' Note that there are 42 titles that are not in the inventory, and this information can be obtained using a `CASE` statement combined with `IFNULL`."

#Here are some tips to help you successfully complete the lab:

#***Tip 1***: This lab involves joins with multiple tables, which can be challenging. Take your time and follow the steps we discussed in class:

-# Make sure you understand the relationships between the tables in the database. This will help you determine which tables to join and which columns to use in your joins.
- #Identify a common column for both tables to use in the `ON` section of the join. If there isn't a common column, you may need to add another table with a common column.
-# Decide which table you want to use as the left table (immediately after `FROM`) and which will be the right table (immediately after `JOIN`).
- #Use table aliases to make your queries easier to read and understand. This is especially important when working with multiple tables.
- #Write the query

#***Tip 2***: Break down the problem into smaller, more manageable parts. For example, you might start by writing a query to retrieve data from just two tables before adding additional tables to the join. Test your queries as you go, and check the output carefully to make sure it matches what you expect. This process takes time, so be patient and go step by step to build your query incrementally.


##1. List the number of films per category.
SELECT *
FROM film;
SELECT *
FROM category;

#1List the number of films per category.
SELECT c.name AS category_name, COUNT(f.film_id) AS film_count
FROM category c
LEFT JOIN film_category fc ON c.category_id = fc.category_id
LEFT JOIN film f 
ON fc.film_id = f.film_id
GROUP BY c.name
ORDER BY film_count DESC;

#2 Retrieve the store ID, city, and country for each store.
SELECT s.store_id, c.city, cou.country
FROM sakila.store s
JOIN sakila.address a
USING(address_id)
JOIN sakila.city c
USING(city_id)
JOIN sakila.country cou
USING(country_id)

#3Calculate the total revenue generated by each store in dollars.
SELECT store.store_id, CONCAT(
