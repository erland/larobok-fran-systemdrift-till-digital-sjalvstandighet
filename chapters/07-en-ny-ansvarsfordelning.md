# 7. En ny ansvarsfördelning

En gemensam plattform gör det möjligt för utvecklingsteam att beställa driftsmiljöer, databaser och andra tekniska förmågor utan ett separat införandeprojekt varje gång. Men självbetjäning förändrar inte ansvaret av sig själv. En organisation kan automatisera alla beställningar och ändå stå med samma gamla fråga när ett viktigt IT-stöd slutar fungera: vem tar ledningen, vem fattar beslut och vem ser till att verksamheten får tillbaka sin tjänst?

Efter ansvarsglappen i kapitel 4 är frågan här hur **mandat, tjänsteägarskap och arbetssätt** konkret kan fördelas på en gemensam plattform. Det är inte fråga om att central drift ska avsäga sig ansvar eller att varje utvecklingsteam ska bli en liten driftavdelning. Ansvar behöver i stället läggas där problemen kan förstås och åtgärdas, samtidigt som gemensamma förmågor fortsätter att styras professionellt.

## Tre nivåer som inte får förväxlas

Det är användbart att skilja mellan tre nivåer. **IT-stödet** är det sammanhängande resultat som verksamheten behöver: exempelvis att ett ärende kan tas emot, handläggas och avslutas. **Applikationstjänsterna** utför delar av detta arbete: ärendehantering, dokument, sökning eller avisering. **Plattformstjänsterna** erbjuder den underliggande förmågan att köra, skydda, övervaka och återställa applikationerna.

Om ett av dessa lager fungerar betyder det inte automatiskt att de andra fungerar. En containerplattform kan vara tillgänglig samtidigt som ärendehanteringen ligger nere på grund av ett fel i verksamhetslogiken. Applikationen kan vara korrekt men ändå otillgänglig om dess databas inte går att nå. En lyckad säkerhetskopiering innebär inte heller att hela ärendehanteringen går att återställa inom den tidsgräns verksamheten behöver.

Därför bör organisationen definiera mål och ansvar på varje nivå – och dessutom utse någon som har mandat att hålla ihop det samlade IT-stödet.

## Sex roller, men inte nödvändigtvis sex avdelningar

Funktionerna nedan behöver finnas, men de behöver inte motsvara separata organisatoriska enheter. En mindre organisation kan förena roller; en större kan behöva specialiserade grupper. Det avgörande är att ansvar och beslutsvägar går att beskriva och använda.

**Produkt- eller tjänsteägaren** företräder verksamhetsvärdet. Rollen prioriterar funktion, budget och önskad tjänstekvalitet samt samordnar de delar som tillsammans ger användaren ett fungerande stöd. Beslut om riskacceptans måste däremot fattas av den roll som organisationens styrning faktiskt har gett mandat, exempelvis ansvarig verksamhets- eller informationsägare. Ägaren behöver kunna fatta prioriteringsbeslut även när flera utvecklingsteam och plattformstjänster berörs. Den behöver inte ha teknisk detaljkompetens i alla delar.

**Utvecklingsteamen** ansvarar för applikationernas beteende: kod, tester, informationsflöden, beroenden, konfiguration och hur den egna tjänsten fungerar i produktion. Teamen behöver kunna felsöka och förstå följderna av egna förändringar. Däremot behöver de inte själva drifta varje underliggande teknisk produkt.

**Plattformsteamen** erbjuder gemensamma förmågor som en långsiktig intern produkt. De ansvarar för standardvägar, automatisering, dokumentation, självbetjäningsgränssnitt, plattformens uppdateringar och den support och de tillgänglighetsmål som utlovas. CNCF:s mognadsmodell betonar just att plattformar behöver produktledning, användaråterkoppling och långsiktigt underhåll – inte bara teknisk installation [K014].

**Drift- och infrastrukturfunktionen** kan vara en del av plattformsteamet eller en separat leverantör. Den ansvarar för underliggande nät, beräkningskapacitet, lagring och specialiserad drift där sådan finns. Den fortsätter att vara nödvändig även när utvecklingsteamen får självbetjäning. Skiljelinjen mellan plattform och drift bör beskrivas som en tjänstegräns, inte som en otydlig överlämning.

**Arkitekturfunktionen** ska främst säkerställa att olika team kan bygga lösningar som fungerar tillsammans över tid. Hit hör principer för identitet, informationsutbyte, dataägarskap, interoperabilitet, livscykler och gränser mellan tjänster. Arkitekter kan bidra nära teamen och behöver inte godkänna varje teknisk detalj. DORA framhåller att teamens förmåga att ändra och leverera utan omfattande beroenden är central, oberoende av teknisk plattform [K007].

**Säkerhetsfunktionen** definierar riskbaserade krav, stödjer riskbedömning och följer upp efterlevnad. Den äger inte automatiskt alla tekniska säkerhetsåtgärder. Plattformen kan verkställa exempelvis nyckelhantering och nätverkspolicyer; applikationsteamet kan ansvara för behörighetslogik och säker kod; informationsägaren kan besluta om vilka uppgifter som får behandlas. NIST:s DevSecOps-vägledning stödjer integration av säkerhetskontroller i utveckling och drift, snarare än enbart sena kontrollpunkter [K015].

En ansvarsmatris kan användas som diskussionsunderlag för att identifiera överlapp och luckor, men en viss RACI-modell eller rollfördelning passar inte alla organisationer. Särskilt vid incidenter måste ansvar anpassas efter faktiskt mandat, tjänstens kritikalitet och organisationens bemanning.

## Vem ansvarar när något går fel?

En ofta använd formulering är att den som bygger en tjänst också ska kunna driva den. Den pekar på ett viktigt samband mellan förändringsbeslut och konsekvenser i produktion. Men den är inte tillräcklig som ansvarskarta. Om ärendetjänsten ligger nere på grund av en avbruten anslutning till en gemensam databas behöver utvecklingsteamet kunna identifiera problemet – medan det kan vara plattformsteamet eller databasdriften som faktiskt kan åtgärda det.

En fungerande incidentmodell behöver därför ha både **en tekniskt ansvarig för varje del** och **en utsedd incidentledare för den samlade störningen**. Incidentledaren behöver mandat att kalla in relevanta team, samordna akuta åtgärder och hålla verksamheten informerad. Rollen kan rotera eller ligga i en central funktion. Den är inte nödvändigtvis samma person som permanent äger IT-stödet och bör ha tydliga eskaleringsvägar för beslut som innebär större verksamhetsrisk eller avsteg från ordinarie säkerhetskrav.

På samma sätt behöver större förändringar ett uttalat samordningsansvar. Teamen ska så långt möjligt kunna uppdatera sina tjänster oberoende, men förändringar som påverkar kontrakt, datamodeller eller flera verksamhetsflöden måste ändå planeras gemensamt. Målet är att minska onödig samordning, inte att låtsas att beroenden har försvunnit.

## Förvaltningens nya betydelse

En traditionell förvaltningsorganisation är ofta ordnad kring en applikation och dess årliga budget. I en plattformsorienterad miljö kan samma verksamhetsstöd konsumera många gemensamma tjänster som har egna produktägare, kostnader och förändringsplaner.

Det gör inte förvaltning överflödig. Tvärtom behöver någon fortsatt hålla samman verksamhetsnytta, informationskvalitet, prioriteringar, kontinuitetskrav och avveckling. Men förvaltningen behöver tydligare skilja mellan **att äga behovet av ett IT-stöd** och **att tekniskt förvalta varje komponent som stödet använder**.

Ett praktiskt exempel är avveckling. Om ett förvaltningsobjekt beslutar att en viss funktion inte längre behövs måste det finnas en väg att avsluta abonnemang på plattformstjänster, återkalla behörigheter, hantera information enligt bevarande- och gallringskrav samt avsluta övervakning och kostnadsföring. En plattform som är bra på att skapa resurser men dålig på att avveckla dem lämnar ett nytt förvaltningsproblem efter sig.

## Arkitektur: färre detaljgodkännanden, tydligare principer

När många team gör förändringar parallellt blir central granskning av varje designbeslut dyr och långsam. Ett alternativ är att skilja mellan tre sorters beslut.

**Gemensamma skyldigheter** behöver vara tydliga: exempelvis identitetshantering, informationsklassning, säkerhetsloggning, hantering av hemligheter och krav på återställning. De bör där det är möjligt genomföras i plattformens standardvägar och kontrolleras automatiskt.

**Lokala teknikval** kan utvecklingsteamen göra själva så länge de håller sig inom organisationens stödbara gränser och inte förändrar gemensamma kontrakt eller risker på ett oacceptabelt sätt.

**Avvikelser och tvärgående beslut** ska ha en begriplig väg för prövning. När ett team behöver något utanför standarden ska det gå att få ett tidsbundet undantag med dokumenterad risk, ägare och plan för uppföljning. Utan en sådan väg kan standardiseringen leda till dolda genvägar eller att verksamheten väljer lösningar helt utanför den gemensamma miljön.

Detta är inte samma sak som att avskaffa arkitekturstyrningen. Den flyttas från detaljstyrning av varje införande mot tydliga gemensamma regler, väl utformade kontrakt och stöd till teamen där deras beslut påverkar andra.

## Delat ansvar måste vara mätbart

Begreppet *delat ansvar* kan låta samarbetsinriktat men bli en källa till missförstånd om ingen vet vilken del som faktiskt hör till vem. Därför behöver varje viktig plattformsförmåga beskrivas med ett enkelt tjänstelöfte: vad levereras, vilka kvalitetsnivåer gäller, vad förväntas av användande team, vem svarar vid fel och hur hanteras förändringar?

Exempelvis kan plattformen tillhandahålla säkerhetskopiering med en viss teknisk frekvens. Den som ansvarar för IT-stödet behöver däremot formulera vilken dataförlust och återställningstid verksamheten accepterar. Applikationsteamet behöver säkerställa att den egna informationen och transaktionslogiken går att återställa konsekvent. Plattformen måste sedan kunna visa att den faktiskt kan leverera dessa mekanismer – och återställning behöver övas, inte bara dokumenteras.

Tillgänglighet bör följas upp på motsvarande sätt. Plattformens egen tillgänglighet är viktig, men användarens mål gäller den sammanhängande tjänsten. Ett användarflöde kan påverkas av en applikationsbugg även när plattformen är fullt tillgänglig. Målen behöver därför skiljas åt och kopplas samman genom kända beroenden. Sådana tjänstenivåmål och incidentrutiner är centrala verktyg i Site Reliability Engineering [K018].

Ett begränsat urval användbara mätetal är ofta bättre än en stor mängd mått utan tydliga beslutsägare: ledtid för en standardbeställning, andel automatiserade leveranser, felutfall och återställningstid för viktiga användarflöden, antal obesvarade ansvarsglapp, säkerhetsavvikelser samt plattformens faktiska användning och användarnöjdhet. Siffrorna behöver följas över tid och tolkas i sitt sammanhang.

## Exemplet: ärendehantering på en gemensam plattform

Återvänd till ärendehanteringsstödet i tidigare kapitel. Verksamheten vill att handläggare ska kunna registrera, söka och avsluta ärenden även när enskilda komponenter förändras. Två utvecklingsteam ansvarar för ärende- respektive dokumenttjänsten. Plattformsteamet tillhandahåller applikationsdrift, databas, identitet, nätverksregler, loggning och säkerhetskopiering. Säkerhetsfunktionen definierar bland annat krav utifrån informationsklassning och granskar undantag.

När dokumenttjänsten börjar svara långsamt kan dess utvecklingsteam först analysera mätvärden och spår. Om felet visar sig ligga i en gemensam lagringstjänst kopplas plattformsteamet in. Samtidigt håller en utsedd incidentledare samman lägesbild och kommunikation för hela ärendehanteringen. Produktägaren prioriterar eventuella tillfälliga begränsningar i funktionaliteten utifrån verksamhetens behov.

Ingen har då tagit över alla andras arbete. Skillnaden är att varje part vet **vilket resultat den ansvarar för, vad den måste bidra med och hur helheten samordnas**. Det är en mer robust ansvarsfördelning än att antingen central drift eller ett enskilt utvecklingsteam förväntas lösa allting.

## Fallgropar och förutsättningar

En plattformsorienterad ansvarsfördelning fungerar sämre om organisationen nöjer sig med att rita om organisationsschemat. Utvecklingsteam som förväntas bära produktionsansvar behöver få behörigheter, övervakning, utbildning och rimliga former för beredskap. Plattformsteam som förväntas erbjuda självbetjäning behöver tid, finansiering, produktledning och befogenhet att ändra sina tjänster. Säkerhetsfunktionen behöver kunna formulera genomförbara kontroller som inte alltid kräver manuell granskning.

Det är också möjligt att gå för långt. Om varje team förväntas kunna allt, försvinner skalfördelarna med gemensamma specialister. Om plattformsteamet styr varje detalj återuppstår däremot de gamla beställningsköerna. En fungerande modell behöver därmed tydliga standardgränser och ett aktivt samarbete snarare än ett försök att göra alla roller identiska.

Förändringen bör inte starta med ett generellt beslut om att flytta driftansvar. Börja hellre med ett begränsat antal tjänster, definiera ansvar för incidenter och förändringar, pröva självbetjäningsvägarna och följ upp vad som faktiskt blir enklare. Om plattformens driftsförmåga eller teamens produktionskompetens ännu är svag är det ofta klokare att först förstärka dessa förutsättningar.

## Det som förändras – och det som består

Det som förändras är framför allt **hur ansvar utövas**. Tekniknära beslut och vardaglig felsökning flyttas närmare dem som kan påverka respektive tjänst. Gemensamma förmågor blir tydligare produkter med användare och tjänstelöften. Arkitektur och säkerhet byggs i högre grad in i standardvägar och automatisk återkoppling.

Det som består är behovet av ansvariga för säkerhet, robust drift, ekonomi, informationshantering och verksamhetsnytta. Dessa frågor försvinner inte när en portal införs. De blir viktigare eftersom fler team kan göra förändringar själva.

Därför är det inte tillräckligt att fråga vem som "äger servrarna" eller vem som "äger koden". Den mer användbara frågan är: **vem kan fatta beslut och agera när kvaliteten på det sammanhängande IT-stödet påverkas?**

När den frågan har ett tydligt svar kan den plattformsorienterade modellen förena självständighet och kontroll. Det öppnar också för nästa förflyttning: att fler delar av verksamheten själva får tillgång till säkra digitala förmågor utan att behöva bli professionella drift- eller utvecklingsorganisationer.
