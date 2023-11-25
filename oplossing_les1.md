# Opdrachten SELECTS
Geef elke keer de correcte query voor volgende vragen:

- Alle customers vanuit Los Angelas<br>
  querry: ```SELECT * from customers where city LIKE 'Los%'``` <br>
  antwoord: 2 lijntjes

- Alle customers die eigenaar zijn<br>
  querry:  ```SELECT * from customers where job_title like 'owner'```<br>
  antwoord: 6 lijntjes 
 
- Alle customers vanuit state *WA*<br>
  querry: ```SELECT * FROM customers WHERE state_province = 'WA'```
  antwoord: 2 lijntjes

- Alle customers gesorteerd op voornaam aflopend
  querry: ```SELECT * FROM customers ORDER BY first_name DESC```
  antwoord: Eerste persoon = Thomas Axen

- Alle customers gesorteerd op achternaam oplopend
  querry: ```SELECT * FROM customers ORDER BY last_name ASC```
  antwoord: Eerste persoon = Elizabeth Andersen