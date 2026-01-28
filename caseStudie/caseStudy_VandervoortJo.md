---
title: "Case Study Vandervoort Jo"
student: "Vandervoort Jo"
class: "Afstandsonderwijs"
date: "29/01/2026"
---

# 1 Theoretisch kader
## 1.1 Wat is robotica?
Robotica is de algemene studie van robots en geautomatiseerde systemen. 
Dit gaat over meerdere disciplines.

## 1.2 Wat is industriële robotica
Industriële robotica is een gebied binnen robotica dat zich richt op robots 
in productieomgevingen.

### 1.2.1 Types van robots en cobots
Er zijn verschillende types van robots. De meest voornaamste zijn:
- 6-assige robotarm
- Scara
- Delta
- Humanoïde
- Mobiele platformen
- ...

6-assige robotarmen ziet men vaak terug in de automotive industrie. Deze zijn
breed inzetbaar en kunnen in veel verschillende posities draaien. 
Ook hebben deze een breed spectrum aan grijpers en andere end-effectors. Zo kom
je ze tegen van een simpele pick and place, lasrobotten, ... .

SCARA‑robots zijn relatief eenvoudige robots. Ik heb ze onder andere gezien 
bij toepassingen zoals het aanbrengen van Loctite op flenzen.

Enkele bekende merken zijn:
- Kuka
- Fanuc
- ABB
- Yaskawa

## 1.3 Veiligheid in industriële robotica

Een robot is en blijft een gevaarlijke machine. Hierdoor moeten we bepaalde
richtlijnen in acht nemen om veilig te werken en programmeren van de robot.  
De voornaamste richtlijnen zijn:  
- Mechanische werken of handelingen binnen de cel voer je steeds uit met 
een uitgeschakelde robot.  
- Programmeren doe je steeds met de Teach Pendant buiten de cel.  
- Testen van een robot programma doe je steeds in T1 en met gesloten celdeur.  
- Automatisch laten lopen van de robot gebeurt steeds met gesloten celdeur met
goedkeuring van de verantwoordelijke.  

# 2 Casestudie - De robotapplicatie
https://www.youtube.com/watch?v=s6xhUYdGHCA

## 2.1 Keuze en beschrijving
Ik heb deze robotapplicatie gekozen omdat het een eenvoudige pick en place
robotcel is maar toch iets wat je in de industrie tegen komt. 

Er wordt ruw materiaal aangeleverd via een transportband. Indien de beladingsplaats
van het bewerkingscentrum leeg is, wordt de mal beladen door de robot. Het deel
gaat bewerkt worden in de machine en de beladingstafel draait naar de
bewerkingszijde. Hierdoor kan de 2de mal ontladen worden. Dit deel 
wordt op een andere transportband geplaatst en afgevoerd.

## 2.2 Technische evaluatie

### 2.2.1 Opbouw
**Mechanisch**  
Het is een 6-assige robotarm van Fanuc. De robot heeft een payload van 7kg en
een reach van 911mm. De grijper die er op zit is een persluchtgestuurde radiale
grijper. In vertraagd afspelen van het filmpje zie je duidelijk dat de robot met 
zijn grijper in de pasgaten gaat en dan zijn grijper open stuurt waardoor het 
deel geklemd wordt.
De delen worden in een bewerkingscentrum in een beladingsplaats op een mal ontladen 
en beladen. De beladingsplaats bevindt zich in het bewerkingscentrum aan de 
afgeschermde zijde van de bewerkingszone. Daar bevindt zich één zijde van de 
beladingstafel. Op elke zijde van de beladingstafel bevindt zich een mal die het 
deel gaat klemmen. De producten worden op een transportband aan- en afgevoerd. 
Deze transportbanden worden waarschijnlijk door mensen beladen.

**Elektrisch**  
Elektrisch zien we vooral twee sensoren op het einde en het begin van de
transportbanden. Dit ter controle van aanwezigheid van een deel. Zo gaat er
vermoedelijk ook sensoren op de gripper zitten die de positie van de gripper
gaan controleren, alsook de aanwezigheid van een deel. Verder zie ik
dat er ook steeds bij het nemen van een ruw deel de robot een foto neemt. Dus
hier komt een visioncamera van pas. Dit is ook zeer nodig aangezien ze niet
werken met een transportband met fixeringspennen of dergelijke.
Hierbij gaat voor het opnemen van het deel een foto genomen worden.
Deze foto wordt vergeleken met een referentiefoto. Bij het vergelijken van 
de twee foto's gaat de hoekverdraaiingen, de langs- en dwarsverplaatsing berekend worden. 
Hierop gaat de robot zijn opname positie wijzigen voor het nemen van het ruwe
deel.

**Pneumatisch**  
Het enige pneumatische deel lijkt mij de grijper van de robot. Dit lijkt mij
een type dat wordt ontwikkeld door het merk Schunk. Dit is een pneumatische
radiale grijper, die vaak een fail-safe heeft waarbij het stuk wordt geklemd 
bij het ontbreken van perslucht.
Wat mogelijk nog pneumatisch kan zijn is de aanlegcontrole van het deel in 
de mal van het bewerkingscentrum. 

**Hydraulisch**  
De klemfunctie van de mal lijkt mij hydraulisch. Dit wordt meestal zo uitgevoerd
wegens de hoge klemkracht. Ook is het mogelijk om in de beladingspositie een klep
open te sturen. Dan het deel te klemmen en de klep te sluiten als het deel
geklemd is. Dan vormt dit een gesloten circuit en hoeft men geen sturing in het
bewerkingsdeel te voorzien. En wordt er een draaiend (zwak) punt weg gehaald.

### 2.2.2 Risico analyse
De robotcel lijkt al in een verder stadium van de opbouw te zijn aangezien er
al een hekwerk aanwezig is. Toch zijn er bepaalde kleine zaken die men moet
adresseren voor het volledig in productie nemen van de robotcel. Ik merk drie 
posities op waar een operator de werkruimte van de robot kan betreden zonder 
detectie of beveiliging.

Locatie 1: Dit is bij de deur van de bewerkingszijde het bewerkingscentrum. Dit
is duidelijk zichtbaar op moment 0:52 van het filmpje. Ik raad hier aan om een
stuk hekwerk bij te plaatsen zodoende dit dicht is.

Locatie 2: Is op moment 0:35 zichtbaar. Hier zie je dat de operator tot aan de
robot kan reiken als hij met zijn arm verder door het gat zou gaan. Hier kan men
perfect een lichtscherm bijplaatsen of een soort van "flap". 

Locatie 3: Is op 0:38. Hier kan men via een opening naast het bedieningspaneel 
nog steeds de robot bereiken. Hier raad ik ook aan om een hekwerk bij te plaatsen.

Verder lijkt het dat de benodigde beveiligingen aangebracht zijn. Zo zouden de
deuren enkel geopend kunnen worden bij een stilstaande robot, die niet meer in
automatisch bedrijf is. 

### 2.2.3 Pseudo-programmatie

```
startUpCheck();

go Home;

Switch Case {

Case geen deel grijper + BW beladen flag{
    gripper open;
    go wacht positie;
    wait -> positie verschuiving ruw deel vision;

    go positie ruw deel;
    gripper toe;
    go tussen positie;
    go beladeplaats;
    gripper open;
    go tussenpositie;
    go home;
    }

Case ruw deel grijper + BW beladen flag{
    
    go tussen positie;
    go beladeplaats;
    gripper open;
    go tussenpositie;
    go home;

    }

Case grijper leeg + BW ontladen flag{
    open gripper;
    go tussen positie;
    go beladepositie;
    close gripper;
    go tussen positie;
    if geen deel ontlaad pos(
    go ontlaadpositie transportband;
    )
    open gripper;
    go tussen positie;
    go home;


    }

Case bewerkt deel grijper{
    go tussen positie;
    if geen deel ontlaad pos(
    go ontlaadpositie transportband;
    )
    open gripper;
    go tussen positie;
    go home;

}

```

## 2.3 Haalbaarheid en kritische reflectie
Ik denk wel dat ik in staat ben om dergelijke installatie in werkelijkheid tot stand
te brengen. Aangezien ik al enkele jaren werkzaam ben in het werkveld. Ook ben
ik met al de technieken in verschillende mate al in aanraking gekomen.

Dit lijkt mij al een goed uitgewerkte installatie. Zo zou je misschien in plaats
van de visioncamera, een transportband met pennen kunnen voorzien. Dit is een
mechanische positionering van het ruwe deel. Wat de visioncamera overbodig maakt 
en ook het robotprogramma kan vereenvoudigd worden. In de toekomst kan men 
misschien deze cel mee in een grotere installatie opnemen. Wat het mogelijk maakt voor 
automatische belading van de ruwe delen.

