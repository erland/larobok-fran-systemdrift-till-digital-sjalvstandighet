# 2. Förflyttningen till distribuerade IT-stöd

När ett sammanhållet IT-stöd börjar bromsa utvecklingen kan det vara lockande att dela upp det i mindre delar. Tanken är begriplig: om en förändring bara berör ärendehanteringen, varför ska den behöva samordnas med förändringar i fakturering, dokumenthantering och rapportering? Om en viss funktion får kraftigt ökad belastning, varför ska hela systemet skalas upp?

Det är ungefär här övergången till en mer distribuerad arkitektur brukar börja. Men den avgörande frågan är inte hur många tjänster ett system bör bestå av. **Frågan är vilka beroenden som hindrar organisationen från att förändra och leverera IT-stödet på ett säkert och ändamålsenligt sätt.** En uppdelning är värdefull först när den minskar dessa hinder mer än den tillför nya.

I föregående kapitel var ett IT-stöd en relativt tydlig teknisk och organisatorisk leveransenhet. Nu förändras den förutsättningen. Funktioner som tidigare delade kod, process och databas kan få egna livscykler, API:er och driftsmiljöer. Förändringen öppnar för större självständighet, men för också med sig fler nätverksberoenden, fler versioner och ett större behov av samordning. Det är alltså lika mycket en förflyttning av **ansvar och arbetssätt** som av teknik.

## Varför vill man dela upp ett fungerande system?

De vanligaste motiven är inte att en monolit är fel i sig. De uppstår när flera delar av systemet behöver utvecklas på olika villkor.

Ett system kan exempelvis växa så att många team arbetar i samma kodbas och behöver vänta på varandras tester och releaser. Det kan finnas funktioner som ska ändras dagligen medan andra helst ska lämnas orörda under längre perioder. Vissa delar kan kräva hög kapacitet under korta belastningstoppar, medan andra har jämn och begränsad användning. Olika verksamhetsområden kan också behöva tydligare ansvar för sina egna processer och tjänster.

Då blir oberoende förändring ett värde i sig. En tjänst som kan ändras, testas och driftsättas utan att andra tjänster måste ändras samtidigt kan minska väntetid och koordinering. Att kunna driftsätta självständigt är dock inte samma sak som att varje ändring måste göras tillgänglig för användarna omedelbart; organisationen kan fortfarande styra när en funktion aktiveras. DORA beskriver detta som en kombination av löst kopplad teknik och löst kopplade team: arkitekturens främsta nytta visar sig i vad teamen faktiskt kan åstadkomma självständigt [K007].

Det betyder inte att alla funktioner behöver brytas ut. Om en förändring i praktiken alltid måste följas av förändringar i flera andra delar kan en uppdelning snarare skapa mer arbete. Tjänster som ser oberoende ut på arkitekturbilden kan vara starkt beroende av varandra i verkligheten.

## Den tekniska förändringen: från interna anrop till externa kontrakt

I ett sammanhållet system kan en funktion anropa en annan direkt i samma process. Data kan hanteras i samma transaktion, och ett gemensamt bygge säkerställer att funktionerna använder kompatibla versioner. När funktioner flyttas till separata tjänster behöver sådana antaganden omprövas.

En typisk förflyttning börjar med att systemets verksamhetsområden avgränsas. Det kan handla om ärendeprocessen, dokumenthantering, aviseringar och rapportering. Varje område får tydliga gränssnitt mot andra. **Ett API är då inte bara en teknisk anslutning: det är ett kontrakt om vad en tjänst lovar sin omgivning.**

Därefter behöver man avgöra hur kommunikationen ska fungera. Vissa behov passar ett direkt anrop, där den ena tjänsten inväntar svar från den andra. Andra passar händelser eller meddelanden, där en tjänst meddelar att något har hänt utan att alla mottagare behöver svara omedelbart. Båda modellerna har styrkor och kostnader.

Även dataansvaret förändras. Om flera tjänster fortfarande skriver direkt i samma databas kan deras interna datamodeller binda dem hårt till varandra. Samtidigt kan en alltför snabb uppdelning av data skapa problem med konsistens, rapportering och transaktioner. Den viktiga principen är därför att göra **ägarskapet till data tydligt** och välja teknik och övergångssätt efter kraven, inte efter en dogm om att varje tjänst alltid måste ha en egen databasserver. En egen logisk datamodell eller ett tydligt skrivansvar kan vara viktigare än fysisk separation av databasservrar. Microsofts arkitekturriktlinjer lyfter fram just datakonsistens, kommunikation och oberoende driftsättning som centrala avvägningar [K008].

Den centrala förändringen är att verksamhetsfunktionerna inte behöver bli fler, men deras **tekniska gränser** blir fler. När en intern funktionsgräns blir en nätverksgräns tillkommer krav som inte tidigare var lika framträdande.

## Nya förmågor som måste finnas på plats

Att dela upp en applikation kan göras med relativt enkla kodförändringar. Att hålla många självständiga tjänster fungerande över tid är betydligt svårare. Följande förmågor bör därför byggas upp parallellt med eller före uppdelningen.

### Modularitet och begripliga tjänstegränser

Innan kod flyttas till separata processer behöver organisationen förstå verksamhetens gränser. Om en tjänst ständigt måste fråga andra tjänster om deras interna data blir den inte självständig. En bra början kan därför vara att strukturera om den befintliga monoliten i tydliga moduler och definiera vilka gränssnitt som är stabila.

Detta är också ett sätt att pröva arkitekturen innan organisationen tar kostnaden för distribuerad drift. Om modulerna fortfarande ändras tillsammans eller har oklara ansvar är det ofta för tidigt att göra dem till egna tjänster.

### Automatisk byggning, testning och driftsättning

När ett system består av flera driftsättbara delar blir manuella releaser snabbt svåra att koordinera. Varje tjänst behöver en repeterbar leveransväg med byggning, tester, versionsmärkning och kontrollerad driftsättning. Gränssnitt bör kunna testas genom kontraktstester så att förändringar inte oavsiktligt bryter konsumenter. Databasscheman och API:er behöver kunna förändras på ett bakåtkompatibelt sätt under övergångsperioder.

DORA:s forskning om kontinuerlig leverans beskriver testautomation, driftsättningsautomation och korta återkopplingscykler som viktiga för att säkert kunna göra förändringar ofta [K009]. Det är värdefullt även för monoliter; fler tjänster gör bara beroendet av dessa förmågor tydligare.

### Snabb och förutsägbar tillgång till driftmiljöer

Om varje ny tjänst kräver en lång serie manuella beställningar för servrar, nätverksregler, databaser och övervakning ökar ledtiderna trots att själva koden blivit mer uppdelad. Organisationen behöver kunna skapa och ändra miljöer repeterbart och med tydliga standardkrav. Det kan börja med automatiserade mallar och väl definierade beställningar; en fullt utbyggd självbetjäningsplattform behöver inte vara första steget.

Redan i en tidig beskrivning av mikrotjänsters förutsättningar betonade Martin Fowler snabb provisionering, grundläggande övervakning och snabb driftsättning samt nära samarbete mellan utveckling och drift [K010]. Dessa är förutsättningar för att modellen ska fungera, inte något man tryggt kan vänta med tills hundratals tjänster redan finns.

### Synlighet i en distribuerad helhet

I en monolit kan ett fel ofta undersökas inom samma process eller applikationsmiljö. I ett distribuerat system kan ett användarflöde passera flera tjänster. Loggar och mätvärden behöver därför kunna kopplas till samma händelsekedja, samtidigt som det finns en bild av tjänsternas beroenden och tillgänglighet.

Här blir tre begrepp användbara: *loggar* beskriver händelser, *mätvärden* visar utveckling över tid och *spårning* gör det möjligt att följa ett anrop genom flera komponenter. Tekniken har störst nytta när den kopplas till de användarflöden som verksamheten vill skydda.

### Identitet, behörighet och kommunikationssäkerhet

När komponenter kommunicerar över nätverk behöver organisationen avgöra vem som får anropa vad, hur tjänster identifierar sig, hur hemligheter lagras och hur nätverkstrafik begränsas. En intern anslutning ska inte automatiskt vara betrodd. Men det betyder inte heller att alla säkerhetsfunktioner ska skrivas om i varje applikation: mycket bör erbjudas som gemensamma tekniska förmågor [K001].

### Felhantering, återställning och datakonsistens

Distribuerade tjänster måste klara att nätverksanrop tar längre tid, att en beroende tjänst är otillgänglig eller att samma meddelande levereras mer än en gång. Tidsgränser, kontrollerade återförsök, idempotens och köhantering blir därför viktiga. En tjänst kan behöva fortsätta erbjuda delar av sin funktion även om andra delar tillfälligt inte fungerar.

För dessa frågor räcker det inte att driftmiljön är redundant. Applikationens verksamhetslogik måste också avgöra vilka fel som kan tolereras, vilka som måste stoppas och vad som behöver återställas.

## Organisationsförändringen börjar före den nya organisationskartan

En uppdelad arkitektur kan inte fungera väl om ingen äger gränserna mellan delarna. Det betyder dock inte att allt ansvar behöver flyttas till utvecklingsteamen på en gång.

När tjänster får egna leveransflöden behöver utvecklingsteamen mandat att ändra dem och ansvar för hur deras ändringar påverkar produktion. De bör förstå tjänstens loggar, felbeteenden, beroenden och återställningsbehov. Driftsorganisationen fortsätter att ansvara för gemensamma miljöer och tekniska tjänster, men behöver bli delaktig i utformningen av automatiserade leveransvägar. Säkerhetsfunktionen behöver tydliggöra obligatoriska kontroller för tjänsteidentitet, data och kommunikation. Arkitekturfunktionen behöver lägga större vikt vid gränssnitt, informationsägarskap och beroenden än vid detaljbeslut inne i varje komponent.

Den största förändringen är alltså inte vem som äger en server. Den är att **ett team som vill leverera självständigt också behöver kunna bära ett tydligt ansvar för sin tjänsts beteende**, utan att ansvaret för hela IT-stödet försvinner. Förvaltningen behöver fortfarande någon som kan prioritera användarens sammanhållna behov och förstå konsekvenser när flera team behöver samverka. Det behövs också ett i förväg utpekat ansvar för samordning vid incidenter som berör flera tjänster; annars kan varje del vara väl omhändertagen samtidigt som ingen har mandat att återställa användarens helhet.

DORA:s beskrivning av löst kopplade team betonar förmågan att testa, ändra och leverera utan ständig detaljkoordinering med andra [K007]. Detta är ett relevant mått på om organisationsförändringen faktiskt fungerar. Om teamen har fått egna tjänster men fortfarande måste planera varje release tillsammans, kan mycket av den tänkta nyttan ha uteblivit.

## Förflyttningen i vårt ärendehanteringssystem

Det fiktiva ärendehanteringssystemet från föregående kapitel ska nu kunna förändras snabbare. Verksamheten vill utveckla nya ärendeflöden oftare, samtidigt som aviseringar behöver skalas upp vid stora utskick. Dokumenthanteringen styrs av särskilda regler och förändras mer sällan.

Organisationen börjar inte med att riva upp allt. Den identifierar tre funktionsområden: **ärenden**, **dokument** och **aviseringar**. Först görs gränserna tydliga inne i den befintliga applikationen. Utvecklarna skapar tester runt gränssnitten och synliggör vilken information respektive del äger. När aviseringarna visar sig behöva en egen livscykel kan den funktionen flyttas ut till en separat tjänst. Ärendefunktionen kan publicera en händelse när något viktigt inträffar; aviseringstjänsten tar emot händelsen och sköter utskicken utan att ärendehanteringen behöver vänta på att alla mottagare nåtts.

Det är en begränsad uppdelning med ett tydligt mål. Om lösningen fungerar kan dokumentområdet senare prövas på samma sätt. Om den nya tjänsten visar sig öka samordningen mer än den ökar självständigheten bör gränserna omprövas. Det är arkitekturens effekt som ska styra, inte antalet tjänster på ett diagram.

## När är förflyttningen värd att starta?

Det finns ingen universell miniminivå där mikrotjänster plötsligt blir rätt. Däremot finns flera tecken som talar för att organisationen bör utreda en uppdelning:

- En gemensam releasecykel skapar återkommande väntetider mellan team som annars skulle kunna leverera var för sig.
- Vissa funktioner har väsentligt olika förändringstakt, krav på kapacitet eller tillgänglighet.
- Det går att identifiera verksamhetsmässigt sammanhållna delar med tydliga gränssnitt och dataansvar.
- Organisationen kan bygga och driftsätta tjänster repeterbart, observera dem i produktion och hantera incidenter över teamgränser.
- Den förväntade nyttan går att beskriva och följa upp, exempelvis kortare ledtid för en avgränsad funktion eller färre samordnade releaser.

Det är särskilt viktigt att skilja en verklig leveransbegränsning från ett önskemål om att införa modern teknik. Om problemet i första hand är otydlig kodstruktur, långsam testning eller tung förändringsstyrning finns det ofta enklare förbättringar att börja med.

## När är det för tidigt – och vad gör man i stället?

Det kan vara för tidigt när utveckling och drift saknar en gemensam modell för incidenter och förändringar, när det tar lång tid att skapa en driftsmiljö, när tester huvudsakligen är manuella eller när tjänstegränserna är så otydliga att alla delar fortfarande måste ändras samtidigt. Då riskerar fler driftsättbara komponenter att bara skapa fler beställningar och mer friktion.

I sådana situationer är en **modulär monolit** ofta ett rimligare steg. Den behåller gemensam driftsättning men skapar tydliga interna gränser mellan verksamhetsområden. Samtidigt kan organisationen utveckla automatisk testning, versionshantering, snabbare miljöleveranser, bättre övervakning och en tydligare ansvarsfördelning.

Det finns också situationer där den traditionella modellen bör behållas utan större förändring. Om systemet är stabilt, verksamhetskraven förändras långsamt och en uppdelning inte ger tydlig nytta kan en distribuerad lösning innebära högre kostnad och större risk utan motsvarande värde. Bedömningen bör göras utifrån IT-stödets uppgift, inte utifrån en förmodad teknisk mognadsskala.

## En praktisk beslutsgrind

Innan ett större uppdelningsarbete startar bör ledningen, arkitektur, utveckling, drift och förvaltning kunna ge ett rimligt svar på fem frågor:

1. **Vilket konkret problem ska uppdelningen lösa?** Exempelvis beroenden mellan team, behov av separat skalning eller oberoende releaser.
2. **Vilka gränser kan göras självständiga?** Finns tydliga verksamhetsfunktioner, dataägare och kontrakt?
3. **Vilka driftförmågor finns redan?** Kan en tjänst byggas, testas, övervakas, säkras och återställas utan improvisation?
4. **Vem ansvarar för del och helhet?** Är både tjänsteägarskap, incidentledning över tjänstegränser och ansvar för användarens sammanhållna IT-stöd tydliga?
5. **Hur vet vi om förändringen lyckades?** Vilka ledtider, driftutfall, kostnader och kvalitetsmått ska följas upp?

**Beslutsutfall:** Finns ett uppmätt hinder, avgränsade tjänster, fungerande leverans och övervakning samt ansvar för både tjänst och helhet kan en begränsad uppdelning prövas. Saknas tydliga gränser bör man först modularisera monoliten; saknas driftförmåga bör man först automatisera tester, driftsättning och felsökning; saknas ansvar bör mandat och incidentledning klarläggas. Microsofts vägledning rekommenderar att applikation, infrastruktur, leveransförmåga och team bedöms före större förändring [K011].

## Vad går förlorat – även när förändringen lyckas?

En distribuerad arkitektur kan ge teamen större handlingsfrihet, men den tar bort en del av de enkelheter som generation 1 hade. Det är inte längre självklart att ett fel kan lokaliseras till en enda process. En användartransaktion kan omfatta flera tjänster, och säkerhetsgränserna blir fler. Antalet versioner och driftsmiljöer ökar. Det kan bli svårare att förstå kostnader, hantera datakonsistens och bevara en samlad bild av IT-stödet.

De nya problemen är inte argument mot all uppdelning. De är kostnader som måste vägas mot den självständighet organisationen vill uppnå. En tekniskt lyckad uppdelning är inte nödvändigtvis en verksamhetsmässig förbättring.

Det är också här nästa del av boken tar vid. När utvecklingssidan har delat upp systemen men drift och förvaltning fortfarande är organiserade för ett fåtal stora leveransenheter kan en ny friktion uppstå. Varje team kan få sin egen tjänst, men organisationen behöver ändå ta ansvar för den helhet som användaren möter.

## Sammanfattning

Förflyttningen från en sammanhållen applikation till distribuerade tjänster motiveras främst av behovet av oberoende förändring, skalning och ägarskap. För att nyttan ska uppstå måste uppdelningen bygga på verkliga verksamhetsgränser och kombineras med testautomation, säker driftsättning, övervakning, tydliga tjänstekontrakt och ett utvecklat samarbete mellan utveckling och drift.

Den avgörande beslutsfrågan är inte om organisationen kan skapa fler tjänster, utan om den kan **driva och förändra dem mer självständigt utan att tappa kontrollen över helheten**. Om förutsättningarna saknas är en modulär monolit eller förbättrade gemensamma leveransförmågor ofta ett bättre nästa steg.
