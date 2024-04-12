---
layout: cv
title: Hackathon | SmartQA
output: 
    pdf_document: default
---

![SmartQA-logo alt >](./images/Logo_SmartQA.png)

<br />

# Hackathon
containers containers containers

<br />

## Wat gaan we doen?
Spelen met containers en databases!
<br /><br />

Eerst gaan we containers maken, met behulp van onderstaande handleiding, google en ChatGPT.
<br />
<!-- 
Er zijn verschillende opties qua containers en databases.
<br />

Nadat we een werkende container met database hebben: 
<br />
Verkennen van 'test isolation'. Verzin een test die zo omgaat met de data dat het een eigen omgeving / database nodig heeft.
-->
<br /> <br />


## Lxd container opzetten

<br />

__snap install lxd__
<br /><br />
__lxd init__
<br />
Alle vragen op default.
<br /><br />
__lxd --version__
<br />
Versie 5.20?
<br /><br />
__lxc launch ubuntu:22.04 [naam container]__
<br />
Maak een container aan met bijvoorbeeld Ubuntu 22.04 en geef de container een naam.
<br /><br />
__lxc exec [naam container] --sudo --user ubuntu --login__
<br />
Om in te loggen op een container.
Nu zit je in de container en heb je een volledige Ubuntu omgeving!
<br /><br />
__exit__
<br />
Om weer uit de container te gaan.
<br /><br />
__lxc list__
<br />
Bekijk de status van je container(s).
<br /><br />
__lxc --help__
<br />
Bekijk de help pagina voor meer commando's.
<br />
<br />

## Database installeren

__Vraag ChatGpt: How to install MariaDB on Ubuntu__
<br />
Als het goed is ga je dan ook iets van mysql-secure-installation draaien
<br />
<br />
__Verwijder test users etc.__
<br /><br />
__Maak een database aan__
<br /><br />
__Maak een nieuwe user aan__
<br /><br />
__Geef de nieuwe user alle (of enkele) permissies op de aangemaakte database__
<br /><br />
__Create een table__
<br /><br />
__Insert data in de table__
<br /><br />
__Select data uit de table__
<br />
Ook met where clause
<br /><br />
__Delete een row__
<br />
Ook met where clause
<br /><br />
__Maak nog een table aan en zorg dat 1 kolom een verwijzing heeft naar de eerste table__
<br />
Bijvoorbeeld een ID in table 1 heeft een kolom met dezelfde waarde in table 2.
<br /><br />
__Doe nu een query__
<br />
m.b.v. een join (inner, left, right), zodat je data uit beide tabellen selecteert.
Dit kun je voor nog veel meer tabellen doen!
<br />
<br />


<!-- 
***Languages***

<br />

## Work Experience



`may 2022 - jul 2022`
__Keana__

### Test Automation Engineer

Supported team of Keana, development of web based TMS by creating an end-to-end automation test using Playwright. 

- Define test cases and flow 
- Determine coverage 
- BDD using testing-library 
- Accessibility testing 
- Suggest test-ability improvements to developers 
- Tool selection: proposed to use Playwright over Cypress. <br />As POC executed part of the test in both Playwright and Cypress to show the advantages in this project 
<br /><br />

## Education

__Bachelor of Design, Fashion__
`2008 - 2011`

### Rietveld Academie, Amsterdam



 -->
