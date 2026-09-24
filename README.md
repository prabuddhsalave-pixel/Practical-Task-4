# Practical-Task-4
# QuickBite MySQL Challenge

**Concepts used:** `CREATE DATABASE`, `CREATE TABLE`, `INSERT`, `SELECT`, `WHERE`, `AND`, `OR`, `NOT`, `BETWEEN`, `IN`, `LIKE`, `DISTINCT`, aliases, `ORDER BY`, `LIMIT`, `AVG()`

> Note: Saara data fictional classroom/demo data hai.

## Setup

```sql
CREATE DATABASE quickbite;
USE quickbite;

CREATE TABLE restaurants (
  restaurant_id INT PRIMARY KEY,
  restaurant_name VARCHAR(100),
  cuisine VARCHAR(50),
  city VARCHAR(50),
  rating DOUBLE,
  avg_order_value DOUBLE,
  orders_count INT,
  delivery_fee DOUBLE,
  est_delivery_time INT,
  owner_name VARCHAR(100),
  brand VARCHAR(100)
);
```

30 records ka `INSERT` script `quickbite_queries.sql` file mein hai.

---

## Level 1 - Food Detective

**Task 1:** Rating greater than 4.5

```sql
SELECT * FROM restaurants WHERE rating > 4.5;
```

**Task 2:** Average order value less than 300

```sql
SELECT * FROM restaurants WHERE avg_order_value < 300;
```

**Task 3:** Restaurants in Pune

```sql
SELECT * FROM restaurants WHERE city = 'Pune';
```

**Task 4:** More than 20,000 orders

```sql
SELECT * FROM restaurants WHERE orders_count > 20000;
```

**Task 5:** Delivery time greater than 40 minutes

```sql
SELECT * FROM restaurants WHERE est_delivery_time > 40;
```

**Task 6:** Rating between 4.2 and 4.7

```sql
SELECT * FROM restaurants WHERE rating BETWEEN 4.2 AND 4.7;
```

**Task 7:** South Indian, Italian or Biryani cuisine (using IN)

```sql
SELECT * FROM restaurants
WHERE cuisine IN ('South Indian', 'Italian', 'Biryani');
```

**Task 8:** Owner name contains 'Patil'

```sql
SELECT * FROM restaurants WHERE owner_name LIKE '%Patil%';
```

**Task 9:** Brand matches restaurant name

```sql
SELECT * FROM restaurants WHERE brand = restaurant_name;
```

**Task 10:** Delivery fee less than 30

```sql
SELECT * FROM restaurants WHERE delivery_fee < 30;
```

---

## Level 2 - Recommendation Team

**Task 11:** Top 5 restaurants by orders

```sql
SELECT * FROM restaurants ORDER BY orders_count DESC LIMIT 5;
```

**Task 12:** 5 restaurants with lowest average order value

```sql
SELECT * FROM restaurants ORDER BY avg_order_value ASC LIMIT 5;
```

**Task 13:** Highest rating to lowest rating

```sql
SELECT * FROM restaurants ORDER BY rating DESC;
```

**Task 14:** Unique cuisines

```sql
SELECT DISTINCT cuisine FROM restaurants;
```

**Task 15:** Aliases `Restaurant_Name` and `Customer_Rating`

```sql
SELECT restaurant_name AS Restaurant_Name,
       rating AS Customer_Rating
FROM restaurants;
```

**Task 16:** Restaurant name, owner and brand only

```sql
SELECT restaurant_name, owner_name, brand FROM restaurants;
```

**Task 17:** Sort by city, then rating descending

```sql
SELECT * FROM restaurants ORDER BY city ASC, rating DESC;
```

**Task 18:** 5 highest-rated restaurants with more than 10,000 orders

```sql
SELECT * FROM restaurants
WHERE orders_count > 10000
ORDER BY rating DESC
LIMIT 5;
```

**Task 19:** 3 most ordered restaurants in Pune

```sql
SELECT * FROM restaurants
WHERE city = 'Pune'
ORDER BY orders_count DESC
LIMIT 3;
```

**Task 20:** 5 restaurants with highest delivery fee

```sql
SELECT * FROM restaurants ORDER BY delivery_fee DESC LIMIT 5;
```

---

## Level 3 - Find the Hidden Restaurants

**Task 21:** Names starting with S

```sql
SELECT * FROM restaurants WHERE restaurant_name LIKE 'S%';
```

**Task 22:** Names ending with 'House'

```sql
SELECT * FROM restaurants WHERE restaurant_name LIKE '%House';
```

**Task 23:** Names containing 'Cafe'

```sql
SELECT * FROM restaurants WHERE restaurant_name LIKE '%Cafe%';
```

**Task 24:** Cuisines containing 'Indian'

```sql
SELECT * FROM restaurants WHERE cuisine LIKE '%Indian%';
```

**Task 25:** Names having exactly 5 characters

```sql
SELECT * FROM restaurants WHERE CHAR_LENGTH(restaurant_name) = 5;
```

**Task 26:** Owner name contains 'Raj'

```sql
SELECT * FROM restaurants WHERE owner_name LIKE '%Raj%';
```

**Task 27:** Brand contains 'Foods'

```sql
SELECT * FROM restaurants WHERE brand LIKE '%Foods%';
```

**Task 28:** City starts with 'P'

```sql
SELECT * FROM restaurants WHERE city LIKE 'P%';
```

---

## Level 4 - Business Team

**Task 29:** Average order value > 400 AND rating > 4.5

```sql
SELECT * FROM restaurants
WHERE avg_order_value > 400 AND rating > 4.5;
```

**Task 30:** Orders > 20,000 OR rating > 4.7

```sql
SELECT * FROM restaurants
WHERE orders_count > 20000 OR rating > 4.7;
```

**Task 31:** Restaurants NOT in Pune

```sql
SELECT * FROM restaurants WHERE NOT city = 'Pune';
```

**Task 32:** Delivery time between 25 and 40 minutes

```sql
SELECT * FROM restaurants WHERE est_delivery_time BETWEEN 25 AND 40;
```

**Task 33:** Average order value between 300 and 600

```sql
SELECT * FROM restaurants WHERE avg_order_value BETWEEN 300 AND 600;
```

**Task 34:** Pune or Mumbai

```sql
SELECT * FROM restaurants WHERE city IN ('Pune', 'Mumbai');
```

**Task 35:** Fast Food with more than 20,000 orders

```sql
SELECT * FROM restaurants
WHERE cuisine = 'Fast Food' AND orders_count > 20000;
```

**Task 36:** Rating > 4.5 and delivery fee below 40

```sql
SELECT * FROM restaurants
WHERE rating > 4.5 AND delivery_fee < 40;
```

**Task 37:** Bengaluru with more than 10,000 orders

```sql
SELECT * FROM restaurants
WHERE city = 'Bengaluru' AND orders_count > 10000;
```

**Task 38:** Owner name is not 'Rahul Jain'

```sql
SELECT * FROM restaurants WHERE owner_name <> 'Rahul Jain';
```

---

## Level 5 - Boss Challenges

**Challenge 1 - Hidden Gem:** Rating above 4.5 but fewer than 10,000 orders

```sql
SELECT * FROM restaurants
WHERE rating > 4.5 AND orders_count < 10000;
```

**Challenge 2 - Cheap & Popular:** Average order value below 300 and orders above 20,000

```sql
SELECT * FROM restaurants
WHERE avg_order_value < 300 AND orders_count > 20000;
```

**Challenge 3 - Fast Delivery:** Delivery time below 30 minutes and rating above 4.3

```sql
SELECT * FROM restaurants
WHERE est_delivery_time < 30 AND rating > 4.3;
```

**Challenge 4 - Trending Restaurants:** 3 most ordered restaurants from Mumbai

```sql
SELECT * FROM restaurants
WHERE city = 'Mumbai'
ORDER BY orders_count DESC
LIMIT 3;
```

**Challenge 5 - Premium Restaurants:** Average order value greater than overall average

```sql
SELECT * FROM restaurants
WHERE avg_order_value > (SELECT AVG(avg_order_value) FROM restaurants);
```

**Challenge 6 - City Spotlight:** Pune restaurants sorted by orders (high to low)

```sql
SELECT * FROM restaurants
WHERE city = 'Pune'
ORDER BY orders_count DESC;
```

**Challenge 7 - Cuisine Report:** South Indian restaurants with restaurant, city, rating and average order value

```sql
SELECT restaurant_name, city, rating, avg_order_value
FROM restaurants
WHERE cuisine = 'South Indian';
```

**Challenge 8 - High Value Partners:** Average order value above 500 and rating at least 4.5

```sql
SELECT * FROM restaurants
WHERE avg_order_value > 500 AND rating >= 4.5;
```

---

## Final Boss - CEO Challenge

Strongest restaurant partners: rating > 4.4, orders > 10,000, average order value between 300 and 700. Sorted by orders (high to low), top 5 only.

```sql
SELECT restaurant_name, cuisine, city, rating, avg_order_value,
       orders_count, delivery_fee, owner_name, brand
FROM restaurants
WHERE rating > 4.4
  AND orders_count > 10000
  AND avg_order_value BETWEEN 300 AND 700
ORDER BY orders_count DESC
LIMIT 5;
```
