# Opdrachten SELECTS
Geef elke keer de correcte query voor volgende vragen:

- Alle customers vanuit Los Angelas<br> 
```sql
SELECT * from customers where city LIKE 'Los%'
```

- Alle customers die eigenaar zijn<br>
```sql
SELECT * from customers where job_title like 'owner'
```
 
- Alle customers vanuit state *WA*<br>
```sql
SELECT * FROM customers WHERE state_province = 'WA'
```

- Alle customers gesorteerd op voornaam aflopend<br>
```sql
SELECT * FROM customers ORDER BY first_name DESC
```

- Alle customers gesorteerd op achternaam oplopend<br>
```sql
SELECT * FROM customers ORDER BY last_name ASC
```

- De volledige naam van alle customer in volgend formaat: Voornaam_Achternaam. De titel van de kolom moet full_name zijn <br>
```sql
SELECT concat(first_name , '_', last_name) as 'full_name' from customers
```

- Alle producten van de categorie Beverages<br>
```sql
SELECT * FROM products WHERE category = 'Beverages' 
```

- Alle producten waar de standaard kost duurder is dan 5 euro<br>
```sql
SELECT * FROM products WHERE category = 'Beverages'
```

- Alle producten waar de lijst prijs lager is dan 20 euro of 20 euro is<br>
```sql
SELECT * FROM products WHERE list_price <= 20
```

- De prijs van alle producten als er 70% korting zou zijn op de standaard kost<br>
```sql
SELECT product_name, ((list_price / 100) * 30) AS 'price'  FROM products
```

- Alle producten die een T in de code hebben moeten worden geselecteerd<br>
```sql
SELECT * FROM products WHERE product_code LIKE '%T%' 
```
<br>

- Alle producten met een S in de code moeten een tag krijgen: smart andere producten moeten als tag dumb krijgen <br>
``` sql
SELECT product_code, 
CASE 
  WHEN product_code LIKE '%S%' then 'smart' £
  ELSE 'dumb' 
END AS 'tag' FROM   products
```

- Alle producten waar de de herbestel hoeveelheid geen even getal is
```sql
SELECT * FROM products WHERE minimum_reorder_quantity % 2 = 0 
```

- Alle producten waar de herbestel hoeveelheid geen veelvoud is van 5
```sql
SELECT * FROM products WHERE minimum_reorder_quantity % 5 != 0
```

- Alle orders die niet betaald zijn (Een order is niet betaald als het gee paid_date heeft)
```sql
SELECT * FROM orders WHERE paid_date IS null
```

- Alle orders die op 5 april 2006 geplaats zijn
```sql
SELECT * FROM orders WHERE order_date like '2006-04-05%'
```

- Alle orders die al verstuurd zijn (Een order is verstuurd als het een shipped_date heeft)
```sql
SELECT * FROM orders WHERE shipped_date IS NOT NULL
```

- Alle orders met een shipping cost van tussen de 6 en 10
```sql
SELECT * FROM orders WHERE shipping_fee > 6 AND shipping_fee < 10
```

- Alle orders die verstuurd worden naar een provincie waar de code van eindigt op L
```sql
SELECT * FROM orders WHERE ship_state_province LIKE '%L'
```

- Alle suppliers met een a in hun voornaam en die als functie Sales Manager of Marketing Manager hebben
```sql
SELECT * FROM suppliers WHERE first_name LIKE '%a%' AND (job_title = 'Sales Manager' OR job_title = 'Marketing Manager')
```