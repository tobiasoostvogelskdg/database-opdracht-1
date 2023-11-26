# Opdrachten SELECTS
Geef elke keer de correcte query voor volgende vragen:

- Alle customers vanuit Los Angelas<br>
  query: ```SELECT * from customers where city LIKE 'Los%'``` <br>

- Alle customers die eigenaar zijn<br>
  query:  ```SELECT * from customers where job_title like 'owner'```<br>
 
- Alle customers vanuit state *WA*<br>
  query: ```SELECT * FROM customers WHERE state_province = 'WA'```<br>

- Alle customers gesorteerd op voornaam aflopend<br>
  query: ```SELECT * FROM customers ORDER BY first_name DESC```<br>

- Alle customers gesorteerd op achternaam oplopend<br>
  query: ```SELECT * FROM customers ORDER BY last_name ASC```<br>

- De volledige naam van alle customer in volgend formaat: Voornaam_Achternaam. De titel van de kolom moet full_name zijn <br>
  query: ```SELECT concat(first_name , '_', last_name) as 'full_name' from customers``` <br>

- Alle producten van de categorie Beverages<br>
  query: ```Alle producten van de categorie Beverages```<br>

- Alle producten waar de standaard kost duurder is dan 5 euro<br>
  query: ```SELECT * FROM products WHERE category = 'Beverages'```

- Alle producten waar de lijst prijs lager is dan 20 euro of 20 euro is<br>
  query: ```SELECT * FROM products WHERE list_price <= 20```

- De prijs van alle producten als er 70% korting zou zijn op de standaard kost<br>
  query: ```SELECT product_name, ((list_price / 100) * 30) AS 'price'  FROM products```<br

- Alle producten die een T in de code hebben moeten worden geselecteerd<br>
  query: ```SELECT * FROM products WHERE product_code LIKE '%T%' ```<br>

- Alle producten met een S in de code moeten een tag krijgen: smart andere producten moeten als tag dumb krijgen <br>
  query: 
```
  SELECT product_code, 
  CASE 
    WHEN product_code LIKE '%S%' then 'smart' £
    ELSE 'dumb' 
  END AS 'tag' FROM   products
```sql
