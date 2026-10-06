# Ändringslogg – TaggKontroll Pro

Sammanfattning av vad som är nytt i varje publicerad version. Fullständiga beskrivningar finns i
`LÄS_MIG.txt` i respektive version. Bara den senaste versionen hålls tillgänglig under Releases.

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
