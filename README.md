Denne guide forklarer et Pick&Place program med integreret vision, og  hele opsætningen af følgende enheder:

- Sick InspectorP62.
- UR3e.
-TIA Portal.


Følgende steps er blevet lavet:

1) Opsæt profinet forbindelse mellem Siemens PLC --> UR3e --> Sick InspectorP62.
 - Profinet forbindelsen melllem vores PLC og UR3e kan oprettes ved hjælp af min anden guide. (https://github.com/Nicolai-Abildgaard/Profinet-guide-UR)


2) Opsætning af Sick InspectorP62 i .
 - Tilslut kameraet til 24 V/DC. 
 - Download Sick AppManager.
 - Åben nu programmet, og følgende vindue kommer frem: <img width="1023" height="800" alt="Sick Appspace 1" src="https://github.com/user-attachments/assets/32e4acd8-8fcc-4020-86e4-2062bc47b657" />
 - Tryk på "Search" og dernæst kommer kameraet frem under "Devices" (Billede her).
 - Ændre nu IP-Adressen for kameraet så det er indenfor range.
 - Download GSDML filen for Sick Inspectorp62 via følgende link : (https://www.sick.com/br/en/catalog/products/machine-vision-and-identification/machine-vision/inspectorp62x/c/g507066?category=g569793&tab=downloads)
 - Åben TIA og importer GSDML filen for Sick Inspectorp62 <img width="1920" height="1028" alt="TIA import GSD" src="https://github.com/user-attachments/assets/29860e4b-9296-4eb3-8332-977ddbe13bb9" /><img width="807" height="510" alt="Installed GSD files" src="https://github.com/user-attachments/assets/a96c6458-92b8-4aee-8ae2-f122fd71fb84" />
 - Nu kan kamerat findes i hardware kataloget i TIA <img width="1920" height="1028" alt="Inspectorp62 in Hardware Catalog" src="https://github.com/user-attachments/assets/49d120c0-a5d4-4a3a-b4dd-74a41d465be3" />.
 - Træk kameraet ind i devices and network og opret en profinet forbindelse mellem kameraet og dine andre devices <img width="1920" height="1028" alt="Sick i devices and network" src="https://github.com/user-attachments/assets/f68ae006-d1ff-4d51-8f07-e11cf7c0190b" />.
 - Kameraets IP-adresse skal være den samme som i Sick AppStudio, og dernæst er der oprettet forbindelse mellem TIA og kameraet.


3) Opsætning af Sick InspectorP62 i SopasAir.
 - Åben Google Chrome og indtast kameraets IP-adresse i søgebaren, dette vil åbne SopasAir, hvis der er oprettet korrekt forbindelse til kameraet (Indsæt billede her)
 - 
   




 
