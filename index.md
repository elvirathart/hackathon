---
layout: cv
title: Hackathon | SmartQA
output: 
    pdf_document: default
---

![SmartQA-logo alt >](./images/Logo_SmartQA.png)

<br />

# Hackathon - 25 april

<br />
## Wat gaan we doen?
<br />
__Spelen met containers en databases!__
<br />
De opzet van deze hackathon is dit keer iets anders. Het is misschien iets minder hackathon, iets meer workshop. We leveren wat meer handleiding en tips erbij omdat misschien niet iedereen bekend is met het gebruik van containers en databases. Het is eigen keuze in hoeverre je dit wilt volgen.<br />
De bedoeling is om kennis te maken met dit onderwerp, comfortabel worden in het gebruik en weten wat de voor en nadelen zijn – dit door er mee te spelen en uiteindelijk een werkend voorbeeld inclusief tests te bouwen.<br />
<br />
Hieronder de handleiding om je op weg te helpen. Gebruik Google en ChatGPT als je er niet uitkomt.
<br />
<br />

## Basis begrippen
<br />
__Docker__
<br />
Docker is a software platform that allows you to build, test, and deploy applications quickly. Docker packages software into standardized units called containers that have everything the software needs to run including libraries, system tools, code, and runtime.<br />
Docker piggybacks off of features in the Linux kernel to perform its magic. Because of this reliance on the Linux kernel, it's important to note that Docker only runs on Linux.<br />
<br />
__Docker Desktop__
<br />
Having a virtual machine is required on Windows and MacOS if you want to run Linux containers. Basically Docker Desktop is a virtual machine + Graphical user interface with some extra features like the new extensions and running a single-node Kubernetes “cluster” easily. Inside the virtual machine there is Docker CE (Docker Community Edition) daemon.<br />
Keep it in mind when you try to access container IP addresses directly, because the Docker network exists only inside the virtual machine, not on your host. This is also true for local volumes too. The other very important difference is related to the network is that even if you use the host network mode (docker run --net host) it will be the host network of the virtual machine, not your actual physical host.<br />
<br />
__Dockerfile__
<br />
A file (with simple) syntax for defining the steps needed to create an image and run it.<br />
<br />
__Image__
<br />
Read-only template with instructions for creating a Docker container.<br />
Often, an image is based on another image, with some additional customization. You might create your own image or you might only use those created by others and published in a registry. To build your own image, you create a Dockerfile.<br />
<br />
__Container__
<br />
A container is a runnable instance of an image. You can create, start, stop, move or delete a container using the Docker API or cli. You can connect a container to one or more networks, attach storage to it, or even create a new image based on its current state.<br />
<br />
__PostgreSQL__
<br />
PostgreSQL, often simply "Postgres", is an object-relational database management system (ORDBMS) with an emphasis on extensibility and standards-compliance. As a database server, its primary function is to store data, securely and supporting best practices, and retrieve it later, as requested by other software applications, be it those on the same computer or those running on another computer across a network (including the Internet). It can handle workloads ranging from small single-machine applications to large Internet-facing applications with many concurrent users. Recent versions also provide replication of the database itself for security and scalability.<br />
<br />
<br />

## Docker container en Postgres database
<br />
<span style="color:red;">Het betere volk kan deze stap overslaan:</span><br />
__Installeer Docker Desktop__
<br />
[Download Docker Desktop](https://www.docker.com/products/docker-desktop/)
<br />
<br />
__Open je terminal en Docker Desktop__
<br />
<br />
__docker --version__
<br />
Als je geen docker versie terugkrijgt, moet je waarschijnlijk de docker daemon starten. Zoek in de applicatie folder in Finder.<br />
<br />
__brew install postgresql@15__
<br />
Installeer PostgreSQL, bv met Homebrew.<br />
<br />
<span style="color:red;">Vanaf hier voor Linux en Mac:</span><br />
__docker pull postgres__
<br />
Download de laatste versie van Postgres image.<br />
In Docker Desktop, in de sidebar links: klik Images. Hier zie je de postgres image in de lijst verschijnen.<br />
<br />
__docker run -d --name pokemonContainer -p 5432:5432 -e POSTGRES_PASWORD=pass123 postgres__
<br />
<br />
<span style="color:blue;">
__Uitleg command:__
<br />
“-d” flag specifies that the container should execute in the background.<br />
“--name” option assigns the container’s name, i.e., “postgresCont”.<br />
“-p” assigns the port for the container i.e. “5432:5432”.<br />
“-e POSTGRES_PASSWORD” configures the password to be “pass123”.<br />
“postgres” is the official Docker image.<br />
</span>
<br />
<br />
We hebben nu een postgres instance gestart met een container genaamd pokemonContainer.<br />
In Docker Desktop, in sidebar klik Containers. Hier zie je de net aangemaakte container genaamd pokemonContainer in de lijst en of deze wel of niet runt. Zo nodig kun je containers hier ook starten en stoppen. Dit kan ook allemaal in cli, probeer uit:<br />
<br />
__docker ps__
<br />
Controleer dat de net aangemaakte container runt.<br />
__docker stop pokemonContainer__<br />
__docker start pokemonContainer__<br/>
<br />
__docker exec -it pokemonContainer bash__
<br />
-it opent de bash shell in de postgres container (eigenlijk opent bash een bash shell en -ti zorgt voor een interactieve tty). Als het goed is zie je nu iets als:<br />
root@*****:/#<br />
We hebben toegang tot de pokemonContainer en kunnen er nu commands in runnen.<br />
Verschil run en exec: bij run maak je een container en start deze, exec gaat uit van een al gestarte container.<br />
<br />
__psql -h localhost -U postgres__
<br />
Als het goed is zie je nu:<br />
postgres=#<br />
Nu zitten we in de SQL Shell, waar we SQL queries en psql commands kunnen uitvoeren.<br />
<br />
__CREATE DATABASE pokemon;__
<br />
Creëer een database genaamd pokemon_types, als het goed gaat krijg je als feedback CREATE DATABASE.<br />
<br />
__\l__ (=Kleine L) <br />
<br />
Bevestig dat de database bestaat / bekijk alle aangemaakte databases.<br />
<br />
__\c pokemon;__
<br />
Maak connectie met de database. Let op dat je bevestiging krijgt dat je connectie hebt met de database.<br />
__CREATE TABLE pokemon_types(ID INT PRIMARY KEY NOT NULL, NAME TEXT NOT NULL, TYPE TEXT NOT NULL);__
<br />
Maakt een tabel aan met de gewenste kolommen.<br />
<br />
__INSERT INTO pokemon_types VALUES (0001, ‘bulbasaur’, ‘poison’);__
<br />
Insert records in de nieuwe tabel.<br />
<br />
__SELECT * FROM pokemon_types;__
<br />
Zo kun je de data in de tabel terug zien.<br />
<br />
__Voeg nu de volgende rijen toe aan de tabel:__
<br />
Dit kan natuurlijk een voor een met het INSERT INTO command… maar hopelijk ga je wat efficiënter te werk dan dat.<br />
<br />
4, charmander, fire<br />
16, pidgey, flying<br />
25, pikachu, normal<br />
79, slowpoke, psychic<br />
94, gengar, poison<br />
97, hypno, psychic<br />
100, voltorb, electric<br />
118, goldeen, water<br />
157, typhlosion, fire<br />
163, hoothoot, flying<br />
7, squirtle, water<br />
<br />
Geen ervaring met sql? Dan nog wat meer basis:<br />
Pikachu is natuurlijk geen normal type. Update het type van Pikachu ajb met electric.<br />
<br />
Er zijn uiteraard veel andere acties die je kan toepassen op een database.<br />
Speel even, bijvoorbeeld: voeg een extra kolom toe, hernoem de kolom en haal de kolom er bv. weer van af.<br />
<br />
__Klaar met spelen?__
<br />
Hopelijk hebben we nog steeds een database met 12 pokémons en 3 kolommen. Deze hebben we zo nodig voor onze eerste test.<br />
<br />
<br />

## TEST TEST TEST

<br />
__Vals spelen: van elke test is er een voorbeeld__ <br />
<br />

## TEST 1 - database.test.ts

<br />
Gebruik Typescript en Jest.<br />
Schrijf een test die een extra pokémon (2, ‘morpeko’, ‘electric’) toevoegt aan de database en assert dat er nu 13 pokémons in de database staan.<br />
<br />
Vergeet niet (ook handig wanneer je ChatGPT vraagt ;) ):<br />
Jest Typescript unit test<br />
connects to postgres localhost 5432<br />
user postgres<br />
inserts a string/record into table <table name><br />
assert the count is 13<br />
<br />
__npm test -- database.test.ts__
<br />
Draai de test 1x.<br />
<br />
Ga naar je terminal, daar waar je in de container zit en contact hebt met de database pokemon.<br />
__SELECT * FROM pokemon_types;__
<br />
Valt iets op?<br />
<br />
__npm test -- database.test.ts__
<br />
Draai de test een tweede keer. <br />
Breng database eventueel in originele staat door wat je hebt toegevoegd in je test via de cli te deleten.<br />
<br />
De test maakt elke keer gebruik van dezelfde database. Hierdoor is de test onbetrouwbaar of faalt altijd na de eerste run.<br />
<br />
Wij willen:<br />
<br />
<span style="color:blue;">
__Test isolation.__<br />
Net als bij web automation wil je een schone browser context bij elke test zodat dat wat je test, de applicatie of het component ook consistent gedraagt. Dit geldt in het algemeen natuurlijk: alle tests zouden altijd onafhankelijk van elkaar gedraaid moeten worden en dus betrouwbaar slagen.</span><br />
<br />

## TEST 2 - container.test.ts

<br />
In deze test gaan we test isolation toepassen. Hoe? Door gebruik van containers.<br />
<br />
Zet in 1 testfile 5 dezelfde tests. Zorg dat voor elke test een nieuwe container wordt aangemaakt waar je de tabel pokemon_types in creëert en voeg vervolgens pokemon (2, ‘morpeko’, ‘electric’) toe aan de tabel.<br />
Je kan een assert toevoegen, maar we weten eigenlijk al of de testisolation geslaagd is als we bij de tweede ‘test’, na toevoegen van de pokémon, geen melding krijgen van duplicate key.<br />
<br />
Om iets van feedback te krijgen en zien wat er gebeurt tijdens het draaien van de tests is aan te raden om mee te kijken in je terminal (op mac misschien installeren met brew):<br />
__watch docker ps__
<br />
<br />

## TEST 3 - preseed.test.ts

<br />
In Test 1 maakten we gebruik van de instance met een database waar we een tabel in gemaakt hadden die we gevuld hadden met 12 Pokémon.<br />
<br />
In Test 2 hebben we voor elke test een nieuwe instance van de image postgres gemaakt, met database pokemon en een tabel pokemon_types. De tabel begint leeg, pas in de test zelf vullen we deze met 1 Pokémon.<br />
<br />
Voor deze test 3 willen we eerst een instance aanmaken die we gelijk vullen met de database pokemon waarin de tabel pokemon_types staat met de 12 pokémon. Zodat we dit niet in de forEach of in de test zelf hoeven doen.<br />
<br />
Maak een sql bestand met de commands om een database en tabel aan te maken en gelijk te vullen met de values (de 12 pokémon die we eerder ook gebruikt hebben).<br />
<br />
Maak een dockerfile die een postgres image pakt en het sql script kopieert naar /docker-entrypoint-initdb.d/<br />
Dit is deel van de postgres base image entrypoint script dat je image erft van de base image.<br />
(postgres image is ingesteld om alles in de map uit te voeren)<br />
<br />
cd naar de map waar je de bestanden hebt staan<br />
__docker build -t preseeded:latest .__
<br />
Als de build goed ging heb je nu een image aangemaakt genaamd preseeded:latest. Als je wilt kun je nog controleren of je image in de lijst staat:<br />
__docker images__
<br />
<br />
Maak een testfile aan genaamd preseed.test.ts. Maak contact met de preseeded image en schrijf 3 tests waarin je bevestigt dat ‘slowpoke’, ‘gengar’ en ‘typhlosion’ al in de database staan.<br />
<br />
<br />

## OPEN OPDRACHT - Bouw een frontendje bij je databaseje

<br />
Maak een nodejs webserver waar pokemon list bv antwoord geeft op select*from pokemon_types. Stop dat antwoord in een html body, maak er mooi lijstje van. <br />
Voer andere acties uit als stop DB, start een andere, refresh, gebruik andere data. Probeer preseeded.
<br />
<br />
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
