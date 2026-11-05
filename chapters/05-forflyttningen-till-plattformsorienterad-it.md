# 5. Förflyttningen till plattformsorienterad IT

I en distribuerad IT-miljö kan varje utvecklingsteam ha blivit skickligt på att förändra sin egen tjänst, samtidigt som organisationen som helhet får allt svårare att leverera. En ny databas kräver en beställning, ett nytt API en brandväggsregel och en ändrad driftsättning kräver samordning med flera specialistgrupper. Utvecklingsteamen automatiserar det de själva kan påverka. Drift och säkerhet försöker kontrollera en växande mängd varianter. Resultatet kan bli många lokala förbättringar utan att den samlade ledtiden minskar.

Det är här plattformsorienterad IT kommer in. Ambitionen är inte att ge varje team obegränsad makt över infrastrukturen, utan att skapa **gemensamma, återanvändbara och säkra sätt att utveckla och driva tjänster**. Det som återkommer för många team görs till en gemensam förmåga. Det som kräver kunskap om verksamheten ligger fortsatt nära dem som utvecklar den.

Den svåra frågan är därför inte vilken plattform som ska köpas eller installeras. Den är hur organisationen kan förändra teknik, ansvar och arbetssätt så att fler team får verklig självständighet utan att helheten blir mindre säker eller robust.

## Från beställningar till användbara förmågor

I den äldre modellen begärde ett team ofta en *aktivitet*: sätt upp en server, öppna nätverkstrafik, skapa en databas eller installera en kö. Varje begäran behövde tolkas, prioriteras och genomföras av någon annan. Om det fanns många team och tjänster blev den modellen snabbt svår att skala.

I den nya modellen begär teamet i stället en *förmåga* med kända egenskaper. Exempelvis en databastjänst med definierad informationsklass, automatiserade säkerhetskopior, spårbar provisionering, behörighetsregler och förutbestämda återställningsalternativ. Teamet ska kunna använda tjänsten utan att behöva förstå alla underliggande detaljer eller invänta ett separat manuellt beslut för varje normalfall.

Det är viktigt att skilja mellan tre nivåer. **Infrastrukturtjänsten** är de tekniska resurserna: beräkning, lagring, nätverk och körmiljö. **Plattformsförmågan** är ett säkert och underhållet sätt att använda dem, med dokumenterat gränssnitt och livscykel. **Självbetjäningen** är den väg som gör förmågan tillgänglig för ett utvecklingsteam, exempelvis API, kommandoradsverktyg eller en portal. En snygg portal utan automatiserade tjänster bakom är fortfarande till stor del en beställningskatalog.

Plattformar är därmed lika mycket organisatoriska produkter som tekniska installationer. CNCF:s mognadsmodell bedömer bland annat investering, användning, gränssnitt, drift och mätning var för sig – ett sätt att undvika föreställningen att en installerad plattform automatiskt är en fungerande plattformsförmåga [K014].

Förflyttningen ändrar hur samordningen sker. När varje nytt behov kräver ett separat samspel mellan utveckling och flera infrastrukturfunktioner uppstår väntetider. Med gemensamma gränssnitt och standardlösningar flyttas specialisternas arbete delvis från upprepade handgrepp till utveckling och förvaltning av tjänster som kan användas många gånger.

## De tekniska förmågor som behöver utvecklas

Det behövs sällan ett fullständigt teknikskifte på en gång. Däremot måste vissa grundförmågor fungera som en sammanhängande kedja. Om ett steg fortfarande är manuellt eller personberoende kan hela självbetjäningsupplevelsen fastna där.

### Infrastruktur som kod och kontrollerad provisionering

Första byggstenen är att skapa och förändra miljöer på ett repeterbart sätt. Infrastruktur som kod gör det möjligt att versionera och granska nätverk, beräkningsresurser, databasinstanser och konfigurationer. Men enbart skript räcker inte. Organisationen behöver också hantera driftlägen, versionsändringar, hemligheter, godkännanden och ansvar för att resurser avvecklas när de inte längre behövs.

En viktig skillnad är om samma automatisering kan köras säkert av många team eller om varje team förväntas bygga sin egen variant. Målet bör vara ett begränsat antal väl underhållna, återanvändbara konfigurationer – inte ett växande bibliotek av specialfall.

### Automatiserad leverans och kvalitetssäkring

En plattform bör kunna stödja ett repeterbart flöde från källkod till körande tjänst. Bygg, test, säkerhetsskanning, paketering och driftsättning behöver samverka. NIST beskriver i sin DevSecOps-vägledning hur applikationskod, infrastrukturkod, policyer och observerbarhet kan hanteras deklarativt och genom automatiserade leveransflöden [K015].

Det betyder inte att alla applikationer ska levereras på exakt samma sätt. Men organisationen bör erbjuda vägar som täcker vanliga behov och som redan uppfyller de grundläggande kvalitetskraven.

### Identitet, behörighet och säkra standardinställningar

När nätverksgränser inte längre ensam kan bära säkerheten behöver identitet och åtkomst bli en naturlig del av tjänsteplattformen. Varje tjänst ska kunna få en tillförlitlig identitet; åtkomst mellan tjänster ska styras efter behov, inte efter att de råkar köras i samma zon. Hemligheter, certifikat, kryptering och åtkomstloggar bör kunna erbjudas som gemensamma förmågor [K001], [K012].

Det behövs också automatiska kontrollpunkter. *Policy as code* kan exempelvis förhindra osäkra konfigurationer eller kräva godkännande vid avsteg. Men automatiserade regler ersätter inte riskbedömning: de måste ägas, hållas uppdaterade och kunna hantera legitima undantag med spårbara beslut.

### Observerbarhet och återställningsförmåga

Gemensamma loggar, mätvärden och spårning över tjänstegränser behövs för att förstå användarflöden, inte bara enskilda servrar. Tjänster måste kunna knytas till ett sammanhang så att incidenter kan följas mellan komponenter. Plattformen bör även erbjuda mekanismer för säkerhetskopiering, återställning och redundans, med dokumenterade begränsningar och ansvar för att återställningsförmågan prövas.

Men här går en viktig ansvarsgräns: plattformen kan tillhandahålla och utföra säkerhetskopiering medan den ansvariga för IT-stödet, tillsammans med applikationsteamet, behöver fastställa *vilken information som ska kunna återställas, till vilken tidpunkt och inom vilken tid*. En redundansmekanism i infrastrukturen garanterar inte att verksamhetsflödet fungerar om någon beroendetjänst fallerar.

### En katalog över tjänster och beroenden

När antalet tjänster växer behöver organisationen veta vad som finns, vem som äger det, vilka beroenden det har och vilka säkerhets- och tillgänglighetskrav som gäller. En tjänstekatalog kan samla denna information och göra den användbar för förändringsarbete, kostnadsuppföljning och incidenthantering. Katalogen måste dock hållas aktuell genom leveransflöden och ägarskap; annars blir den bara ännu en dokumentationsuppgift.

## Var går gränsen mellan plattform och applikation?

Denna förflyttning misslyckas lätt om plattformen försöker göra för mycket eller om utvecklingsteamen förväntas lösa allt själva. En användbar tumregel är att **plattformen tar hand om det som kan standardiseras och återanvändas, medan applikationen tar hand om det som kräver verksamhetskunskap**.

| Fråga | Plattformens huvudsakliga bidrag | Applikationsteamets huvudsakliga bidrag |
|---|---|---|
| Säkerhet | Tjänsteidentitet, hemligheter, nätpolicyer, kontroller | Korrekt behörighet i verksamhetslogik och säker datahantering |
| Tillgänglighet | Redundanta körmiljöer, övervakning, driftsmekanismer | Feltoleranta beroenden och begripligt beteende vid fel |
| Backup | Säker och testbar kopiering samt återställningsverktyg | Krav på återställningspunkt, dataordning och verksamhetskontroller |
| Leverans | Standardiserade bygg- och driftsättningsvägar | Applikationstester, schemaförändringar och releasebeslut |
| Spårbarhet | Gemensam insamling, åtkomst och korrelation | Meningsfulla applikationshändelser och transaktionsspår |

Tabellen är inte en universell ansvarsmatris. Den visar en möjlig princip för arbetsfördelning. Vissa organisationer har dedikerade databasteam, andra använder externa tjänster. Ansvar behöver därför definieras för den faktiska lösningen och vara särskilt tydligt vid incidenter och förändringar.

## Organisationen behöver byta arbetssätt, inte bara verktyg

Tekniken kan möjliggöra självbetjäning, men det är i organisationsmodellen som förflyttningen blir verklig.

**Drift och infrastruktur** behöver i ökande grad arbeta som utvecklare och förvaltare av gemensamma tjänster. Kompetensen kring säker drift, kapacitet, nätverk och databaser är fortfarande nödvändig; däremot används den mer till att utforma standardiserade tjänster, automatisk styrning och återställningsbarhet än till att upprepa manuella installationer.

**Utvecklingsteamen** får större frihet att välja och använda godkända förmågor, men också tydligare ansvar för att deras applikationer fungerar i produktion. Att en tjänst kan driftsättas utan driftbeställning innebär inte att teamet får ignorera loggning, dataskydd, beroenden eller incidentberedskap.

**Arkitekturfunktionen** behöver flytta en del av sitt arbete från detaljgranskning av varje lösning till definition av gemensamma principer, arkitekturmönster, API-kontrakt och spelregler för undantag. Den behöver också kunna se när en standardlösning inte längre passar, och undvika att nya plattformskrav skapar onödig teknisk inlåsning.

**Säkerhetsfunktionen** behöver formulera testbara och riskanpassade krav som kan byggas in i plattformens tjänster och leveransflöden. Granskningar behövs fortfarande, men bör koncentreras till risker och avsteg snarare än varje återkommande teknisk detalj.

**Förvaltning och tjänsteägare** måste fortsätta företräda den samlade verksamhetsnyttan. Plattformsteamet kan äga körmiljön och ett utvecklingsteam kan äga en komponent, men någon behöver fortfarande ansvara för kvaliteten i det sammanhängande IT-stödet och kunna prioritera mellan tvärgående behov.

Detta är inte en instruktion att flytta en organisatorisk ruta från drift till utveckling. Det är ett sätt att skilja på vem som *bygger en gemensam förmåga*, vem som *använder den* och vem som *ansvarar för resultatet för verksamheten*.

## Plattformen behöver behandlas som en intern produkt

En återkommande fallgrop är att en central plattform konstrueras utifrån vilka tekniker specialisterna behärskar, snarare än utifrån vad utvecklingsteamen faktiskt försöker åstadkomma. Plattformen får många funktioner men ett otydligt användargränssnitt. Då fortsätter teamen att bygga egna lösningar vid sidan av eller beställa hjälp manuellt.

Ett plattformsteam behöver därför förstå sina användare, ha en prioriterad produktplan, kunna ge stöd och mäta om de vanligaste uppgifterna verkligen blivit enklare. CNCF beskriver just detta som en mognad från tillfälliga processer till hanterade självbetjäningstjänster med kontinuerlig återkoppling [K014].

En användbar standardväg – ibland kallad *golden path* – gör det lätt att göra rätt. Den kan exempelvis skapa en ny tjänst med godkänd driftsmiljö, testflöde, grundläggande säkerhet, övervakning och dokumenterat ägarskap. Men den bör inte vara ett tvång som gör legitima specialfall omöjliga. Alternativa vägar behöver kunna hanteras genom tydliga, proportionerliga undantag.

Det finns också empiriska skäl att vara försiktig med en alltför triumferande berättelse om plattformar. DORA:s undersökning från 2024 fann positiva samband med produktivitet och organisationsresultat men också samband med sämre leveransstabilitet och genomströmning i vissa utfall. Det är samband i en enkät, inte bevis för att plattformen ensam orsakat resultaten [K016]. Förflyttningen behöver därför följas upp med flera mått samtidigt.

## När är förflyttningen motiverad?

En större satsning på plattformsorienterad IT är framför allt intressant när liknande behov återkommer hos många team och den befintliga driftsmodellen skapar mätbara begränsningar. Typiska signaler är att flera team beställer samma slags miljöer, att säkerhetskonfigurationer skiljer sig utan goda skäl, att leveranser blockeras av återkommande infrastrukturköer eller att organisationen har svårt att se vilka tjänster och beroenden som finns.

Plattformen bör däremot inte byggas enbart för ett antaget framtida behov. Det är bättre att börja med ett fåtal verkliga behov som går att standardisera. En databasförmåga, en säker driftsättningsväg eller en standard för applikationsloggning kan räcka för att visa om modellen fungerar.

En viktig förutsättning är att organisationen kan finansiera **löpande produktförvaltning**. Självbetjäningstjänster behöver utvecklas, patchas, övervakas, dokumenteras och supporteras. Att bygga en plattform som ett tidsbegränsat projekt och sedan lämna den till en underbemannad driftgrupp riskerar att skapa en ny form av teknisk skuld.

## När är det för tidigt – och vad kan göras först?

Förflyttningen är ofta för tidig om organisationen saknar någon av följande grundförutsättningar:

- Det finns inte tillräckligt många återkommande behov för att motivera en gemensam tjänst.
- Ingen äger plattformens produktplan, kvalitet, säkerhet, drift och långsiktiga finansiering.
- Teamen saknar tillräckliga test-, driftsättnings- och incidentrutiner för att använda självbetjäning ansvarsfullt.
- Informationsklassning, behörighetsprinciper eller grundläggande säkerhetskrav är oklara.
- IT-stöden har så otydliga systemgränser och beroenden att en ny plattform mest skulle dölja problemen.
- Befintlig arkitektur kan förenklas betydligt utan ett stort plattformsskifte.

I sådana situationer kan första steget vara att minska variationen, dokumentera ansvarsgränser, etablera automatiserade tester eller återställa ordning i tjänstekatalogen. Ibland är en modulär monolit eller en mindre uppsättning delade tjänster bättre än en stor plattformsinvestering.

### En praktisk beslutsgrind

Innan organisationen tar beslut om en större plattformsförflyttning bör den kunna svara på fem frågor:

1. **Vilket återkommande problem ska lösas?** Finns uppmätta ledtider, incidentmönster, kostnader eller säkerhetsavvikelser som visar behovet?
2. **Vem är användaren?** Vilka team ska använda förmågan, och vad behöver de faktiskt kunna göra utan manuell hjälp?
3. **Vem äger hela livscykeln?** Finns bemanning och mandat att utveckla, driva, säkra, stödja och avveckla plattformstjänsten?
4. **Var går ansvarsgränserna?** Är ansvar för applikation, plattform, data, säkerhet och operativ helhet begripligt också vid en incident?
5. **Hur vet vi om det blev bättre?** Mäts både leveranshastighet, självständighet, kostnader, användarnöjdhet och tillförlitlighet?

**Beslutsutfall:** Återkommande behov, ett definierat internt kundteam, finansierad livscykel, tydliga ansvar och mätbara effekter talar för en avgränsad plattformspilot. Saknas gemensamma behov bör man först standardisera manuella leveranser; saknas produkt- och driftägarskap bör det etableras före självbetjäning; saknas säkerhetskrav bör grundkontrollerna definieras innan åtkomst automatiseras. Piloten ska bevisa kortare väntetid med bibehållen kvalitet, inte bara att tekniken kan installeras.

## Ett ärendehanteringsstöd som första pilot

Återvänd till det fiktiva ärendehanteringsstödet. Flera team ansvarar nu för ärendehantering, dokument, notifieringar och sök. Varje team behöver loggning, behörigheter, testmiljöer och en väg till produktion. Tidigare har de beställt liknande lösningar var för sig, ibland med lokala varianter som drift måste stödja.

Organisationen väljer att börja med **en standardiserad tjänsteväg**. När ett team skapar en ny komponent får den en godkänd körmiljö, grundläggande loggning, identitet, källkodsbaserad driftsättning och ett tydligt ägarskap. Databaser och andra känsliga förmågor läggs till stegvis efter riskbedömning. De flesta vanliga ändringar kan då ske utan separata beställningar. Drift- och säkerhetsspecialisterna utvecklar standardlösningen tillsammans med de team som ska använda den.

Piloten bedöms inte efter hur många verktyg som installerats. Den bedöms efter om ett team kan leverera en säker förändring snabbare, om incidenter går att förstå och om den gemensamma kostnaden blir mer hanterbar. Den kanske viktigaste observationen är om utveckling, drift och förvaltning får **tydligare** ansvar än tidigare.

## Vad som egentligen förändras

Förflyttningen från distribuerad till plattformsorienterad IT innebär ett byte av samordningsmodell. I stället för att organisationen samordnar varje nytt tekniskt behov genom manuella beställningar och personkontakter skapas gemensamma tjänster som bär en del av samordningen i sig.

Det kan frigöra utvecklingsteamens tid och göra säkerhet och driftskrav mer konsekventa. Men det fungerar bara om plattformen löser verkliga problem, har ett långsiktigt ägarskap och inte ersätter en gammal flaskhals med en ny. Nästa kapitel beskriver hur en sådan plattformsorienterad IT-miljö kan fungera när förmågorna väl har etablerats – och vilka nya risker som då behöver hanteras.
