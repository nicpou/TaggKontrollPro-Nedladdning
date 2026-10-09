# Ändringslogg – TaggKontroll Pro

Sammanfattning av vad som är nytt i varje publicerad version. Fullständiga beskrivningar finns i
`LÄS_MIG.txt` i respektive version. Bara den senaste versionen hålls tillgänglig under Releases.


## 1.34.0 – 2026-10-09

Ny funktionsversion för dig som ändrar datamodellen. Byt ut TaggKontrollPro.exe; villkor och brandvägg påverkas inte. Agenten finns som 1.3.2 (ombyggd med Go 1.27.2, byt när det passar). Läs "Vad behöver jag göra?" i releasetexten först.

- Viktigt: första starten strukturerar befintliga modellversioner i bakgrunden. Programmet går att använda under tiden, och förloppet syns i Datamodellversioner (LÄS_MIG 7.2).
- Viktigt: en datamapp från före 1.21.0 kan få en annan namnrymd för exporterade instanser. Kontrollera den i Inställningar före nästa export (LÄS_MIG 8.9, avsnitt 6).
- Nytt: validering av datamodellen med fel, varningar och information per version, en rapport, märken i Modellträd och hinder vid beslut av en ny version (LÄS_MIG 7.15, 8.3).
- Nytt: profil för Codesys eller generisk OPC UA per modellserie under Inställningar (LÄS_MIG 8.9).
- Rättat: en agent som loggade in på nytt kunde få sin nya anslutning stängd under belastning, vilket gav ett kort avbrott. Felet fanns i 1.33.1 (LÄS_MIG avsnitt 9).
- Rättat: namn från en kunds datamodell låg kvar i programmet och i TaggKontrollPro.exe. Nu är de borta, och dialogerna är generiska.
- Säkerhet: programmeringsverktyget Go uppgraderat till 1.27.2, som rättar tio kända säkerhetsbrister. Felet fanns i 1.33.1.
- Inte provat: Windows. Teamet har provat på en testserver med Linux. Prova i en testinstallation först om ni kör programmet som tjänst.
- Provat: uppgradering från 1.33.1 med två versioner utan modellnamn. Från 1.33.0 är den inte provad. Ta en säkerhetskopia av datamappen före första starten.
- Tar tid: kontrollen av en ändring i Nästa version kan ta ungefär 2 minuter på mycket stora modeller (ungefär 10 000 typer och 16 ändringar). Den körs i bakgrunden. Vänta på resultatet.

## 1.33.1 – 2026-10-08

Rättningsversion för er som har använt Ersätt användare i datamodellförvaltningen, och för er som tar bort typer i fliken Modellträd. Byt ut TaggKontrollPro.exe; data, villkor, brandvägg och agenten på iFIX-noderna påverkas inte.

- Viktigt: har ni använt Ersätt användare med valet "Ersätt också i fritext" i 1.32.1 eller 1.33.0, kontrollera motiveringar och kommentarer som nämner de ersatta personerna (LÄS_MIG 7.14).
- Rättat: en ägandeform med typografisk apostrof, till exempel "Anna’s", kunde ersättas i fritext av Ersätt användare. Nu lämnas den orörd och redovisas i kontrollen (LÄS_MIG 7.14).
- Rättat: kontrollen efter Ersätt användare redovisade ett längre valt namn som "annan användare" trots att det ersattes, och felmeddelandena om genitiv är tydligare (LÄS_MIG 7.14).
- Rättat: Ta bort typ stoppades med "refereras av 1 nod i filen" när modellfilen skrev en referens med ett kortnamn i stället för den vanliga identiteten (LÄS_MIG 7.9).
- Rättat: villkorsdialogen och Ersätt användare kunde inte användas i smala fönster eller med zoomad webbläsare (LÄS_MIG 7.14).
- Inte provat: Windows. Teamet har provat på en testserver med Linux. Prova i en testinstallation först om ni kör programmet som tjänst.
- Rättat: byte av bastyp i Modellträd tog inte bort den gamla bastypens referens när modellfilen skrev den med ett kortnamn, så typen kunde få två bastyper; självtestet upptäcker nu en sådan fil (LÄS_MIG 7.9).

## 1.33.0 – 2026-10-08

Ny funktionsversion för er som tar fram migreringsrapporten. Byt ut TaggKontrollPro.exe; data, villkor, brandvägg och agenten på iFIX-noderna påverkas inte.

- Viktigt: kommer ni från 1.32.0 gäller också rättningen i 1.32.1 (Ersätt användare, LÄS_MIG 7.14). Läs den posten.
- Nytt: fliken Rapport visar migreringsrapporten på skärmen med innehållsförteckning, hopfällbara avsnitt och tabeller. Ett understruket antal öppnar taggarna i Taggar, och Tillbaka leder till rapporten (LÄS_MIG 8.3).
- Nytt: Spara som HTML ger en fristående fil med innehållsförteckning och tabeller, som kan skrivas ut eller sparas som PDF i webbläsaren. Spara som text ger samma textfil som förut. Varje tabell kan sparas som CSV eller Excel i filformatet från Inställningar (LÄS_MIG 8.3, 8.9).
- Inte provat: Windows. Teamet har provat på en testserver med Linux. Prova i en testinstallation först om ni kör programmet som tjänst.
- Inte provat: utskrift till PDF är provad i Chromium, inte i Edge på Windows, och Excelfiler är inte öppnade i Microsoft Excel. Kontrollera utskriften och filen innan ni lämnar dem vidare.

## 1.32.1 – 2026-10-08

Rättningsversion för er som har använt Ersätt användare i datamodellförvaltningen. Byt ut TaggKontrollPro.exe; data, villkor, brandvägg och agenten på iFIX-noderna påverkas inte.

- Viktigt: har ni använt Ersätt användare med valet "Ersätt också i fritext" i 1.32.0, kontrollera motiveringar och kommentarer som nämner de ersatta personerna (LÄS_MIG 7.14). Hjälptexten under valet säger nu att fritexten inte kan ersättas i efterhand.
- Rättat: Ersätt användare kunde ändra en annan användares namn i fritexter när namnen hade ett ord gemensamt (1.32.0). Det gällde också genitiv ("Anna Bergs"), dubbla mellanslag, radbrytning och annan versalisering. Nu lämnas andra användares namn orörda, och bytet med många skyddade namn går snabbare (LÄS_MIG 7.14).
- Rättat: kontrollen efter Ersätt användare varnade "oväntat kvar" för ett förnamn som också var en annan användares namn, och klassade ett namn i ändringsloggen fel när fritextvalet var av. Den valda personens genitiv ("Annas") ersätts inte och redovisas nu under förväntat kvar som böjd form. Sådana förekomster syntes inte alls i 1.32.0 (LÄS_MIG 7.14).
- Rättat: förhandsvisningen och "Visa koden" visar ändringarna i kortnamnen vid namnbyte och borttagning av en typ, och modellfilen blir snabbare att skapa när många typer tas bort. Statusraden under "Ej vald" visas hel i smala fönster (LÄS_MIG 7.10, 7.13).
- Inte provat: Windows. Teamet har provat på en testserver med Linux. Prova i en testinstallation först om ni kör programmet som tjänst.
- Inte provat: Ersätt användare i fritext visar bara genitiv på s och 's som böjd form i kontrollen. Den valda personens namn med bindestreck ("Anna-listan") ersätts inte och visas inte i kontrollen; andra användares namn skyddas även i sådana former. Kontrollera fritexter med sådana former efter bytet.

## 1.32.0 – 2026-10-08

Ny funktionsversion för er som ändrar datamodellen i programmet eller ansvarar för personuppgifter i
det. Byt ut TaggKontrollPro.exe; data, villkor, brandvägg och agenten på iFIX-noderna påverkas inte.

- Viktigt: godkännandet av ändringar är ett stöd för er interna kontroll, men inget
  behörighetsskydd, och personer hos en uppdragsgivare kan inte vara förvaltare (LÄS_MIG 7.13).
- Viktigt: har ni slagit på godkännandet, gå inte tillbaka till en äldre version. Den känner inte
  till godkännandet och kan besluta en ny version utan det.
- Nytt: godkännande av ändringar i datamodellen – varje ändring kan krävas godkänd av en annan
  person (rollen Datamodellförvaltare) innan den tas med i en ny version. ⋮ → "Inställningar…" →
  Modellförvaltning, av från början (LÄS_MIG 7.13).
- Nytt: listan Nästa version kan filtreras på status, med "Före och efter" och "Logg" per ändring,
  och historiken och ändringsförteckningen visar vem som godkände (LÄS_MIG 7.13).
- Nytt: Ersätt användare – en persons namn och Windows-konto ersätts med till exempel "Tidigare
  användare 1" i hela databasen, med förhandsvisning och kontroll efteråt. Kopior utanför databasen
  gallras separat (LÄS_MIG 7.14).
- Inte provat: versionen på Windows. Kör ni programmet som tjänst eller med lokala konton, prova i
  en testinstallation först.

## 1.31.1 – 2026-10-08

Rättningsversion för er som ändrar datamodellen i fliken Modellträd. Byt ut TaggKontrollPro.exe;
data, villkor, brandvägg och agenten på iFIX-noderna påverkas inte.

- Rättat: en typ kunde få ett namn som bara var prefixet (till exempel K_) om namnfältet lämnades
  tomt i "Ny typ" eller "Byt namn på typ" (LÄS_MIG 7.9).
- Rättat: en typ som fortfarande användes av en global variabel i modellfilen kunde tas bort, och
  filen fick då en hänvisning som inte gick att följa (LÄS_MIG 7.9).
- Rättat: efter namnbyte på en typ fanns det gamla namnet kvar som kortnamn (alias) i modellfilen.
- Rättat: "Förslag på ny typ" kunde föreslå ett namn med tecken som programmet sedan inte godtog
  (LÄS_MIG 7.11).
- Rättat: ofullständig text i Metadata, fel länkfärg i fliken Data i mörkt tema och sidledsrullning
  av hela sidan i fliken Taggar.
- Nytt: BEROENDEN.txt – läsbar förteckning över ingående bibliotek, för IT- och säkerhetsgranskning.
- Inte provat: versionen på Windows. Kör ni programmet som tjänst, prova i en testinstallation först.

## 1.31.0 – 2026-10-08

Ny funktionsversion: programmet hjälper dig att bygga nya typer i datamodellen, och brandväggen
ändras bara när du själv ber om det. Inga nya villkor och dina data behålls.

- Viktigt: att installera programmet som Windows-tjänst öppnar inte längre brandväggen. Regeln för
  iFIX-agenterna skapar du själv, när agenterna ska användas, med kommandot som visas färdigt under
  ⋮ → "iFIX-agenter…". En regel som redan finns står kvar. Skript som kör
  `-installera-tjanst -brandvagg` nekas och måste ändras (LÄS_MIG 3.5 och 9.3).
- Nytt: Förslag på ny typ – programmet föreslår namn, bastyp och signaler för en ny typ (en mall i
  datamodellen för en sorts komponent) utifrån taggar som saknar motsvarighet, och visar vad
  förslaget bygger på. Fliken Modellträd → "+ Ny typ…", eller "Föreslå typ…" i taggens
  detaljpanel. Kräver licens (LÄS_MIG 7.11).
- Nytt: valfria signaler och nya datatyper – markera att alla instanser av en typ inte behöver ha
  en viss signal eller ett visst delobjekt ("Gör valfri"), och lägg till uppräkningar (till exempel Av = 0, Auto = 1) och
  enkla strukturer under Datatyper → "Ny datatyp…". Analysen och exporterna påverkas inte
  (LÄS_MIG 7.12).
- Nytt: brandväggsstatus under ⋮ → "iFIX-agenter…" och i fliken Data – programmet visar om regeln
  för agenterna finns och ger ett kommando att kopiera till Kommandotolken eller PowerShell.
- Säkerhet: biblioteket för Excelfiler är uppdaterat. Tidigare kunde en manipulerad Excelfil få
  programmet att krascha vid inläsning.
- Rättat: ändringsdialogerna i fliken Modellträd tappade det du hade skrivit om de stängdes av
  misstag (Esc eller klick utanför). Nu sparas ett utkast som kommer tillbaka nästa gång.
- Rättat: namnbyte på en typ som en annan typ använder som delobjekt kunde stoppas av programmets
  kontroll av modellfilen.
- Inte provat: brandväggsdelen på Windows, och Excelfilerna är inte öppnade i Microsoft Excel av
  teamet. Kontrollera regeln i Windows Defender-brandväggen och öppna en exporterad fil innan du
  lämnar den vidare.

## 1.30.0 – 2026-10-07

### Viktigt vid uppgradering
- Inga nya villkor. Inget nytt i databasen eller flyttfilen; 1.29.0 kan öppna en datamapp från 1.30.0.
- Uppgradering genom att byta ut TaggKontrollPro.exe rör aldrig brandväggen.
- Brandväggsregeln "TaggKontroll Pro agentkanal" tas nu bara bort när den finns (vid
  -installera-tjanst -brandvagg … och -avinstallera-tjanst). Tidigare kördes borttagningen alltid,
  vilket kunde ge ett onödigt larm "regel borttagen" i Windows brandväggslogg. Utskriften anger om
  regeln skapades, ersattes, inte fanns, eller om läget inte kunde avgöras (LÄS_MIG 3.5).

### Nytt
- Kodvyn i Modellträd (knappen Kod eller Alt+K, kräver licens): NodeSet2-koden för vald nod,
  hela modellfilen eller en enskild ändring i Nästa version med markering + ~ − och U-nummer.
  Sökning i hela filen med träfflista, Gå till rad, hopp mellan kod och träd, hopp mellan
  ändringar, kopiera och ladda ner utsnitt. Klarar en modellfil på 200 MB (LÄS_MIG 7.10).

### Ändrat och rättat
- Medlemsnamnen i detaljrutans medlemslista syntes inte vid 1440/1920 px (sedan 1.29.0).
- Mappen kodvy_tmp i datamappen (kodvyns arbetsyta) kan undantas från säkerhetskopior.

### Kända begränsningar
- U-nummer i kodvyn knyts till elementet, inte till enskilda rader.
- "Visa koden" för en ändring som tar bort en medlem ger även notisen "Noden finns inte i
  version X" – rättas i 1.31.0.

## 1.29.0 – 2026-10-07

### Viktigt vid uppgradering
- Inga nya villkor.
- Fliken Datakällor heter Data. All inläsning startar med "Läs in…" i fliken eller i sidhuvudet
  (hette "Importera data"). ⋮-menyn är grupperad (Data, System, Fönster); Flytt och säkerhetskopia
  ligger under System.
- Datamodellen kan ändras i modellträdet, men programmet ändrar aldrig PLC-projektet – det verktyg
  som äger modellen är master. 1.28.x visar de nya ändringsslagen som hinder.

### Nytt
- **Inaktivera en datakälla** utan att ta bort den: taggar, rättningar, undantag och exportlogg
  finns kvar men ingår inte i analys, filter, KPI eller exporter; räknas mot taggtaket; hamnar
  aldrig på gatewayns borttagningslista. Chippet "Inaktiva källor"; Aktivera återställer exakt.
- **Vyn Data:** Läs in… (Taggar, Datamodell, Från iFIX), kolumnerna Bilder och Hälsa, Agenter och
  inkorg i vyn, rad om noder som bilderna refererar men som inte är inlästa.
- **Ändra datamodellen i modellträdet:** ny typ, byt namn, byt bastyp, beskrivning, ta bort typ,
  signaler och delobjekt, standardvärden – med motivering, löpnummer, logg, konsekvenskontroll
  (hinder, varningar, extra bekräftelse vid NodeId-ändring), markeringar i trädet, Nästa
  version-kortet, förhandsvisning och jämförelse med U-nr. Genererad NodeSet2 ändrar och tar bort
  noder i befintlig fil med självtest. Typtilldelningen följer namnbyten.
- **Metadata i detaljrutan** (standardvärden, dolda medlemmar, attribut, referenser), sökning i
  metadata och raden "Modellfilen".
- Supportpaketet anonymiserar ändringslistans namn, konton, motiveringar och standardvärden.

### Ändrat
- Hälsokontrollens sammanfattning sparas mellan ändringar.
- Undantagsregler prövas bara mot aktiva källor.

### Kända begränsningar
- Valfria medlemmar, nya datatyper, kodvy och redigerbar kod kommer i 1.30.0; godkännandeflöde
  (datamodellförvaltare) i 1.31.0.

## 1.28.1 – 2026-10-06

### Rättat
- Excel-import: en Excelfil med kolumnen Nod (och en enda nod) fick filnamnet som datakälla i
  stället för noden i kolumnen, så att inlästa bilder inte matchade taggarna. Nu gäller kolumnen
  Nod alltid; nodfältet i dialogen används bara när kolumnen saknas.

### Nytt
- Importdialogen föreslår kända iFIX-noder (bildernas noder först) och varnar om namnet inte är ett
  iFIX-nodnamn eller inte finns bland de inlästa bilderna.
- Kvittot visar varifrån noden kom och har knappen Koppla… när noden tagits ur filnamnet –
  kopplingen datakälla → iFIX-nod ger bildanvändning utan ny import. Fliken Datakällor visar samma
  anmärkning med länk.

### Viktigt vid uppgradering
- En Excelfil som tidigare lästs in under filnamnet som nod blir vid ny inläsning en ny datakälla
  bredvid den gamla – ta bort den gamla under Datakällor.

## 1.28.0 – 2026-10-06

### Viktigt vid uppgradering
- Inga nya villkor.
- Fliken Forge-batcher heter nu Export och samlar all taggexport; Exportera-dialogen är borttagen
  (knappen Exportera i sidhuvudet öppnar fliken). Sparade flikval från äldre versioner öppnar Export.
- Sammanslagning av stationer ligger nu under Inställningar; fliken Datakällor länkar dit.
- 1.27.0 kan öppna en datamapp från 1.28.0; analyserar 1.27.0 om visar 1.28.0 sedan "Kör om analysen".

### Nytt
- **Namnregler** (Inställningar): alla programmets namnregler i grupper med klartextnamn, regel-ID,
  beskrivning och antal taggar. 97 regler kan stängas av; strukturella regler, kontrollen mot
  datamodellen och informationssteg är fasta med angiven orsak, följdregler följer sin huvudregel.
  Sök, filter, "Alla på" per grupp, beroendedialog, förhandsvisning (övergångstabell, nya namn per
  regel, krockar, modellförslag, exporterade taggar per mål) och "Spara och analysera om". Ändringar
  loggas per regel. Med alla regler på är resultatet identiskt med 1.27.0.
- Detaljpanelen visar steget "Avstängd namnregel" med länk till regeln; ny fasett "Avstängda
  namnregler"; hjälpvyn får kolumnen Status och avsnittet "Stänga av regler"; rapporten och Excelns
  sammanfattning nämner avstängda regler när någon är av.
- **Fliken Export:** formatval Excel/CSV · Rapport · NodeSet · Forge-batcher · Gateway · Listor,
  startar med Förvald export, statusrad för förval/ändrat val, knapprad som säger vad som exporteras,
  samlad exporthistorik för Forge och gateway. Forge-batcher kan vara förvald export. Exportfiler
  och exportloggar är byte för byte som i 1.27.0.

### Ändrat
- Kontrast: reglagen i läget Av och länkar i varningsrutor i mörkt tema.
- Ångra i Forge-historiken är avstängd i läsläge.
- Forge-kortet i fliken Export visas direkt även med flera hundra tusen taggar.

## 1.27.0 – 2026-10-06

### Viktigt vid uppgradering
- Modellträdet kräver nu en giltig licens. I demoläget och när alla licenser gått ut visas fliken
  utgråad med knappen "Licens…"; med giltig licens och överskridet taggtak fungerar den som förut.
  Datamodellen kan ändå läsas in, analyseras och visas/exporteras under Datamodellversioner.
- Vid första starten skapas ett index i gatewayloggen (några sekunder vid stora loggar); exporter
  väntar under tiden. Första analysen efter uppgraderingen tar cirka 10 % längre (engångs).
- 1.26.0 kan öppna en datamapp från 1.27.0. Har datamappen analyserats om i 1.26.0 medan
  BIP-förslag var på, kör om analysen i 1.27.0 (programmet uppmanar till det).
- Inga nya villkor.

### Nytt
- **Namnförslag enligt beteckningslistan (BIP)** där datamodellen saknar motsvarighet: ny inställning
  under Inställningar → Beteckningslista, av från början, slås på efter en förhandsvisning som visar
  vad som ändras. Ny bedömning "Rättad – enligt BIP" med egen färg, egen rad i fasetten och delsiffran
  "varav enligt BIP n" under KPI:n Rättad. Datamodellen är alltid förstahandsval; BIP styr bara
  komponentdelen. Motiveringen får källan "Beteckningslista" och hjälpvyn "Så föreslås namn" ett eget
  avsnitt. Med inställningen av är resultatet identiskt med 1.26.0.
- **Modellförslag med BIP:** nya typer namnges `K_<domän>_<BIP-kod>` och benämningen blir Description i
  NodeSet2-filen när förslaget tas med i en version. Modellträdet visar BIP-kod när en lista är aktiv.
- **Kontrollfråga vid export:** om taggar redan exporterats till Forge eller ett gatewaymål med ett
  annat namn än det som nu föreslås visas dialogen "Tidigare exporterade namn ändras" med lista,
  "Spara listan", "Skriv över" och "Avbryt". Jämförelsen görs i varje måls egen namnform. Forge-paketet
  får `Namnbyten.csv` när byten finns.
- **Panelavsnittet "Tidigare":** föregående förslag (namn, bedömning, modellversion, tidpunkt) och
  senast exporterat namn per mål – visas bara när något skiljer.

### Ändrat
- BIP-förhandsvisningens varning räknar bara riktiga namnbyten per mål.
- Bekräftelsen "Ta bort licens" låg bakom licensdialogen – rättad.

## 1.26.0 – 2026-10-06

### Viktigt vid uppgradering
- Licens- och användarvillkoren version 1.6 (bland annat punkt 12.6 om beteckningslistor). Alla
  användare godkänner villkoren på nytt vid första start.
- TaggKontroll Pro som Windows-tjänst: efter byte till 1.26.0 startar tjänsten, men import och
  agentdata nekas tills någon har godkänt villkoren i ett programfönster eller kört
  `TaggKontrollPro.exe -installera-tjanst -godkann-villkor` som administratör (LÄS_MIG 4.5).
- TaggKontrollAgent 1.3.1: tjänsten startar inte förrän
  `TaggKontrollAgent.exe -installera-tjanst -godkann-villkor` har körts som administratör, med samma
  skanningsflaggor som vid installationen (LÄS_MIG_AGENT avsnitt 4, Uppgradering).

### Nytt
- **Kolumnen BIP-kod:** programmet jämför varje taggs komponent med en beteckningslista och visar
  koden i en egen kolumn, med filter, ett avsnitt i detaljpanelen, tre kolumner sist i Excel- och
  CSV-exporten (BIP-kod, BIP-benämning, BIP-system) och ett avsnitt i rapporten.
- Inbyggd lista: BIP-koder 3.0.2, ett urval av typ- och systembeteckningar ur BIP (förvaltas av
  BIM Alliance Sweden). Välj vilka discipliner som ska ge träff; de som brukar finnas i
  fastighetsautomation är förvalda. Koder med en bokstav matchas bara om du väljer det.
- Egen lista: en nyare version eller fastighetsägarens egen beteckningslista kan läsas in som CSV-
  eller Excelfil (Inställningar, kortet Beteckningslista). Varje inläsning sparas som en version.
- Funktionen är avstängd från början, även i befintliga datamappar. Den slås på under Inställningar,
  kortet Beteckningslista.
- Hjälpvyn "Så föreslås namn" visar "Ej beräknad" i kolumnen Antal taggar när analysen behöver köras
  om, med knappen Analysera om nedanför tabellen.

### Ändrat
- Beteckningslistan ändrar inga föreslagna namn, motiveringar eller bedömningar.
- Excelfiler med ogiltiga cellreferenser eller radnummer över 1 048 576 nekas vid inläsning med ett
  begripligt meddelande (beteckningslista och taggar ur Excel).

## 1.25.0 – 2026-10-06

### Nytt
- **Varför detta namn:** detaljpanelen visar steg för steg hur det föreslagna namnet tagits fram –
  en rad per namndel (station, system, komponent, signal) med gammalt och nytt värde, varför, och
  vilken namnregel som användes. Rutan "Att kontrollera" visar det du själv bör kontrollera.
- Programmet säger att något finns eller saknas i datamodellen bara när det har slagit upp det i
  den datamodell analysen gjordes mot. Inbyggda regler står som "Regel i programmet – ingen kontroll
  mot datamodellen". Ett namn på en anläggningsdel (t.ex. FF02) förklaras som just det: numret
  kommer från taggen, inte från modellen.
- Filtret "Belägg i datamodellen" (Kontrollerat / Regel i programmet / Kunde inte kontrolleras /
  Avviker) och kolumnen "Varför" i taggtabellen.
- Hjälpvyn "Så föreslås namn" (⋮ → Hjälp) beskriver hur namnen tas fram och listar alla namnregler
  med antal taggar; tabellen kan exporteras.
- Tre nya kolumner sist i Excel och CSV: Motivering per namndel, Belägg i datamodellen, Att
  kontrollera. Rapporten har avsnitten "Så har namnen tagits fram" och "Okända mönster".

### Ändrat
- Kolumnen Motivering i Excel och CSV har samma namn och plats som tidigare men innehåller nu
  sammanfattningen. För en analys gjord av en äldre version står den tidigare texten kvar tills
  analysen körs om. Föreslagna namn och bedömningar är oförändrade.

## 1.24.0 – 2026-10-06

### Nytt
- **Supportpaket** (⋮ → Skapa supportpaket…): en zip-fil med loggar, panikloggar,
  systeminformation, versioner, licensläge (utan koder), inställningar, databasens schema och antal
  samt jobbhistorik – aldrig databasen, taggdata, modellfiler eller hemligheter. Dialogen visar fil
  för fil vad som ingår innan paketet skapas. Programmet skickar aldrig paketet; du skickar filen
  själv.
- Paketet är **anonymiserat som förval:** namn på noder, taggar, stationer, typer, modeller, filer,
  användare och datorer ersätts med alias (t.ex. Nod-K7Q2) och fritext med "<fritext, N tecken>".
  Aliasen är stabila för datamappen, och "Slå upp alias" i dialogen visar lokalt vilket namn ett
  alias står för. Namn i klartext väljs bara efter överenskommelse med leverantören. Loggrader
  skrivna av äldre versioner anonymiseras efter bästa förmåga – läs igenom paketet innan du skickar
  det.
- **Loggnivåer:** FEL, VARNING, INFO (förval) och DEBUG väljs i Inställningar → Loggning och
  felsökning och gäller direkt. "Utökad loggning i 30 minuter" finns under ⋮ → Om. Licenskoder,
  nycklar och sessionskakor loggas aldrig.
- **Kraschskydd:** ett internt fel i en åtgärd eller ett bakgrundsjobb stoppar inte längre
  programmet. Åtgärden avbryts med ett fel-id som också står på raden i loggen och i en paniklogg.
  Avslutas programmet ändå sparas felet och loggas vid nästa start.
- Kommandoraden: `TaggKontrollPro.exe -supportpaket <fil.zip>` skapar ett paket utan att programmet
  startar. Agenten: `TaggKontrollAgent.exe -supportpaket <fil.zip>` (och `-supportpaket-dbexporter`
  för ett anonymiserat utdrag ur en ny DBExporter-körning).

### Ändrat
- Felmeddelanden från programmet har ett fel-id som också står på loggraden – ange det när du
  kontaktar leverantören.

## 1.23.0 – 2026-10-06

### Nytt
- **Fliken Modellträd:** datamodellen visas som ett klickbart träd i två lägen – Typhierarki (vilken
  typ som bygger på vilken) och Uppbyggnad (vad en typ innehåller: delar, signaler och fält) – och
  två visningar som växlas med en knapp: ett grafiskt träd med zoom och panorering, och en utfällbar
  lista. Sök på typ, signal, datatyp och fält, teckenförklaring, "Fäll ut alla", "Anpassa" och
  "Till vald".
- Varje typ visar hur många taggar analysen kopplat till den. "Visa taggarna" öppnar fliken Taggar
  med det nya filtret Modelltyp. Hopp till trädet finns från taggens detaljpanel, från Modellförslag
  och från Datamodellversioner.
- Historiska modellversioner kan visas i trädet; en återkallad version märks. Aktiverar någon annan
  en ny version medan trädet är öppet visas ett besked, och trädet byter först vid klick på
  Uppdatera.
- Fliken fungerar i läsläge och utan licens; tangentbord och skärmläsare stöds.

### Ändrat
- Modelljämförelsen: "Ärvd från X" anger nu typen där signalen deklareras (den översta bastypen som
  har den), inte den närmaste bastypen. Det märks bara vid arv i fler än två nivåer.

## 1.22.0 – 2026-10-06

### Viktigt vid uppgradering
- Tidsbegränsade licenser räknas nu från startdatumet i licenskoden (normalt dagen koden
  skapades), inte från dagen den lästes in. Det gäller även licenser som redan är inlästa. En licens
  kan därför ha kortare tid kvar än tidigare eller redan ha gått ut – programmet går då i läsläge
  och alla data finns kvar. Leverantören byter koden på begäran: software@mindeu.se.
- Licens- och användarvillkoren är uppdaterade till version 1.5 och visas för godkännande vid
  första start.

### Nytt
- Licenser: samma kod ger samma slutdag oavsett var eller när den läses in. En licens kan ha ett
  startdatum i framtiden ("Kommande"). Licensdialogen visar hur många dagar som återstår. Nya
  licenskoder kräver version 1.22.0 eller senare; äldre koder fungerar.
- Klockskydd: om datorns klocka ligger mer än två timmar efter den tid programmet senast har sparat
  visas en klockvarning. Programmet fungerar som vanligt i 72 timmar; därefter spärras
  tidsbegränsade licenser (läsläge) tills klockan har gått ikapp eller en återställningskod från
  leverantören har lästs in. Sommar- och vintertid, byte av tidszon och små justeringar ger ingen
  varning. Evighetslicenser, taggbegränsade licenser och demoläget påverkas inte.
- Exporterade instanser: nya datamappar använder namnrymden `urn:taggkontroll:instanser`.
  Datamappar där exporter redan kan ha gjorts behåller sin tidigare namnrymd, så att redan
  exporterade id:n inte ändras. Inställningar visar vilken namnrymd som används. Forge- och
  edgeAggregator-exporten varnar om tidigare exporter gjorts med en annan namnrymd.
- Kontaktadressen är software@mindeu.se.

### Rättat
- Programmet kunde i sällsynta fall avslutas för alla användare om en analys startades samtidigt som
  en namnkontroll, rapport eller export kördes.
- CSV-exporten: datamodellens namn skyddas mot att tolkas som formel i kalkylprogram.

## 1.21.0 – 2026-10-05

### Nytt
- Tillbaka och Framåt i sidhuvudet (även Alt+vänsterpil/Alt+högerpil och musens sidoknappar).
  Sparade ändringar ångras aldrig – bara var du är och vad du tittar på.
- Godkänn alla i inkorgen, med fråga före och kvitto efter. Poster som kräver ditt val ligger kvar.
- Globala variabler och instanser i modellfilen (GVL) används aldrig som underlag för namnförslag.
- Gränssnittet fungerar bättre i smala fönster och med tangentbord; tydligare kontrast i ljust och
  mörkt tema.

### Rättat
- Ett dolt fält i den stängda detaljpanelen kunde ta emot tangenttryck.
- Fel i webbläsarens konsol när detaljpanelen öppnades för vissa taggar.

## 1.20.1 – 2026-10-05

### Ändrat
- Rubriker och filnamn i edgeAggregator- och Tunneller-exporterna följer modellens eget namn
  (ModelUri). Modelldelen i filnamnet är högst 40 tecken.
- Förtydligade importinstruktioner för Forge och gateway-exporterna.

### Rättat
- Dialogen "Ta med i nästa version" kraschade för en datamodell utan variabel- eller komponenttyper.

## 1.20.0 – 2026-10-05

### Nytt
- Troligen döda taggar: bedömning med förklaring, vyn "Troligen döda taggar" med möjlighet att
  undanta från export, filter och snabbvalet "Dölj troligen döda" i taggtabellen.

---

Programmet får endast användas enligt Licens- och användarvillkoren (VILLKOR.md i respektive
version). Kontakt och licenser: software@mindeu.se. © 2026 Mindeu AB.
