Controlling the world with JavaScript and Arduino
=================================================

Intro
-----
* Skynet will be written in JavaScript. 
* JavaScript er overalt, nettleserens programmeringsspråk
* Nå også på serversiden med node.js
* Sist men ikke minst kan det også brukes til å kontrollere roboter etc.

Meg / formål
------------
* Hvem er jeg? Hva jeg vil at dere skal få ut av det?
* Hva er IoT og Arduino?
* Hvordan komme igang
* Gi inspirasjon til å starte egne prosjekter
* En haug av teknologier, jeg får ikke tid til å presentere alle

automatr demo?
--------------

Internet of things
------------------
* Kan bygges inn i hjemmet, hvitevarer sier ifra at de må fikses eller fylles på
* Kontrollere lamper, ovner, kaffetralter you name it.
* Sensorer for temperatur, lys, gasser, nærhet, alkohol
Lys, motorer, servoer og releer som lar deg kontrollere andre elektriske enheter som ovner, lys, kaffetraktere.

Arduino
-------
* En åpen kildekode prototypingplattform for designere, kunstnere, utviklere som vil ha en billig og enkel måte å komme igang med prosjekter som involverer styring og sensing med elektronikk
* Finnes nå i ulike varianter, for min del startet jeg med en Arduino Uno som er den som er i starter kit. 
* Microcontroller board basert på ATmega328, 14 digitale input /output pinner, 6 kan brukes til PWM (Pulse Width Modulation), 6 analoge input (Brukes gjerne til sensorer 0-1023).
* Kan motta og sende mellom 0 - 5v styrke, det er slik man f.eks. tar imot verdier fra en sennsor.
* Opererer med voltstyrke på 5V.

Enter johnny five & Raspberry pi
--------------------------------
* Arduino kan kobles til internett ved å bruke Ethernet eller Wi-Fi skjold
* Jeg kicka på muligheten til å skrive JavaScript mot Arduino med Johnny Five, men for å kunne gjøre det må man ha en server som kan kjøre mot Arduinoen, her kommer Raspberry Pi inn for min del.

johnny five
-----------
* node.js basert JavaScript bibliotek som bruker Firmata protokollen til å kommunisere med Arduino
* Connectivity, nettskyen rett inn i applikasjonen. 

Raspberry pi
------------
* Startet som et prosjekt for å små og billige datamaskiner som barn kunne lære å programmere
* ARM basert microcomputer med skjermkort, nettverksport, USB-porter etc.
* Kjører linux operativsystem
* Kan fint kjører en web-server, og ulike applikasjoner
* Jeg bruker OS'et Debian, linux basert open source

Firebase
--------
* Skybasert API-tjeneste for real-time sync og lagring. Ganske så romslig gratis-avtale. Svært enkelt å komme i gang med. API'er for Node og 
* AngularFire (eget bibliotek for Angular)
* Firebase, et alternativ er å bruke noe slikt som MQTT

Demo
----
* Vise workflow, kode på Windows box, overføre filer med WinSCP, kjøre kode etc via SSH

Oppsummering
------------
Ikke bare en gutte / jenteromsgreie
Avhengig av et godt økosystem og gode tjenester rundt for at de skal bli bra
Nettskyen er en opplagt plattform for kommunikasjon
Anbefaler Simen Sommerfeldt sin artikkel på utbrudd, http://blogg.bouvet.no/2014/03/07/the-internet-of-things-keiserens-nye-wearables/