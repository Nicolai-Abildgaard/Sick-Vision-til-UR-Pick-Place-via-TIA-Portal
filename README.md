Denne guide forklarer et Pick&Place program med integreret vision, og  hele opsætningen af følgende enheder:

- Sick InspectorP62.
- UR3e.
-TIA Portal.


Følgende steps er blevet lavet:

1) Opsæt profinet forbindelse mellem Siemens PLC --> UR3e --> Sick InspectorP62.
 - Profinet forbindelsen melllem vores PLC og UR3e kan oprettes ved hjælp af min anden guide. (https://github.com/Nicolai-Abildgaard/Profinet-guide-UR)


2) Opsætning af Sick InspectorP62 i TIA .
 - Tilslut kameraet til 24 V/DC. 
 - Download Sick AppManager.
 - Åben nu programmet, og følgende vindue kommer frem: <img width="1023" height="800" alt="Sick Appspace 1" src="https://github.com/user-attachments/assets/32e4acd8-8fcc-4020-86e4-2062bc47b657" />
 - Tryk på "Search" og dernæst kommer kameraet frem under "Devices" <img width="1023" height="800" alt="Sick Appspace med device" src="https://github.com/user-attachments/assets/eb761e6d-a508-4cc4-8b76-c14506d42541" />
.
 - Ændre nu IP-Adressen for kameraet så det er indenfor range.
 - Download GSDML filen for Sick Inspectorp62 via følgende link : (https://www.sick.com/br/en/catalog/products/machine-vision-and-identification/machine-vision/inspectorp62x/c/g507066?category=g569793&tab=downloads)
 - Åben TIA og importer GSDML filen for Sick Inspectorp62 <img width="1920" height="1028" alt="TIA import GSD" src="https://github.com/user-attachments/assets/29860e4b-9296-4eb3-8332-977ddbe13bb9" /><img width="807" height="510" alt="Installed GSD files" src="https://github.com/user-attachments/assets/a96c6458-92b8-4aee-8ae2-f122fd71fb84" />
 - Nu kan kamerat findes i hardware kataloget i TIA <img width="1920" height="1028" alt="Inspectorp62 in Hardware Catalog" src="https://github.com/user-attachments/assets/49d120c0-a5d4-4a3a-b4dd-74a41d465be3" />.
 - Træk kameraet ind i devices and network og opret en profinet forbindelse mellem kameraet og dine andre devices <img width="1920" height="1028" alt="Sick i devices and network" src="https://github.com/user-attachments/assets/f68ae006-d1ff-4d51-8f07-e11cf7c0190b" />.
 - Kameraets IP-adresse skal være den samme som i Sick AppStudio, og dernæst er der oprettet forbindelse mellem TIA og kameraet.


3) Opsætning af Sick InspectorP62 i SopasAir.
 - Åben din browser og indtast kameraets IP-adresse i søgefeltet, dette vil åbne SopasAir, hvis der er oprettet korrekt forbindelse til kameraet.
 - Det første man skal er at oprette et Job <img width="1920" height="1020" alt="SopasAir Job" src="https://github.com/user-attachments/assets/9ec943e2-7875-4ccd-8a37-3c7e7389cd25" />.
 - Når man har oprettet sit job, kan man begynde opsætningen. Man kan se kameraets billede live dette bruges til at kalibrere kameraet.
 - For at skabe sit eget origo (Nulpunkt) skal kameraet kalibreres, dette gøres med et plain kalibreringsmønster som printes i a4 eller a3 <img width="642" height="427" alt="Kalibreringsmønster" src="https://github.com/user-attachments/assets/b5468417-bdc9-45b8-adac-af4f78993770" />.
 - Man åbner System --> Calibration og herinde kan man angive størrelsen af tilesne på ens kalibreringspapir og sige hvilken type mønster det er <img width="1920" height="1020" alt="SopasAir kalibrering" src="https://github.com/user-attachments/assets/86bf7c6f-1d0d-47bd-9219-1623e5bc4785" />.
 - Nu skal man vælge den kalibrering man har lavet, dette gøres under Acquisition også i højre side vælger man "Image correction" og i dropdown menuen vælger man "Full calibration". Dette definerer altså at kameraet bruger den nye kalibrering af origo som referencepunkt, desuden konverteres kameraets pixels til mm.<img width="1920" height="1020" alt="SopasAir kalibrering aq" src="https://github.com/user-attachments/assets/d4c75d7a-085a-413f-aedf-bc5b2b45cf3b" />.
 - Nu kan man sikre at kameraet har de optimale forhold, dette kan den selv gøre ved hjælp af auto setup. Dette skal gøres når emnet er placeret i origo <img width="1920" height="1020" alt="SopasAir autosetup" src="https://github.com/user-attachments/assets/92254e41-9bf9-42fc-9b8a-9adb41fb865c" />.
 - Tilføj nu den måde du vil detektere emnet med, i dette tilfælde vælges object locator <img width="1920" height="1020" alt="SopasAir Object locater" src="https://github.com/user-attachments/assets/e691461f-a95f-42a4-b36f-3ef3785e12b6" />.
 - Når man har valgt detekteringsmetoden, kan man tilpasse denne så den kan se objektet man ønsker. Man kan tilpasse hvor mange pixels den detektere i kanten af objektet, og man kan ændre på hvor stor en vinkel emnet kan have og stadig blive godkendt af den matchscore man kan sætte for hvert objekt <img width="1920" height="1020" alt="SopasAir Edge" src="https://github.com/user-attachments/assets/8f9d86f2-2555-47c5-90fa-c0584980c9e1" /><img width="1920" height="1020" alt="SopasAir Matchscore" src="https://github.com/user-attachments/assets/67d8983f-0b39-4af5-a8cc-9a77cda56295" />.
 - Nu mangles der kun at oprette forbindelse med profinet. Dette gøres i System --> Fieldbus. Her kan man enable profinet og enheden kan navngives, så man let kan finde og matche den i TIA <img width="1920" height="1020" alt="SopasAir profinet" src="https://github.com/user-attachments/assets/3fe41906-a691-4105-a426-d8afc12a8bec" />.
 - Sidste step er at gå ind i menuen Jobs og scrolle ned til communication. Her tilføjer man profinet og det er i denne menu at man kan vælge hvilken data man vil sende over, og på hvilke adresser de skal sendes til. <img width="1920" height="1020" alt="SopasAir Profinet in" src="https://github.com/user-attachments/assets/6fdc4b5c-95f1-4fe5-9c1c-a0a681bc24f4" />.


4)Opsætning af tags og program i TIA
 - Her ses project tree og alle de blokke og tagtables der er oprettet <img width="1920" height="1028" alt="TIA ProjectTree" src="https://github.com/user-attachments/assets/65e6d6f8-0991-462d-b92c-b94d804cf8a5" />.
 - Her ses alle de oprettede tags i programmet <img width="1221" height="1020" alt="PLC Tags" src="https://github.com/user-attachments/assets/e1afa7e0-b560-4e28-9703-563a91604571" />.
 - Her er koden der er lavet i de forskellige blokke:
 - <img width="1920" height="1028" alt="TIA Main" src="https://github.com/user-attachments/assets/3c43d72c-ef30-45d1-83c1-c98c162d3874" />



    // Konverterer DWORD til REAL og bytter rund på Word (BIG_endian, Little_Endian)
"UR_X" := DWORD_TO_REAL(SWAP_WORD(SWAP_DWORD( "UR_Raw_X")));
"UR_Y" := DWORD_TO_REAL(SWAP_WORD(SWAP_DWORD( "UR_Raw_Y")));
"UR_Z":= DWORD_TO_REAL (SWAP_WORD(SWAP_DWORD("UR_Raw_Z")));

"RX_Out" := "Joint_RX";
"RY_Out" := "Joint_RY";
"RZ_Out" := "Joint_RZ";

// Ganger REAL med 1000 for at få værdi i MM
"UR_X_mm" := "TCP_1.X" * 1000.0;
"UR_Y_mm" := "TCP_1.Y" * 1000.0;
"UR_Z_mm" := "TCP_1.Z" * 1000.0;

//Positioner fra sick skal divideres med 10000 for at have samme enhed som ur3e
"Sick_to_UR_X" := "Sick_Pos_X_mm" / 10000;
"Sick_to_UR_Y" := "Sick_Pos_Y_mm" / 10000;

// Afventer match score, samt kordinater mellem -50 og 50. hvis alt er opfyldt starter subprogram (Firkant)
IF "Sick_Match_Score" > 70 AND "Sick_Pos_X_mm" > -50 AND "Sick_Pos_X_mm" < 50 THEN
    "UR_General_Purpose_Reg1".Bits.Register[0] := 1;
ELSE
    "UR_General_Purpose_Reg1".Bits.Register[0] := 0;
END_IF;

//Sender [X,Y,Z,RX,RY,RZ] til robotten, X,Y er kordinater fra vision.
IF "Sick_Match_Score" > 70 THEN
    "UR_General_Purpose_Reg1".Floats.Register[0] := "Sick_to_UR_X";
    "UR_General_Purpose_Reg1".Floats.Register[1] := "Sick_to_UR_Y";
    "UR_General_Purpose_Reg1".Floats.Register[2] := 0.036;
    "UR_General_Purpose_Reg1".Floats.Register[3] := 0;
    "UR_General_Purpose_Reg1".Floats.Register[4] := 3.141;
    "UR_General_Purpose_Reg1".Floats.Register[5] := 0;
END_IF;

// Manuel styring til transportbånd
IF "Knap_Rev" THEN
    "Motor_REV" := TRUE;
ELSE
    "Motor_REV" := false;
END_IF;

IF "Knap_Fwd" THEN
    "Motor_FWD" := true;
ELSE
    "Motor_FWD" := false;
END_IF;

- De enkelte tags kan åbnes og ses i de tilhørende tagtables. Desuden kan adresserne ses under devices and network.

5) Opsætning af UR3e
- Det sidste der skal gøres er konfigurering af UR3e robotten. Lav et nyt projekt.
- Robotten skal køre over profinet, dette er tidligere beskrevet.
- Det kalibrerede plane der er lavet på sick kameraet, skal passe med et plane på UR robotten. Gå derfor ind under features og opret et nyt plane.
- Ved oprettelse af et plane, er det vigtigt at holde styr på x og y retningerne stemmer overens med dem fra vision kameraet.
- Dette plane, skal man så bruge til at lave et script.
- De værdier som er blevet sendt fra vision til plc, kan nu sendes fra plc til UR robotten. Dette gøres med script funktionen hvor man definere en variabel og sætter den lig en general purpose pin.
- Det sidste punkt er at oprette selve UR programmet, i dette tilfælde er der lavet et offset, for at få robotten til at samle objektet op et stykke efter kameraet.












   
   




 
