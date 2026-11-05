# 1. Den traditionella IT-modellen

När många organisationer beskriver sin äldre IT-miljö gör de det ibland som om allt var enklare förr. Det ligger något i det, men bara om man samtidigt förstår **vad** som faktiskt var enklare.

Det var sällan så att den traditionella modellen automatiskt gav bättre kvalitet i allting. Monoliter kunde vara svårtestade, interna beroenden kunde bli täta och releasefönster kunde vara både riskfyllda och arbetskrävande. Men modellen hade en egenskap som gjorde den mycket hanterbar: ett IT-stöd kunde ofta behandlas som **en sammanhållen leveransenhet**. Arkitektur, driftmiljö, ansvar och beställningar hängde därför ihop på ett sätt som i många fall blev praktiskt och begripligt.

I den här generationen bestod ett IT-stöd typiskt av ett mindre antal tydliga huvudkomponenter: ett användargränssnitt, ett applikationslager, en databas och ibland en integrationslösning eller en kö. Runt detta fanns infrastruktur för nätverk, lastbalansering, säkerhetskopiering, övervakning och drift. I stället för att många små tjänster kommunicerade med varandra över nätverket utgjorde större delen av logiken ett sammanhållet system med relativt få externa beroenden.

Det betydde inte att systemen var små. Tvärtom kunde de vara mycket omfattande. Det som gjorde dem hanterbara var att de ändå gick att beskriva som ett avgränsat system med en tydlig teknisk och organisatorisk insida och utsida.

## En typisk teknisk arkitektur

Den klassiska modellen varierade mellan organisationer, men den följde ofta ett liknande mönster. Användare nådde systemet via webbläsare eller klienter. Trafiken passerade en eller flera nätverksgränser och togs emot av en lastbalanserare eller webbserver. Därefter gick anropen vidare till ett applikationslager, som innehöll verksamhetslogiken och i praktiken var systemets kärna. Applikationslagret använde en databas för att lagra information och kunde också ansluta till integrationskomponenter, exempelvis filöverföring, batchjobb eller meddelandeköer.

I många fall låg flera delar av lösningen i samma driftmiljö och ibland även på samma eller ett begränsat antal servrar. Även när miljön bestod av flera virtuella eller fysiska servrar uppfattades den fortfarande som ett sammanhållet system. I beställningen till driftsorganisationen kunde man därför beskriva behovet i termer av ett system eller en applikation, inte i termer av många enskilda tjänster.

Det fanns ofta ett tydligt tänk kring nätverkszoner. Extern trafik kunde släppas in till vissa delar, medan applikationsservrar och databaser placerades längre in i infrastrukturen. Den modellen gjorde det förhållandevis lätt att skapa en hanterbar perimeter runt systemet. Men en hanterbar perimeter är inte detsamma som att hela säkerhetsproblemet är löst. Om ett system väl hade passerat sin yttre gräns kunde den interna tilliten fortfarande vara hög och de interna skydden svagare än man först trodde [K001].

Den traditionella modellen behöver förstås både som en teknisk helhet och som ett sätt att organisera ansvar. När ett IT-stöd kunde behandlas som en sammanhållen leveransenhet blev samspelet mellan utveckling, central drift, säkerhet och förvaltning förhållandevis begripligt.

## Ett sammanhållet system gav en sammanhållen beställning

En central styrka var att ett nytt eller förändrat IT-stöd ofta kunde beskrivas med ett begränsat antal infrastrukturella behov. Driftsorganisationen behövde sätta upp servrar eller virtuella maskiner, operativsystem, databaser, applikationsservrar, nätregler, övervakning, säkerhetskopiering och ibland integrationskomponenter. När detta väl var gjort kunde utvecklingsteamet leverera sin applikation in i en i förväg begriplig miljö.

Beställningsmodellen passade därför väl i organisationer med tydliga roller. Utveckling specificerade vad applikationen behövde. Drift tillhandahöll en kontrollerad miljö. Informationssäkerhet eller infrastruktursäkerhet kunde ställa krav på nätverkssegmentering, hårdning, loggning och behörigheter. Förvaltningen tog ansvar för livscykel, prioriteringar, budget och relationen till verksamheten.

Det gick med andra ord att skilja mellan **applikationen** och **miljön som applikationen körde i**. Det var en viktig källa till ordning. Ansvarsgränsen blev inte alltid perfekt, men den var tillräckligt tydlig för att organisationen skulle veta vem som skulle göra vad när något behövde förändras.

## Hur ansvar brukar vara organiserat

Den traditionella modellen förstärkte ofta en klassisk ansvarsfördelning.

Utvecklingsorganisationen ansvarade för applikationens funktionalitet: verksamhetsregler, användargränssnitt, integrationslogik och datamodell. Arkitekturfunktionen satte principer för teknikval, återanvändning, integrationer och ibland informationsmodellering. Driftsorganisationen ansvarade för den tekniska miljön: servrar, operativsystem, databasmotorer, lastbalansering, backup, övervakning och återställning. Säkerhetsfunktioner granskade eller styrde skyddsåtgärder, särskilt kring nätverk, åtkomst och loggning. Förvaltningsorganisationen prioriterade förändringar och planerade releaser.

Detta skapade ibland ett tungrott maskineri, men det gav också flera fördelar. Specialiseringen var tydlig. Kompetenser gick att bygga upp över tid. Driftsorganisationen kunde standardisera sitt arbete eftersom många system beställde liknande typer av miljöer. För verksamheten gick det att peka ut en ansvarig för applikationen och en ansvarig för den tekniska driften.

Det här betyder inte att ansvaret alltid följde användarnyttan. Användaren bryr sig sällan om var gränsen går mellan applikation och infrastruktur. Men i en värld där ett IT-stöd kunde avgränsas ganska väl räckte denna ansvarsfördelning långt.

## Varför modellen fungerade väl

Det finns minst fem skäl till att den traditionella modellen blev så stabil och långlivad.

### 1. Systemgränsen var begriplig

När ett IT-stöd i huvudsak bestod av en större applikation med relativt få gränssnitt mot omvärlden var det lättare att förstå vad som hörde till systemet. Det förenklade design, drift, säkerhetsbedömning och incidenthantering.

### 2. Infrastruktur kunde standardiseras

Databaser, applikationsservrar, brandväggar, lastbalanserare och köer kunde erbjudas som återkommande byggblock. Standardisering i driftledet gjorde både leverans och förvaltning mer förutsägbara.

### 3. Förändringar gick att samordna

Större releasefönster kunde vara långsamma, men de var ofta tydligt planerade. Organisationen visste när testning, driftsättning och återställningsplaner skulle aktiveras. I miljöer med höga krav på kontroll kunde detta vara en styrka snarare än en svaghet [K002].

### 4. Säkerhetsansvaret kunde koncentreras

Eftersom mycket skydd byggdes upp kring miljön kunde drift- och säkerhetsfunktioner arbeta metodiskt med härdning, nätverksregler, åtkomst och övervakning. När samma typ av lösningar återkom gick det att höja kvaliteten stegvis.

### 5. Förvaltningen fick en tydlig motpart

Verksamheten hade ofta ett system eller ett förvaltningsobjekt att förhålla sig till. Prioriteringar, budget, planering och ansvar kunde knytas till något som uppfattades som stabilt över tid.

## Det som ofta var enklare än i senare generationer

Den traditionella modellen hade flera egenskaper som i dag ibland underskattas.

Det var till exempel ofta lättare att förklara **var** ett fel hörde hemma. Om ett användarflöde inte fungerade kunde man i hög grad felsöka inom ett tydligt system och dess närmiljö. Beroenden fanns förstås till andra lösningar, men de var ofta färre och tydligare definierade än i senare distribuerade miljöer.

Det var också lättare att resonera om prestanda och kapacitet. Om applikationen blev långsam undersökte man databasen, applikationsservrarna, nätverket eller lastbalanseringen inom samma lösning. Problemen kunde vara komplexa, men de var inte lika ofta resultatet av många små tjänsters samlade beteende.

En annan styrka var att mycket driftkompetens gick att återanvända. Om driftsorganisationen hade lärt sig hur en viss databasmotor eller applikationsserver skulle installeras, övervakas, säkras och återställas kunde den kunskapen användas för många system. Det skapade skalfördelar i en tid då infrastrukturen ofta var mer heterogen och manuellt administrerad än i dag.

## Begränsningar och dolda problem

Det är dock viktigt att inte idealisera den traditionella modellen. Dess styrkor hade nästan alltid en baksida.

### Tätt kopplad intern struktur

Ett sammanhållet system är inte automatiskt välmodulerat. Många monoliter växte över tid och fick täta kopplingar mellan funktioner, svårtestade beroenden och omfattande regressionstestning inför varje större release. Det kunde göra utveckling långsam även när driftsmiljön i sig var stabil.

### Stora releaser och höga samordningskostnader

När många förändringar samlades i samma leverans ökade både väntetid och risk. Ett fel i en del av systemet kunde fördröja allt annat. Ju större releaserna blev, desto större blev behovet av koordinerad testning, godkännande och förändringsberedskap [K002].

### Infrastruktur som flaskhals

Standardisering i drift var effektiv så länge behoven var relativt lika. Men när utvecklingssidan ville införa nya tekniker, nya driftsmönster eller fler specialiserade beroenden kunde samma standardisering upplevas som en begränsning. Det som tidigare varit ordning kunde då i stället framstå som långsamhet.

### Perimeterskydd gav inte hela svaret

Modellen byggde ofta på antagandet att systemet kunde skyddas genom tydliga nätverksgränser. Det fungerade till viss del, men moderna säkerhetsramverk påminner om att intern tillit också måste granskas. Identitet, behörighet, loggning och principen om minsta privilegium behöver tillämpas även inom systemets inre delar [K001].

### Förvaltningen kunde bli tung

När systemen blev äldre riskerade de att få lång livslängd, många anpassningar och ett växande beroende av specialistkunskap. Det gav stabilitet men också tröghet. Vissa system blev så affärskritiska att varje större förändring upplevdes som riskfylld i sig.

## Ett återkommande missförstånd: monolit betyder inte dålig arkitektur

I senare debatter har ordet *monolit* ibland använts nästan som ett skällsord. Det är olyckligt. En monolit är i grunden bara ett system där stora delar av lösningen utvecklas, testas och driftsätts tillsammans. En välstrukturerad monolit kan vara både snabb att utveckla och enkel att drifta. Den kan ge hög kvalitet, låg operativ komplexitet och tydligt ansvar – särskilt när verksamhetsdomänen ännu inte motiverar en mer distribuerad lösning.

Det avgörande är därför inte om ett system är monolitiskt eller distribuerat i sig. Det avgörande är om arkitekturen passar problemets natur, organisationens kompetens och de operativa krav som faktiskt gäller.

## När modellen fortfarande är ett gott val

Det är frestande att beskriva generation 1 som något organisationer lämnar bakom sig för gott. Det vore en förenkling.

Den traditionella modellen är fortfarande rimlig när flera av följande villkor gäller:

- IT-stödet är sammanhållet och domänen kräver inte oberoende skalning eller fristående livscykler för många delkomponenter.
- Organisationen har höga krav på förutsägbar drift, kontrollerade förändringsprocesser och tydliga beställningsvägar.
- Förändringstakten är måttlig eller koncentrerad till vissa tillfällen snarare än kontinuerlig.
- Kompetensen och verktygen för distribuerad drift, observerbarhet och automatiserad plattform ännu inte finns på plats.
- En enklare arkitektur ger mer värde än en mer flexibel men mer komplex leveransmodell.

För stora, långlivade och stabila verksamhetsstöd kan generation 1 därför fortfarande vara helt rationell. Det gäller särskilt när alternativet vore att införa distribuerad komplexitet utan att de organisatoriska eller tekniska förutsättningarna finns.

## När modellen börjar bli otillräcklig

Samtidigt finns tydliga tecken på att modellen inte längre passar lika bra.

Ett sådant tecken är när många utvecklingsteam behöver arbeta parallellt men hindras av att allt måste samordnas i samma releasecykel. Ett annat är när olika delar av systemet förändras i så olika takt att den gemensamma livscykeln blir ett återkommande problem. Ett tredje tecken är när integrationer, variationer i last eller krav på snabb experimentering växer snabbare än den centrala drift- och beställningsmodellen kan hantera.

Det betyder inte automatiskt att nästa steg måste vara mikrotjänster. Men det betyder ofta att organisationen behöver fundera på hur den ska öka modularitet, automatisering och teamens självständighet utan att förlora överblicken.

Det är den frågan som nästa kapitel tar vidare.

## Konkreta exempel eller fall

Föreställ dig ett ärendehanteringssystem i en större myndighet eller koncern. Systemet används av interna handläggare via webbläsare. Ärenden, dokument, beslut och historik lagras i en relationsdatabas. Integrationer mot identitetstjänst, dokumentarkiv och ett ekonomisystem hanteras via ett begränsat antal tydliga gränssnitt. Driftsorganisationen tillhandahåller den tekniska miljön, databasen, övervakningen och säkerhetskopieringen. Utvecklingsteamet levererar ny funktionalitet ett fåtal gånger per år, samordnat med testning, releaseplanering och driftberedskap.

I en sådan miljö kan generation 1 fungera mycket väl. Ansvaret är tydligt, miljön är känd och varje förändring kan förberedas noggrant. Men om samma organisation senare vill att flera team ska förändra olika delar av lösningen varje vecka börjar modellen kännas trång. Det är alltså inte systemets ålder i sig som avgör, utan skillnaden mellan vad modellen är bra på och vad verksamheten nu vill uppnå.

## Centrala fakta

- Den traditionella IT-modellen organiserar ofta ett IT-stöd som en sammanhållen leveransenhet.
- Teknisk arkitektur och organisatoriskt ansvar passar ofta väl ihop när systemgränsen är tydlig.
- Modellen gör det relativt enkelt att standardisera driftmiljöer, nätverkszoner och beställningsvägar.
- En tydlig nätverksperimeter gör skyddsarbetet mer hanterbart, men den löser inte alla säkerhetsfrågor [K001].
- Monolitiska system är inte per definition dåliga; de kan vara ett ändamålsenligt val när kraven passar modellen.

## Begrepp att känna till

- **Monolit:** Ett system där stora delar av funktionaliteten utvecklas, testas och driftsätts tillsammans.
- **Perimeter:** Den yttre skyddsgräns som avskiljer ett system eller en miljö från omgivningen.
- **Applikationsserver:** Den miljö där verksamhetslogiken körs.
- **Lastbalanserare:** En komponent som fördelar trafik mellan flera instanser eller noder.
- **Förvaltningsobjekt:** Ett organisatoriskt objekt som samlar ansvar för verksamhetsnytta, prioritering och livscykel.

## Sammanfattning

Den traditionella IT-modellen fungerade väl därför att teknik, drift och ansvar hängde ihop kring ett sammanhållet system. Det gjorde det möjligt att standardisera infrastrukturen, skydda lösningen med tydliga nätverksgränser och organisera ansvar mellan utveckling, drift, säkerhet och förvaltning på ett begripligt sätt.

Samtidigt fanns tydliga begränsningar: stora releaser, tät intern koppling, tung samordning och en säkerhetsmodell som ibland byggde för mycket på den yttre perimetern. Därför är generation 1 varken ett ideal eller ett misslyckande. Den är en stark modell i rätt sammanhang – och en otillräcklig modell när förändringsbehov, skala och organisatoriska mål börjar kräva något annat.
