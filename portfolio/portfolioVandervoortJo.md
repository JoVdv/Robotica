---
title: "Portfolio Vandervoort Jo"
student: "Vandervoort Jo"
class: "Afstandsonderwijs"
date: "10/01/2026"
---

# 1. Kennisblog Robotica  

## 1.1 Beschrijving Fanuc Education cell  
Ik heb mijn opdrachten op de Fanuc ER-4iA met R-30iB Mate Plus Controller
uitgevoerd.  
Het is een 6-axis robot die een maximale last van 4kg kan dragen en een reach
heeft van 550mm. De controller is bedienbaar met knoppen en of met touchscreen.  

## 1.2 Veiligheidsinstructies
Een robot is en blijft een gevaarlijke machine. Hierdoor moeten we bepaalde
richtlijnen in acht nemen om veilig te werken en programmeren van de robot.  
De voornaamste richtlijnen zijn:  
- Mechanische werken of handelingen binenn de cel voer je steeds uit met 
een uitgeschakelde robot.  
- Programmeren doe je steeds met de Teach Pendant buiten de cel.  
- Testen van een robot programma doe je steeds in T1 en met gesloten celdeur.  
- Automatisch laten lopen van de robot gebeurt steeds met gesloten celdeur met
goedkeuring van de verantwoordelijke.  

## 1.3 Basisbegrippen robotica  

### 1.3.1 Coördinatensystemen  
Binnen robotica gebruiken we verschillende coördinatensystemen. Deze systemen
hebben elk hun eigen nut en toepassing. De volgende coördinaten systemen worden
bij Fanuc toegepast:  
- Worldframe  
- Toolframe (UTOOL)  
- Userframe (UFRAME)  
- Joint coördinaten  

De coördinaatsystemen uitgezonderd de joint coördinaten werken met het
XYZ-assenstels. Het coördinaten systeem UFRAME is bij mijn toepassing het
interessantste om toe te passen. Je kan meerde UFRAMES instellen. Bij dit
systeem gaan we als gebruiker zelf de positie van ons assenstelsel definiëren.
Dit heeft als voordeel dat we het frame op een voor ons gunstige positie
kunnen plaatsen. Ook is het mogelijk om in het programma verloop van userframe
te wisselen. Dit geeft dat ook al zijn 2 of meerdere werkgebieden van de robot
op een bizarre hoek van elkaar geplaatst we toch binnen elk werkgebied met een
logische XYZ kunnen werken. 

### 1.3.2 Singulariteit


## 1.4 Opstarten van de robot.  
De roborcontroller is voorzien van een keuzeschakelaar. Deze keuze schakelaar
heeft de volgende standen:  
- Auto  
- T1  
- T2  
Elke stand is een andere bedrijfsmodi van de robot. Zo dient de automode enkel 
gebruikt te worden na setup en met een gesloten celdeur. De standen T1 en T2
zijn teststanden. Zo is bij T1 de snelheid van de robot beperkt tot 250mm/s en
de voornaamste modus om het robotprogramma te testen. De modus T2 is de snelheid
niet beperkt en moet steeds met bedachtzaamheid gebruikt worden.  

Het opstarten van de robot gaan we doen door de Teach Pendant te nemen, de 
keuzeschakelaar op de controller in stand 1 te plaatsen en hoofdschakelaar 
in stand "On" te plaatsen.  

## 1.5 Bedienen van de robot.  

### 1.5.1 Basis info
Het bedienen van de robot gebeurt aan de hand van de Teach Pendant. Deze Teach
Pendant kan men bedienen met de knoppen en of met touchscreen. 
Teach Pendants zijn ook steeds uitgerust met dodemansknoppen op de achterzijde.
Dit zijn knoppen die gebruikt worden bij industriële installaties die men 
handmatig gaat bedienen met de kans op een gevaarlijke situatie. Deze knoppen 
hebben 3 standen waarbij de knop in een middenstand moet gehouden moet worden 
om vrijgave van de assen te verkrijgen.  

![Teach Pendant](images/controller.png){width=50%}

\pagebreak

### 1.5.2 Handmatig bedrijf
Voor het handmatig bedienen van de robot moet men steeds de volgende stappen 
doorlopen:  
- Het houden van de dodemansknop in de middenstand voor hele tijd we de robot
bedienen.  
- Bedien "RESET".  
- Houdt de knop "SHIFT" ingedrukt tijdens het bedienen van de robot.  
- Met de rechtse knoppen rij kan je nu de robot bedienen. 

### 1.5.3 Automatisch bedrijf






# 2. Gemaakte oefeningen  

## 2.1 Opdracht Loops  
Er zijn 2 velden, één veld heeft 10 cilinders. Het andere veld is leeg.
De cilinders zijn gerangschikt in een driehoek vormig patroon.  
De opzet is om met de robot in een loop programma cilinders van veld 1 naar
veld 2 te verplaatsen.  

# 3. Gevolgde cursussen/video's  

# 4. Datasheets & Fabrikanten informatie  
[Fanuc brochure Educational Package](https://hogeschoolpxl.sharepoint.com/:b:/r/sites/ROBOTICA/Gedeelde%20documenten/FANUC/Fanuc_Robot/Robot/Fanuc_EducationalCell/FanucBrochure_robots-educational-package-brochure-en.pdf?csf=1&web=1&e=CQSN9p)  
[Fanuc Educational Cell Manual](https://hogeschoolpxl.sharepoint.com/:b:/r/sites/ROBOTICA/Gedeelde%20documenten/FANUC/Fanuc_Robot/Robot/Fanuc_EducationalCell/FANUC%20Educational%20Cell%20Manual.pdf?csf=1&web=1&e=wcypbv)  

