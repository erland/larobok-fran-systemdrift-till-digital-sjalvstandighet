# 8. Förflyttningen till verksamhetsdriven utveckling

Föreställ dig att en handläggare själv kan skapa en digital assistent som sammanfattar ärenden, hämtar relevant information och förbereder ett beslutsunderlag. Eller att en verksamhetsutvecklare kan bygga ett enkelt arbetsflöde genom att beskriva behovet på vanlig svenska. Tekniken kan göra sådana uppgifter betydligt lättare än tidigare. Men när lösningen börjar läsa känsliga uppgifter, fatta förslag som andra förlitar sig på eller skriva tillbaka till ett verksamhetssystem uppstår frågor som den enskilda skaparen sällan kan besvara ensam.

Den plattformsorienterade modellen från föregående kapitel erbjuder en viktig utgångspunkt: gemensamma tekniska förmågor med tydliga ägare, säkra standardvägar och självbetjäning. Nästa förflyttning handlar om att göra dessa förmågor användbara även för personer som inte arbetar som professionella utvecklare. Det är en större förändring än att införa ett nytt verktyg för AI eller lågkod. Den förändrar **vem som får skapa IT-stöd, vilka beslut som kan delegeras och vilket skydd som måste fungera utan individuell specialistgranskning**.

Det betyder inte att verksamheten bör utveckla alla lösningar själv. Målet är att sänka tröskeln för de lösningar där snabb och lokal utveckling skapar värde, utan att släppa de krav som följer med information, integrationer och produktion.

## Det nya är inte bara att kod går snabbare att skriva

Verksamhetsnära utveckling har funnits länge i form av kalkylblad, makron, databaser och senare low-code- och no-code-plattformar. Generativ AI gör det möjligt att beskriva funktioner i naturligt språk, skapa kod och formulera arbetsflöden med mindre formell programmeringskunskap. AI-assistenter kan dessutom kombinera språkförståelse med sökning och tillåtna verktygsanrop.

Men tiden som krävs för att skapa ett första fungerande exempel är inte samma sak som tiden som krävs för att etablera ett pålitligt IT-stöd. En prototyp kan fungera på några testdokument och ändå vara olämplig för produktion. Den kan sakna säkra behörigheter, hantera undantag dåligt, skriva felaktiga uppgifter, vara svår att underhålla eller bygga på data som inte får användas för ändamålet. NIST:s ramverk för generativ AI beskriver varför tillförlitlighet och riskhantering behöver omfatta hela livscykeln, inte bara själva modellen [K019].

Därför behöver förflyttningen skilja mellan att **skapa**, **publicera**, **driva** och **avveckla** en lösning. Det är olika förmågor och kräver olika mandat.

## En plattform som gör rätt väg enklast

I generation 3 är den typiska plattformsanvändaren ett professionellt utvecklingsteam. Teamet förstår exempelvis API:er, programbibliotek, loggning och driftsättningsmiljöer. En verksamhetsanvändare behöver ofta ett annat gränssnitt: godkända mallar, visuella arbetsflöden, AI-stöd, tydliga dataval och begriplig återkoppling när något inte får göras.

Under ytan kan många av förmågorna vara desamma. Identitet, loggning, datakontroll, hemlighetshantering, säkerhetskopiering och uppföljning behöver inte byggas på nytt för varje användargrupp. Skillnaden är att plattformen måste kunna presentera dem så att den som skapar en lösning inte behöver förstå alla tekniska detaljer för att följa reglerna.

En gemensam utvecklingsväg för verksamheten är mer än ett gränssnitt för att skapa appar. Organisationen behöver också säkra sätt att använda data, integrationer, säkerhet, kvalitetskontroll och förvaltning. Det avgör om ökad handlingsfrihet kan skalas utan att skapa okända och svårförvaltade lösningar.

## De tekniska förmågorna som behöver finnas

### Identitet och åtkomst som följer användaren och lösningen

Varje applikation och assistent behöver en tydlig ägare och en egen teknisk identitet där den agerar mot andra system. Åtkomsten ska inte bygga på att någon kopierar ett personligt lösenord eller en åtkomstnyckel till ett arbetsflöde. Rättigheter bör vara begränsade till det som behövs, kunna återkallas och följas upp. När en assistent agerar på uppdrag av en användare behöver organisationen dessutom skilja mellan användarens rättigheter och assistentens tillåtna handlingar.

Detta är särskilt viktigt för AI-agenter. En assistent som får läsa dokument är en annan risk än en agent som kan godkänna betalningar, ändra behörigheter eller publicera information. OWASP beskriver risker som prompt injection och alltför omfattande handlingsmandat (*excessive agency*) i sina rekommendationer för språkmodellstillämpningar [K020].

### Styrd tillgång till information

Verksamheten behöver kunna upptäcka och använda godkända datakällor utan att kringgå informationsklassning, sekretesskrav eller lagliga ändamålsbegränsningar. Det kräver information om datakällornas ägare, kvalitet, tillåtna användning och åtkomstvillkor. Plattformen kan erbjuda dokumenterade data-API:er, söktjänster och kontrollerade datamängder för testning.

En AI-assistent ska exempelvis inte få se mer information än användaren och användningsfallet tillåter bara för att modellen tekniskt kan söka i ett stort index. Samma behörighetsprinciper behöver fungera genom hela kedjan från fråga och hämtning till visat svar och eventuell åtgärd.

### Säkra och stabila integrationsgränssnitt

En intern app blir sällan särskilt användbar om den inte kan samverka med befintliga IT-stöd. Men direkt databasåtkomst och odokumenterade genvägar skapar beroenden som blir svåra att styra. Därför behövs versionerade API:er, tydliga kontrakt, spårbara anrop och begränsning av trafik och resursanvändning.

För arbetsflöden som kan ändra information bör det finnas separata, begripliga åtgärder, exempelvis *skapa utkast*, *föreslå ändring* och *verkställ godkänt beslut*. Att allt tekniskt kan uttryckas som ett API-anrop betyder inte att alla anrop ska erbjudas till självbetjäning.

### Godkända AI-förmågor och kontrollerade verktygsanrop

Verksamheten behöver en enkel väg till godkända modeller och AI-tjänster. Den vägen kan omfatta modellval, dataskydd, användningsregler, kostnadstak, dokumenterad lagring, loggning och utvärdering. En gemensam AI-gateway kan vara ett sätt att tillämpa vissa kontroller, men den ersätter inte säkerhetsdesignen i varje lösning.

När en assistent får använda verktyg bör åtgärdernas behörigheter, parametrar och konsekvenser kontrolleras utanför språkmodellen. För känsliga eller irreversibla handlingar kan mänskligt godkännande behövas. Ett naturligt språkgränssnitt är inte en säkerhetsgräns. En illvillig instruktion i ett hämtat dokument får inte kunna ge assistenten nya befogenheter [K020].

### Testning och kvalitet även när koden skapats av AI

Att ett verktyg kan generera kod eller ett arbetsflöde gör inte testning överflödig. Plattformen behöver erbjuda enkla sätt att testa funktion, behörigheter, felhantering, förändringar och återställning. För AI-baserade lösningar tillkommer utvärdering med representativa fall, kontroll av oönskade svar och uppföljning av hur beteendet förändras när modell, instruktioner eller data uppdateras.

Det bör också gå att se vilken version av en lösning som är publicerad, vilka datakällor den använder och vem som har gjort senaste förändringen. Annars går möjligheten till snabb förändring lätt ut över spårbarhet och felsökning.

### Publicering, drift och avveckling

En verksamhetsbyggd lösning behöver kunna publiceras på en godkänd plats, få en ansvarig ägare, övervakas och tas ur drift. Plattformen kan automatisera grundläggande åtgärder: registrering, loggning, resursgränser, uppdateringar, säkerhetskopiering där information lagras, larm och hantering av hemligheter. Men för ett viktigt IT-stöd behöver verksamheten fortfarande ange krav på kontinuitet, återställning, informationsbevarande och support.

Avveckling är lika viktig som etablering. En lösning som inte längre används ska kunna stängas, åtkomster återkallas, beroenden dokumenteras och information hanteras enligt gällande regler. Annars kan snabbt skapade lösningar bli en ny sorts teknisk och organisatorisk skuld.

## Risknivån behöver styra handlingsutrymmet

Det vore ineffektivt att behandla en personlig sammanfattningsassistent på samma sätt som ett system som fattar beslut i en kritisk process. Men det vore också riskabelt att låta användarens val av verktyg avgöra kravnivån. Det är **information, konsekvenser och befogenheter** som bör styra.

Ett praktiskt sätt är att skilja mellan tre nivåer:

| Typ av lösning | Typiskt mandat | Exempel på nödvändiga skydd |
|---|---|---|
| Personligt hjälpmedel | Eget arbete inom godkända tjänster | Godkända datakällor, begränsad delning, inga obehöriga åtgärder |
| Gemensamt verksamhetsstöd | Publicering för en grupp efter definierad kontroll | Utsedd ägare, versionshantering, testning, behörigheter, support och loggning |
| Verksamhetskritisk lösning | Professionellt tekniskt stöd och särskilt godkännande | Dokumenterad arkitektur, kontinuitetskrav, återställning, oberoende kontroller och incidentberedskap |

Nivåerna är exempel för att strukturera beslut, inte officiella riskklasser eller generella tillstånd att publicera lösningar. En till synes liten lösning kan behöva hamna högt om den använder särskilt känsliga uppgifter eller kan orsaka stor skada. NIST:s AI RMF och dess profil för generativ AI betonar kontext, riskbedömning och kontinuerlig uppföljning genom hela livscykeln [K006] [K019].

## Hur organisationens ansvar behöver förändras

Att verksamheten får skapa mer själv innebär inte att IT-avdelningen ska dra sig undan. Tvärtom behöver den tillhandahålla lättanvända och tillförlitliga förmågor, hjälpa till när lösningar passerar riskgränser och förvalta de gemensamma tekniska beroendena.

**Verksamheten** bör äga ändamålet, nyttan, informationens användning och prioriteringen. Den som beställer eller bygger ett arbetsflöde måste kunna beskriva vad som ska uppnås, vilka användare som berörs och vilka konsekvenser ett fel kan få. Det behöver finnas en namngiven ansvarig även efter att den person som skapade prototypen har bytt roll.

**Plattforms- och IT-funktionen** tillhandahåller godkända byggblock, tekniska skydd och uppföljning. Den ska göra den vanliga vägen enkel och ge stöd när verksamheten behöver gå utanför standarden. Det innebär ansvar för tjänsternas driftsbarhet, dokumentation och livscykel – inte att automatiskt äga varje enskild verksamhetsapp.

**Arkitektur och informationsförvaltning** behöver definiera kontrakt, gemensamma begrepp, dataägarskap och principer för integration. Utan det riskerar en stor mängd snabbskapade lösningar att binda ihop systemen genom sköra kopplingar. Arkitekturstyrning bör i första hand ske genom godkända mönster och tydliga gränser, med särskild prövning för undantag och kritiska lösningar.

**Säkerhets- och riskfunktioner** definierar kontroller och hjälper till att bedöma avvikelser. Riskacceptans måste följa organisationens faktiska mandatordning; den får inte bli en automatisk följd av att en användare själv kan publicera en lösning. För AI kan risker även omfatta felaktig information, otillbörlig påverkan, oväntade handlingar och bristande insyn [K019] [K020].

**Professionella utvecklingsteam** behövs fortsatt för avancerad utveckling, kritiska integrationer, kvalitetskrävande tjänster och stöd till verksamheten. En viktig uppgift kan vara att hjälpa en verksamhetsbyggd prototyp att växa till ett professionellt förvaltat IT-stöd när dess betydelse ökar.

## En möjlig stegvis förflyttning

Förändringen behöver inte börja med att hela organisationen får bygga och publicera vad som helst. Den kan genomföras i en ordning där man lär sig hur både teknik och ansvar fungerar.

**Första steget är kontrollerade experiment.** Välj ett fåtal användningsfall med tydligt avgränsad information och begränsade konsekvenser. Tillhandahåll godkända verktyg, testdata, dokumenterade regler och ett enkelt sätt att få hjälp. Mät hur mycket tid som faktiskt sparas och vilka problem som uppstår.

**Andra steget är gemensamma lösningar med definierat ägarskap.** Innan en lösning publiceras för fler användare behöver det finnas en fastställd publiceringsprocess, versionshantering, testning, behörigheter och en tydlig supportväg. Pröva hur lösningar kan överlämnas mellan personer utan att kunskap och åtkomster går förlorade.

**Tredje steget är selektiv delegering.** När plattformens kontrollmekanismer fungerar och verksamheten har visat att den kan hantera sina lösningar kan fler uppgifter automatiseras. Det betyder inte att alla risknivåer får samma frihet. Vissa typer av åtgärder bör fortsatt kräva särskilt godkännande eller professionellt utvecklingsansvar.

Precis som vid självbetjäning för professionella utvecklingsteam bör mandatet alltså växa först när skydd och ansvar är prövade.

## När är förändringen värd att påbörja?

Det finns goda skäl att inleda en förflyttning när verksamheten har många relativt små digitaliseringsbehov som annars fastnar i långa köer, när gemensamma data- och integrationsgränssnitt redan är användbara och när organisationen kan erbjuda godkända verktyg med grundläggande skydd.

Men det finns också tecken på att det är för tidigt att skala upp:

- Ingen kan beskriva vilka data och åtgärder som får användas i självbyggda lösningar.
- Lösningar saknar namngivna ägare och fungerande vägar för support och avveckling.
- Åtkomst bygger på delade användarkonton, breda tekniska rättigheter eller odokumenterade direktintegrationer.
- Plattformen saknar loggning, kostnadskontroll, versionering eller möjlighet att återkalla en publicerad lösning.
- Organisationen förväntar sig att AI-genererad kod eller AI-svar kan användas i kritiska processer utan systematisk testning och bedömning.

**Beslutsutfall:** Välj en begränsad pilot när nyttan är beskriven, godkänd dataåtkomst finns, tekniska kontroller går att prova och någon har mandat att äga lösningen under hela dess livscykel. Saknas data- och behörighetsregler ska informationsägare och IT först fastställa dem; saknas publicerings- eller återkallningsförmåga ska plattformsteamet bygga den; saknas drift- och supportägare bör lösningen stanna i en kontrollerad försöksmiljö. En bred utrullning får vänta tills dessa skydd fungerar i praktiken.

## Ett återkommande exempel: handläggarens assistent

Återvänd till ärendehanteringen. Verksamheten vill ha en assistent som tar fram ett förslag till sammanfattning och pekar ut relevanta styrdokument inför ett beslut. En lämplig första version kan använda godkända dokumentkällor, visa sina underlag och lämna det slutliga ställningstagandet åt handläggaren. Den behöver inte kunna förändra ärendedata.

Om verksamheten senare vill att assistenten också ska skapa beslutsutkast i ärendesystemet behövs ett kontrollerat skrivgränssnitt, spårbarhet och tydligt godkännande. Om den dessutom ska fatta eller verkställa beslut förändras riskbilden ytterligare. Då krävs en ny bedömning av behörighet, rättsliga krav, kvalitet, ansvar och möjlighet att stoppa eller återställa felaktiga åtgärder.

Det är samma verksamhetsidé i tre olika former, men kraven skiljer sig markant. Förflyttningen till verksamhetsdriven utveckling handlar därför inte bara om att ge fler människor verktyg. Den handlar om att kunna **öka friheten stegvis utan att förlora kontrollen över konsekvenserna**.

## Vad nästa generation behöver klara

När fler personer kan skapa lösningar ökar antalet möjliga utvecklingsinitiativ. Det kan ge bättre lokal anpassning och kortare väg från idé till fungerande hjälpmedel. Samtidigt växer behovet av gemensamma identiteter, data- och integrationsgränssnitt, säkerhetskontroller och livscykelhantering. Det som tidigare var specialistarbete i varje projekt behöver i högre grad erbjudas som återanvändbara förmågor.

Den avgörande förändringen i ansvar är att IT inte längre behöver vara ensam producent av all digital funktionalitet. IT behöver däremot fortsatt säkerställa att den gemensamma miljön gör det möjligt att skapa lösningar på ett säkert, robust och förvaltningsbart sätt. Verksamheten får större frihet, men också ett tydligare ansvar för ändamål, informationsanvändning, prioritering och livscykel.

Nästa kapitel beskriver hur denna modell kan se ut när AI-assistenter och verksamhetsbyggda applikationer har blivit en naturlig del av organisationens digitala landskap. Den framtidsbilden ska läsas som ett möjligt scenario – inte som ett påstående att alla organisationer redan fungerar så.
