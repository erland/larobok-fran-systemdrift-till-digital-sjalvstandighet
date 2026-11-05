# 3. Den distribuerade IT-miljön

Ett utvecklingsteam får ansvar för ärendehantering, ett annat för dokument och ett tredje för aviseringar. Varje team kan bygga och leverera sin del utan att vänta på en gemensam release. Det är ungefär den självständighet som uppdelningen i föregående kapitel skulle skapa. Men när det nya arbetssättet blir vardag upptäcker organisationen något oväntat: driftsorganisationen får fler ärenden, säkerhetsgränserna blir svårare att definiera och det krävs mer kunskap för att förstå ett enda användarflöde.

Det är ingen motsägelse. **En arkitektur kan göra varje del enklare att förändra och samtidigt göra helheten svårare att drifta.** Den distribuerade IT-miljön kännetecknas just av detta. Komponenterna blir fler och ofta mindre, medan samordning, kommunikation och säkerhet får större betydelse.

Den andra generationen i bokens analysmodell är alltså inte liktydig med mikrotjänster på en viss teknisk plattform. Det är ett vanligt läge i större organisationer där utvecklingsarkitekturen har förändrats snabbare än driftens, säkerhetens och förvaltningens sätt att arbeta. Den kan innehålla containrar, virtuella maskiner, traditionella integrationsplattformar och molntjänster i olika kombinationer.

## Ett IT-stöd, många separata delar

I den traditionella modellen var IT-stödets systemgräns ofta en naturlig utgångspunkt för drift, nätverk och ansvar. I den distribuerade modellen kan samma IT-stöd bestå av många tjänster med egna byggprocesser, gränssnitt och driftsättningar. Användaren möter fortfarande ett ärendehanteringsstöd, men ett enda ärende kan passera identitetstjänst, ärendetjänst, dokumenttjänst, behörighetstjänst och en aviseringskö innan allt är klart.

En del kommunikation sker synkront: tjänst A väntar på svar från tjänst B. Andra utbyten sker asynkront via köer eller händelser. I praktiken blandas dessa former. Vissa tjänster har separata datalager. Andra använder gemensamma databasservrar eller delar till och med tabeller. Olika team kan ha valt olika ramverk och driftsätt, därför att det har varit rimligt för den enskilda leveransen.

Problemet är inte att det finns många komponenter i sig. Problemet uppstår när deras **beroenden och livscykler** inte längre följs åt. En ändring kan vara isolerad till en tjänst i koden men ändå bero på andra tjänsters versioner, certifikat, nätverksregler eller datamodeller. Microsofts arkitekturvägledning beskriver komplexitet, nätverkslatens, datakonsistens, styrning, versionshantering och observerbarhet som typiska avvägningar i mikrotjänstarkitektur [K008].

Samtidigt som det sammanhållna IT-stödet får fler anslutningar och tekniska gränser ökar antalet leveransenheter och kontaktytor. Den centrala driftsorganisationen kan ändå förväntas leverera och kontrollera varje del, ofta med arbetssätt som utvecklades för färre och större system.

## När lokala förbättringar blir en gemensam belastning

Det är lätt att förstå logiken bakom varje enskilt beslut. Ett team bryter ut en tjänst för att slippa samordna alla releaser. Ett annat väljer en separat databas för att få tydligt dataägarskap. Ett tredje inför en ny integrationskomponent för att minska beroenden till ett äldre system.

Varje beslut kan vara rationellt. Men summan blir inte automatiskt rationell. En ny tjänst innebär kanske ytterligare en miljö, en identitet, en driftsättningsprocess, en uppsättning hemligheter, ett antal nätverksregler, loggar, larm och en återställningsplan. Det arbete som tidigare behövdes för ett system kan nu upprepas för varje tjänst, även när uppgifterna i grunden liknar varandra.

Särskilt tydligt blir detta i organisationer med många driftbeställningar. Utvecklingsteamen vill snabbt ändra kapacitet, skapa testmiljöer och koppla ihop tjänster. Driften vill leverera säkert och förutsägbart men får ett ökande antal små, delvis unika uppdrag. Om varje uppdrag hanteras manuellt blir beställningsflödet ett växande hinder för båda sidor.

### Automation kan också skapa nya varianter

Automatisering är en naturlig reaktion. Men om varje team automatiserar sin egen uppsättning databaser, servrar och säkerhetsinställningar kan resultatet bli många välfungerande lokala lösningar som ändå är svåra att underhålla tillsammans. Organisationen har då automatiserat **variationerna** snarare än minskat dem.

En gemensam beställnings- och automationsmodell kan därför vara värdefull. Men först behöver de ansvariga komma överens om vilka egenskaper som faktiskt ska vara gemensamma. Den frågan återkommer i förflyttningen till generation 3.

## En annan typ av nätverkssäkerhet

I ett traditionellt system gick det ofta att formulera säkerhetsfrågan som: vilka användare och externa system behöver nå detta IT-stöd, och vilka tekniska gränser ska skydda dess interna delar? I en distribuerad lösning behöver man dessutom fråga: **vilka interna tjänster får nå vilka andra tjänster, med vilken identitet och för vilket ändamål?**

Brandväggar och segmentering fortsätter vara relevanta, men kan bli svårare att förvalta om alla interna anrop behöver en unik nätverksregel. För att minska antalet regler kan organisationen frestas att placera många tjänster i samma zon. Om en zon då tillåter bred kommunikation mellan tjänster blir gränsen grövre än den ursprungliga avsikten: en felkonfigurerad eller komprometterad tjänst kan få fler möjliga angreppsvägar.

Det är inte nätverkszoner som sådana som är problemet. Det är **skillnaden mellan den avsedda behörigheten och den faktiska kommunikationsmöjligheten**. Att flera tjänster delar en fysisk värd eller en molnplattform måste heller inte innebära att de delar nätverksbehörighet. Logisk segmentering, separata identiteter och konsekventa policyer kan fortfarande skapa tydliga skydd även på gemensam infrastruktur.

NIST:s vägledning om säkra mikrotjänster framhåller behovet av tjänsteautentisering, auktorisation, skyddad kommunikation, nyckelhantering, upptäckt av tjänster och motståndskraft mot fel [K012]. Det är en användbar påminnelse om att säkerhet behöver fungera mellan tjänster och inte bara vid IT-stödets ytterkant.

En vanlig fallgrop är att flytta alla dessa frågor till applikationskoden i varje team. En annan är att tro att ett service mesh eller en nätverksplattform automatiskt kan ta ansvar för verksamhetsregler och åtkomst till information. I praktiken behöver tekniken för kommunikationsskydd vara gemensam där det går, medan applikationen måste förstå vilka användare och processer som faktiskt ska få utföra en åtgärd.

## Samnyttjade servrar och licenskostnader

Många organisationer har goda skäl att samnyttja infrastruktur. Databasmotorer, integrationsplattformar, virtuella servrar och övervakning kan vara kostsamma att driva i helt separata miljöer. Vissa licenser eller specialistkompetenser gör det också naturligt att koncentrera resurserna.

Det som förr var ett mindre problem kan däremot bli svårt när tjänster från många team blandas på samma underliggande resurser. En tjänst behöver ändra sin konfiguration; en annan behöver ett annat underhållsfönster. Två team behöver olika versioner av samma produkt. Om många tjänster delar databasinstans kan en resursbrist eller uppgradering påverka flera IT-stöd samtidigt.

Här behöver man skilja mellan tre saker: **ekonomiskt samnyttjande**, **teknisk isolering** och **operativt ägarskap**. De behöver inte vara samma gräns. En välutformad plattform kan använda samma fysiska resurser men hålla logiska säkerhets- och åtkomstgränser isär. Om organisationen i stället förlitar sig på gemensamma operativsystem, breda konton eller stora tillåtande zoner kan besparingen bli köpt till priset av större samrisk.

Det finns heller inget generellt svar på vilken resurs som bör delas. En central licensierad databasmotor kan vara rimlig för vissa system, medan andra tjänster vinner på lättare datalager med egen livscykel. Arkitekturvalet måste väga ekonomi mot separation, kompetens och återställningskrav. CNCF:s undersökning om luckor i det molnnativa ekosystemet 2024 lyfter fram säkerhet, kostnadshantering, kompetens, komplexitet, interoperabilitet och observerbarhet som återkommande problemområden [K004]. Undersökningen beskriver erfarenheter bland molnnativa utvecklare, inte en generell fördelning för alla större organisationer.

## Robustheten avgörs av kedjan, inte av varje server

Anta att varje teknisk komponent är redundant. Två instanser av ärendetjänsten finns i olika noder, databasen har replikering och köplattformen har flera servrar. Det låter robust. Men om handläggaren inte kan öppna ett ärende när dokumenttjänsten har problem är användarens IT-stöd ändå otillgängligt för den uppgiften.

**Systemets användbara tillgänglighet bestäms av de beroenden som krävs för just det användarflödet**, inte bara av om varje infrastrukturkomponent rapporterar grönt. Ett synkront anrop som väntar länge kan skapa följdfel i tjänster uppströms. Många återförsök kan överbelasta en redan svag beroende tjänst. Ett felaktigt meddelande kan fastna i en kö och påverka senare ärenden. Samtidigt kan asynkron kommunikation ge bättre isolering, men då uppstår frågor om fördröjning och datakonsistens.

Därför behöver driftsorganisationens redundans kompletteras med applikationsnära felhantering: tidsgränser, kontrollerade återförsök, möjlighet att hantera ofullständiga svar, idempotens och ibland en säker reservfunktion. En del av dessa mekanismer kan tillhandahållas i kommunikationsplattformen. Andra kräver kunskap om vad verksamheten kan acceptera. NIST behandlar exempelvis lastbalansering, begränsning av trafik och circuit breaking som relevanta tekniska mekanismer för mikrotjänsters tillgänglighet [K012].

Det här är en viktig ansvarsförändring. Drift kan garantera att en plattform levererar det den lovar, men kan inte ensamt garantera att ett användarflöde fungerar när verksamhetslogiken spänner över många beroenden.

## Data och kompatibilitet skapar särskilda beroenden

I en monolit genomfördes många ändringar inom samma databastransaktion. I den distribuerade miljön kan olika tjänster behandla samma verksamhetshändelse vid olika tidpunkter. Det kan vara fullt acceptabelt för aviseringar men mer problematiskt för ekonomiska beslut eller rättsligt betydelsefull ärendestatus.

Tjänsterna behöver därför tydliga kontrakt för data, ändringar och fel. Det innebär inte alltid att varje tjänst måste ha en egen fysisk databasserver. Däremot bör det vara begripligt vilken tjänst som äger en viss information och hur andra får använda den. Direktåtkomst till varandras tabeller kan minska utvecklingsfriheten eftersom en intern schemaändring påverkar flera team [K013].

Bakåtkompatibilitet blir också en vardagsfråga. Om dokumenttjänsten får en ny version måste ärendetjänsten kunna fortsätta fungera under övergången. Det påverkar API:er, meddelandeformat, datamodeller och hur länge gamla klienter behöver stödjas. De enskilda teamens kortare leveranscykler skapar alltså ett större behov av samordnad kontraktsstyrning – inte nödvändigtvis av gemensamma releaser.

## Driftens och utvecklingens olika bilder av samma problem

Ur utvecklingsteamets perspektiv kan tjänsteuppdelningen vara en framgång: mindre kodbaser, kortare utvecklingscykler och möjlighet att införa förändringar utan att samla hela organisationen. Ur driftsorganisationens perspektiv kan samma förändring se ut som ett växande antal miljöer, undantag, larm, tekniska produkter och nätverksberoenden.

Båda perspektiven kan vara korrekta. Driften kan uppleva att den förväntas ta ett samlat ansvar utan att längre kontrollera alla förutsättningar. Utvecklingen kan uppleva att den förväntas vara självständig men måste invänta beslut om varje mindre miljöförändring. Säkerhetsfunktionen kan bli pressad mellan krav på konsekvent kontroll och ett ökande antal specialfall.

Detta är sällan en fråga som löses av att någon part arbetar snabbare. Det är ofta ett tecken på att **ansvaret fortfarande är ordnat efter tidigare tekniska gränser**. En utvecklare kanske äger en tjänst men inte dess driftkonfiguration. Drift äger infrastrukturen men inte anropens felbeteende. Förvaltning äger IT-stödets användarnytta men saknar överblick över tjänsternas gemensamma beroenden.

Kapitel 4 fördjupar dessa ansvarsglapp. Här är det tillräckligt att konstatera att det operativa arbetet kräver nya former av samverkan: vem kan stoppa en felaktig release, vem prioriterar en incident över flera team, och vem ser till att ett IT-stöd faktiskt går att återställa efter ett större avbrott?

## Vad blir faktiskt bättre?

Det vore missvisande att enbart beskriva generation 2 som en försämring. När gränserna är väl valda kan de distribuerade tjänsterna erbjuda betydande fördelar.

Ett team kan göra en ändring utan att behöva testa eller leverera hela systemet. En tjänst kan skalas efter sitt eget belastningsmönster. Fel kan isoleras bättre om tjänsterna har rimligt självständiga beroenden och rätt felhantering. Teknik kan förnyas stegvis och ett komplext system kan bli lättare att förstå genom tydliga verksamhetsgränser. Framför allt kan ansvar och förändringsmandat komma närmare den del av verksamheten som behöver utvecklas.

De här fördelarna är dock **villkorade**. Om alla tjänster ändå måste driftsättas samtidigt eller dela samma förändringskänsliga data finns inte den tänkta självständigheten. Om ett användarflöde passerar alltför många tätt kopplade tjänster kan prestanda och felsökning bli sämre. Om varje team skapar egna driftstandarder kan den totala förvaltningskostnaden öka.

Framgången bör därför bedömas efter nyttan för användaren och teamens förmåga att förändra sitt område, inte efter antalet tjänster eller teknologier som införts.

## Vårt ärendehanteringssystem i generation 2

I det återkommande exemplet har organisationen brutit ut aviseringar och dokumenthantering från det tidigare sammanhållna systemet. Ärendehanteringen använder ett API för att hämta dokument och publicerar händelser när ärenden ändras. Aviseringstjänsten behandlar dessa händelser asynkront.

Utvecklingsteamen upplever förbättringar. Aviseringar kan ändras utan att hela ärendehanteringen måste testas om, och dokumenttjänsten kan utvecklas på egen plan. Men varje tjänst behöver nu övervakning, certifikat, behörigheter och driftmiljö. Nätverksreglerna blir fler. När användare rapporterar att ärenden ibland inte går att öppna visar det sig att ärendetjänsten inväntar dokumenttjänsten alltför länge. Den enskilda tjänsten ser frisk ut medan användarflödet fungerar dåligt.

Driften föreslår att tjänsterna samlas på ett begränsat antal virtuella maskiner för att hålla nere kostnaderna. Säkerhetsfunktionen vill begränsa kommunikationen, men särskilda regler för varje tjänst kräver ett omfattande underhåll. Teamen vill automatisera sina miljöer, men de gör det på olika sätt. Lösningen fungerar, och den ger verklig nytta, men arbetet för att hålla ihop den har blivit större än vad organisationen först räknade med.

Det är en typisk generation 2-situation: **det finns fler självständiga komponenter, men helheten har inte fått motsvarande operativa stöd**.

## När är den distribuerade modellen rimlig att behålla?

Generation 2 kan vara ett ändamålsenligt läge, inte enbart ett övergångssteg. Om det handlar om ett begränsat antal tjänster med tydliga ägare, få beroenden och fungerande leverans- och incidentprocesser kan en förhållandevis enkel driftsmodell räcka långt.

Det är inte säkert att organisationen behöver en omfattande intern utvecklarplattform. Den kanske klarar sig med väl dokumenterade mallar, ett begränsat antal godkända tekniker, tydliga nätregler och automatiserade standardrutiner. En avancerad plattform har också en kostnad att bygga, driva och vidareutveckla.

Samtidigt finns signaler som motiverar förändring: samma beställningar upprepas i allt större volym, väntetider gör att team inte kan leverera självständigt, standardkrav måste förhandlas i varje ärende eller ingen kan enkelt följa ett användarflöde över komponentgränser. När dessa problem blir återkommande kan organisationen behöva ändra sin leveransmodell, inte bara förbättra varje enskilt ärende.

## Var bör en förändring börja?

Första steget bör inte vara att införa en stor plattform eller flytta allt driftansvar till utvecklingsorganisationen. Börja i stället med att undersöka **vad som faktiskt driver friktionen**.

Om det främst handlar om onödigt många tjänster eller alltför täta synkrona beroenden kan arkitekturen förenklas. Om problemet ligger i många upprepade driftbeställningar bör standardisering och automatisering av de vanligaste tjänsterna prioriteras. Om incidenter går mellan flera team utan tydlig ledning behöver ansvarsmodellen tydliggöras. Om säkerhetszonerna har blivit breda behöver den faktiska åtkomsten granskas och kontrollerna göras mer precisa.

Det går alltså att förbättra generation 2 utan att omedelbart bygga en fullständig generation 3-modell. Men när skalan växer och samma problem fortsätter återkomma blir en gemensam plattformsförmåga allt mer attraktiv.

## Sammanfattning

Den distribuerade IT-miljön har ofta uppstått ur en rimlig ambition: att ge utvecklingsteamen mindre, mer självständiga delar att förändra. I rätt sammanhang skapar det snabbare leveranser, tydligare funktionsgränser och bättre möjligheter till oberoende skalning.

Samtidigt flyttas komplexitet från applikationens insida till kommunikationen mellan tjänsterna. Antalet nätverksanrop, behörigheter, miljöer, versioner och operativa beroenden växer. Kostnadsdrivet samnyttjande kan göra säkerhetsgränserna grövre, men delade resurser behöver inte betyda delad tillit. Även när varje komponent är tillgänglig kan användarens sammanhållna IT-stöd fallera.

Den viktigaste insikten är att **utvecklingsmässig självständighet inte automatiskt ger operativ självständighet**. För att lyckas måste organisationen förstå både tjänsterna och helheten, och skapa en ansvarsfördelning som passar den nya tekniska verkligheten. Det är utgångspunkten för nästa kapitel.
