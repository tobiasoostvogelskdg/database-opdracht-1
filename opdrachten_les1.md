# Opdrachten Setup

Voor de opdrachten gaan we gebruik maken van de *northwind* database. Een demo db van Microsoft

- Maak een nieuwe db aan om je Combell
    - Geef deze de naam: `jeinitialen`northwind (aan elkaar)
- Download de zip file Northwind.zip van Canvas ([canvas.kdg.be](https://canvas.kdg.be/courses/43251/modules/items/901199))
- Importeer de structuur (northwind.sql)
- Importeer de data (northwind_data.sql)

Je mag voor deze opdrachten kiezen of je gebruik maakt van PHPMyAdmin of een andere client.

# Opdrachten SELECTS

Geef elke keer de correcte query voor volgende vragen:

- Alle customers vanuit Los Angelas
- Alle customers die eigenaar zijn
- Alle customers vanuit state *WA*
- Alle customers gesorteerd op voornaam aflopend
- Alle customers gesorteerd op achternaam oplopend
- De volledige naam van alle customer in volgend formaat: *Voornaam_Achternaam*. De titel van de kolom moet **full_name** zijn
- Alle producten van de categorie *Beverages*
- Alle producten waar de standaard kost duurder is dan 5 euro
- Alle producten waar de lijst prijs lager is dan 20 euro of 20 euro is
- De prijs van alle producten als er 70% korting zou zijn op de standaard kost
- Alle producten die een *T* in de code hebben moeten worden geselecteerd
- Alle producten met een *S* in de code moeten een tag krijgen: *smart* andere producten moeten als tag *dumb* krijgen
- Alle producten waar de de herbestel hoeveelheid geen even getal is
- Alle producten waar de herbestel hoeveelheid geen veelvoud is van 5
- Alle orders die niet betaald zijn (Een order is niet betaald als het gee *paid_date* heeft)
- Alle orders die op 5 april 2006 geplaats zijn
- Alle orders die al verstuurd zijn (Een order is verstuurd als het een *shipped_date* heeft)
- Alle orders met een shipping cost van tussen de 6 en 10
- Alle orders die verstuurd worden naar een provincie waar de code van eindigt op *L*
- Alle suppliers met een *a* in hun voornaam en die als functie *Sales Manager* of *Markerting Manager* hebben

# Opdrachten UPDATES

Geef elke keer de correcte query voor volgende vragen.
Maak ook telkens een SELECT query om je resultaat te controleren.

- Alle met een standaard kost lager dan *10* moeten bij discontinued een true waarde krijgen
- Alle producten met een *C* in hun code moeten als minimum herbestelhoeveelheid + 5 bij het huidige aantal krijgen
- *Jan Kotas* & *Andrew Cencini* zijn van bedrijf veranderd en werken nu voor *Google* pas dit aan voor de employees
- *Steven Thorpe* heeft zijn naam veranderd naar *Stivie* pas dit aan voor de employees.
- De stad *Boise* is van naam veranderd en heet nu *Boston* pas dit aan voor de orders
- Voor elk order moet de taxes exact 21% zijn van de shipping fee. Uiteraard moeten we ingeven dat we 21% berekenen in de tax_rate kolom
- Voer het thuis telefoonnummer: *123-456-789* toe voor *Sato Naoki* bij de suppliers
- Voeg voor elke customer een web pagina toe met volgende url: *https://achternaam-northwind.com*
- Alle customers die in de state *WA* of *CA* wonen moeten worden aangepast zodat de *state_province* *WMCA* wordt
- Bij *shippers* staat bedrijf A nu op naam van: *Kevin Van Oevelen*

# Opdrachten DELETES

Voer voor je aan deze opdracht begint volgende query uit:

```sql
SET @OLD_FOREIGN_KEY_CHECKS=@@FOREIGN_KEY_CHECKS, FOREIGN_KEY_CHECKS=0;
```

Geef elke keer de correcte query voor volgende vragen:

- Alle producten die als eenheid ergens *jars* bevatten mogen worden verwijderd
- Alle producten van de categorie *Oil* mogen worden verwijderd
- Alle producten met een van deze codes mogen worden verwijderd: *NWTS-8* , *NWTCM-40* , *NWTP-56* , *NWTDFN-74*
- Alle orders ouder dan *maart 2006* mogen worden verwijderd
- Alle orders verstuurd naar *Milwaukee* mogen worden verwijderd
- *Company B* mag worden verwijderd bij de shippers
- Alle *Marketing Manager*'s mogen worden verwijderd uit de suppliers
- Alle privileges mogen worden verwijderd
- Alle *order_details* met een even *unit_price* mogen worden verwijderd op voorwaarde dat ze status 2 hebben of een *purchase_order_id* hebben
- Alle invoices met een datum die voor *03/04/2006* ligt mogen worden verwijderd

#  Opdrachten INSERTS

- Voeg een customer toe met eigen verzonnen gegevens (Alle kolommen moeten een waarde hebben)
- Voeg een customer toe met volgende gegevens:
  - Naam: Ronny Ronssens
  - Titel: Developer
- Voeg 2 suppliers toe met één query. Volgende gegevens
  - Bedrijf 1:
    - Bedrijf: GeNx
    - Naam: Sam Serrien
    - Web Pagina: genx.be
  - Bedrijf 2:
    - Bedrijf: Meteor
    - Naam: Alessandro Aussems
    - Web Pagina: meteor.be
- Voeg een product toe met volgende gegevens:
    - Code: APPLE-13
    - Naam: Iphone 13
    - Standaard prijs: 899,99
    - Lijst prijs: 950.52
    - Categorie: Iphones
- Voeg een order toe met volgende gegevens:
    - Datum: Huidige datum
    - Adres: Selesianenlaan Hoboken
    - Tax: 120.45 euro
    - Betaald met: Payconiq
