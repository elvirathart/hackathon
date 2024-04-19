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
<span style="color:red";>Het betere volk kan deze stap overslaan:</span><br />
__Installeer Docker Desktop__
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
