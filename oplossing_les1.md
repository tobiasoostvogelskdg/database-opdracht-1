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

# Opdrachten UPDATES
Geef elke keer de correcte query voor volgende vragen. Maak ook telkens een SELECT query om je resultaat te controleren.

- Alle producten met een standaard kost lager dan 10 moeten bij discontinued een true waarde krijgen
```sql
UPDATE products SET discontinued = true WHERE standard_cost < 10
SELECT * FROM products WHERE standard_cost < 10
```

- Alle producten met een C in hun code moeten als minimum herbestelhoeveelheid + 5 bij het huidige aantal krijgen
```sql
UPDATE products SET minimum_reorder_quantity = minimum_reorder_quantity + 5 WHERE product_code LIKE '%C%'
SELECT * FROM products WHERE product_code LIKE '%C%'
```

- Jan Kotas & Andrew Cencini zijn van bedrijf veranderd en werken nu voor Google pas dit aan voor de employees
```sql
UPDATE employees SET company = 'Google' WHERE first_name LIKE 'Jan' OR first_name LIKE 'Andrew'
SELECT first_name, company FROM employees WHERE first_name LIKE 'Jan' OR first_name LIKE 'Andrew'
```

- Steven Thorpe heeft zijn naam veranderd naar Stivie pas dit aan voor de employees.
```sql
UPDATE employees SET first_name = 'Stevie' WHERE last_name LIKE 'Thorpe'
SELECT first_name, last_name FROM employees WHERE last_name LIKE 'Thorpe'
```

- De stad Boise is van naam veranderd en heet nu Boston pas dit aan voor de orders
```sql
UPDATE orders SET ship_city = 'Boston' WHERE ship_city LIKE 'Boise'
SELECT ship_city FROM orders WHERE ship_city LIKE 'B%'
```

- Voor elk order moet de taxes exact 21% zijn van de shipping fee. Uiteraard moeten we ingeven dat we 21% berekenen in de tax_rate kolom
```sql
UPDATE orders SET tax_rate = 21
SELECT tax_rate FROM orders 
UPDATE orders SET taxes = (shipping_fee / 100) * tax_rate
SELECT taxes FROM orders
```

- Voer het thuis telefoonnummer: 123-456-789 toe voor Sato Naoki bij de suppliers
```sql
UPDATE suppliers SET home_phone = '123-456-789' WHERE first_name LIKE 'Naoki'
SELECT first_name, home_phone FROM suppliers WHERE first_name LIKE 'Naoki'
```

- Voeg voor elke customer een web pagina toe met volgende url: https://achternaam-northwind.com
```sql
UPDATE customers SET web_page = concat('https://', last_name, '-northwind.com');
SELECT first_name, last_name, web_page FROM customers
```

- Alle customers die in de state WA of CA wonen moeten worden aangepast zodat de state_province WMCA wordt
```sql
UPDATE customers SET state_province = 'WMCA' WHERE state_province LIKE 'WA' OR state_province LIKE 'CA'
SELECT state_province FROM customers WHERE state_province LIKE 'WA' OR state_province LIKE 'CA' OR state_province LIKE 'WMCA'
```

- Bij shippers staat bedrijf A nu op naam van: Kevin Van Oevelen
```sql
UPDATE shippers SET first_name = 'Kevin', last_name = 'Van Oevelen' WHERE company LIKE '%A'
SELECT * FROM shippers WHERE company LIKE '%A'
```

# Opdrachten UPDATES
Geef elke keer de correcte query voor volgende vragen:
- Alle producten die als eenheid ergens jars bevatten mogen worden verwijderd
```sql
DELETE FROM products WHERE quantity_per_unit LIKE '%jars%'
```

- Alle producten van de categorie Oil mogen worden verwijderd
```sql
DELETE FROM products WHERE category LIKE 'Oil'
```

- Alle producten met een van deze codes mogen worden verwijderd: NWTS-8 , NWTCM-40 , NWTP-56 , NWTDFN-74
```sql
DELETE FROM products WHERE product_code LIKE 'NWTS-8' OR product_code LIKE 'NWTCM-40' OR product_code LIKE 'NWTP-56' OR product_code LIKE 'NWTDFN-74'
```

- Alle orders ouder dan maart 2006 mogen worden verwijderd
```sql
DELETE FROM orders WHERE order_date LIKE '2006-03%' OR order_date LIKE '2006-02%' OR order_date LIKE '2006-01%'
```

- Alle orders verstuurd naar Milwaukee mogen worden verwijderd
```sql
DELETE FROM orders WHERE ship_city LIKE 'Milwaukee'
```

- Company B mag worden verwijderd bij de shippers
```sql
DELETE FROM shippers WHERE company LIKE '%B'
```

- Alle Marketing Manager's mogen worden verwijderd uit de suppliers
```sql
DELETE FROM suppliers WHERE job_title LIKE 'Marketing Manager'
```

- Alle privileges mogen worden verwijderd
```sql
DELETE FROM privileges
```

- Alle order_details met een even unit_price mogen worden verwijderd op voorwaarde dat ze status 2 hebben of een purchase_order_id hebben
```sql
DELETE FROM order_details WHERE unit_price % 2 = 0 AND (status_id = 2 OR purchase_order_id IS NOT NULL)
```

- Alle invoices met een datum die voor 03/04/2006 ligt mogen worden verwijderd
```sql
DELETE FROM invoices WHERE invoice_date < '2006-04-03'
```

# Opdrachten INSERTS

- Voeg een customer toe met eigen verzonnen gegevens (Alle kolommen moeten een waarde hebben)
```sql
INSERT INTO customers (company, last_name, first_name, email_address, job_title, business_phone, home_phone, mobile_phone, fax_number, address, city, state_province, zip_postal_code, country_region, web_page, notes, attachments) VALUES ('kdg', 'Oostvogels', 'Tobias', 'tobias.oostvogels@student.kdg.be', 'student', 0123, 4567, 8910, 1112, 'Westdoor', 'Wuustwezel', 'Antwerp', 2990, 'BE', 'portfilio.tobias.oostvogels.nxtmediatech.eu', 'test', 'no')
```

- Voeg een customer toe met volgende gegevens: 
```sql
INSERT INTO customers (first_name, last_name, job_title) VALUES ('Ronny', 'Ronssens', 'Developer')
```

- Voeg 2 suppliers toe met één query. Volgende gegevens 
```sql
INSERT INTO suppliers (company, first_name, last_name, web_page) VALUES ('GeNx', 'Sam', 'Serrien', 'genx.be'), ('Meteor', 'Alessandro', 'Aussems', 'meteor.be')
```

- Voeg een product toe met volgende gegevens: 
```sql
INSERT INTO products (product_code, product_name, standard_cost, list_price, category) VALUES ('APPLE-13', 'Iphone 13', 899.99, 950.52, 'Iphones')
```

- Voeg een order toe met volgende gegevens: 
```sql
INSERT INTO orders (order_date, ship_address, taxes, payment_type) VALUES ('2023-11-26', 'Selesianenlaan Hoboken', 120.45, 'Payconiq')
```
