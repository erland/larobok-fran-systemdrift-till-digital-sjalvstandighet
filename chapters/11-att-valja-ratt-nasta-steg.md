# 11. Att välja rätt nästa steg

En organisation kan känna igen sig i stora delar av bokens beskrivning och ändå inte behöva genomföra någon stor omställning. Ett verksamhetskritiskt system kan fungera väl med en sammanhållen arkitektur samtidigt som en annan del av samma organisation behöver självbetjäning, automatiserade plattformar och tydligare tjänsteägarskap. En avdelning kan få stort värde av AI-assistenter medan det vore för tidigt att låta den skapa egna produktionssystem med känsliga uppgifter.

Det är därför missvisande att fråga vilken generation organisationen *befinner sig i* och sedan planera en övergång till nästa. En bättre fråga är: **vilka problem är tillräckligt viktiga för att motivera en förändring, och vilka förutsättningar behöver finnas för att förändringen ska vara säkrare och mer värdefull än nuläget?**

Här prövas bokens teknik- och ansvarsperspektiv tillsammans. Beslutsfattaren behöver se nyttan och risken, organisationsansvarig behöver se mandat och kompetens, och arkitekten behöver se beroenden och saknade förmågor.

## Börja med det som faktiskt behöver bli bättre

Förändring börjar ofta med en teknisk idé: mikrotjänster, containrar, en utvecklarplattform, en AI-tjänst eller ett nytt arbetssätt. Det är förståeligt. Sådana idéer är konkreta och lätta att visa upp. Men en teknik är en möjlig åtgärd, inte en beskrivning av problemet.

Utgångspunkten bör i stället vara ett observerbart hinder för verksamheten. Kanske tar en relativt enkel förändring flera månader att leverera trots att kodändringen bara kräver några dagar. Kanske skapar varje ny tjänst en kedja av manuella beställningar. Kanske går det inte att följa ett användarflöde genom flera beroenden vid en incident. Kanske blir säkerhetskontroller svåra att upprepa när fler verksamheter börjar bygga egna lösningar.

Beskriv varje sådant hinder med fyra frågor: **vem påverkas, hur ofta inträffar problemet, vilka konsekvenser får det och vad är den sannolika orsaken?** Gör skillnad mellan upplevelser och belägg. ”Drift är långsam” är en värdering. ”Ett utvecklingsteam väntar i median tolv arbetsdagar på en standarddatabas, varav nio dagar är kötid” är ett användbart beslutsunderlag. Exemplet är illustrativt; varje organisation behöver mäta sina egna ledtider.

Det är också viktigt att identifiera det som redan fungerar. Förutsägbar återställning, kompetent specialistdrift, låg förändringsrisk och välkända integrationsmönster är värden som inte bör gå förlorade bara för att tekniken förändras. Den nya modellen ska helst bevara dessa styrkor och minska de hinder som faktiskt finns.

## En beslutsmodell med tre utfall

När nuläget är begripligt finns tre huvudsakliga vägar: **bevara och förbättra**, **förenkla och standardisera** eller **genomföra en målmedveten förflyttning**. De är alternativ för ett visst IT-stöd eller en viss förmåga, inte etiketter på hela organisationer.

![Beslutsmodell för att välja mellan att bevara och förbättra, förenkla och standardisera eller genomföra en målmedveten förflyttning. Modellen börjar med ett verifierat verksamhetsproblem, bedömer om den befintliga lösningen kan möta behovet, undersöker komplexitet och prövar förutsättningar och risk före begränsad förändring.](../assets/generated/IMG-11-01.svg)

Beslutsillustrationen [@fig:IMG-11-01] visar ordningen i resonemanget. Den är inte en automatisk poängmodell. Beslut kräver fortfarande professionell bedömning, men modellen gör det svårare att hoppa över frågan om varför en förändring behövs.

### Väg 1: Bevara och förbättra

Om ett IT-stöd fungerar tillförlitligt, möter verksamhetens förändringsbehov och har rimliga kostnader kan den klokaste vägen vara att bevara dess grundarkitektur. Då bör förbättringarna riktas mot tydligt identifierade svagheter: bättre tester, dokumenterade beroenden, starkare identitetsskydd, förbättrad backup och återställningsförmåga eller kortare releaseprocess.

En välmodulerad monolit med en tydlig ägare kan fortsätta vara ett gott val. Att dela upp den i många tjänster är inte en förbättring om resultatet bara blir fler beroenden och större operativ börda. DORA:s vägledning lyfter fram möjligheten att testa, förändra och driftsätta självständigt, oavsett om tekniken är en stordator, en monolit eller mikrotjänster [K007].

Beslutet att bevara är inte ett beslut att stå stilla. Det är att utveckla en fungerande modell utan att introducera en ny komplexitet som behovet inte motiverar.

### Väg 2: Förenkla och standardisera

När problemen främst kommer av teknikvariation, manuella beställningar, oklara integrationer eller ett växande antal specialfall bör organisationen först förenkla. Det kan innebära att konsolidera teknikvarianter, skapa gemensamma tjänstekontrakt, avveckla onödiga komponenter, tydliggöra systemgränser eller automatisera några vanliga driftuppgifter.

En modulär monolit med tydliga modulgränser kan exempelvis minska intern koppling utan att varje modul får eget nätverk, egen databas och egen releasekedja. En begränsad självbetjäningstjänst för databaser kan lösa ett återkommande väntetidsproblem utan att en komplett intern utvecklarplattform byggs. Gemensamma integrationsprinciper kan ibland ge större effekt än ytterligare en produkt.

Förenkling är också en förberedelse inför större förändringar. Om verksamheten har mycket oklara komponent- och dataägarskap kommer ny automation ofta att automatisera otydligheten snarare än lösa den.

### Väg 3: Genomföra en målmedveten förflyttning

En större förflyttning kan vara motiverad när många team har likartade hinder, när gamla processer inte skalar, när kritiska användarflöden saknar tydligt helhetsansvar eller när verksamhetens utvecklingsbehov inte rimligen kan mötas i den nuvarande modellen. Det kan handla om en intern utvecklarplattform, förändrat tjänsteägarskap, en ny säkerhetsmodell eller möjligheten att verksamheten själv bygger avgränsade lösningar.

Här krävs mer än ett tekniskt beslut. Organisationen behöver samtidigt investera i kompetens, ansvar, mandat, finansiering, tjänstenivåmål och förmåga att hantera incidenter och avveckling. DORA:s och CNCF:s vägledningar betonar att plattformar ska utvecklas utifrån verkliga användarbehov och hanteras som interna produkter, inte som stora teknikprojekt som byggs i förväg [K014] [K017].

## Fem frågor som bör avgöra om organisationen är redo

Det är särskilt frestande att börja när problembilden blivit tydlig. Men ett upplevt behov innebär inte automatiskt att organisationen är redo. Följande fem frågor bör kunna besvaras innan en större förändring beslutas.

**1. Finns en tydlig och återkommande efterfrågan?** Det bör gå att peka ut konkreta användargrupper, frekventa behov och mätbara hinder. En plattform utan verkliga interna användare riskerar att bli ännu en tjänst som måste förvaltas.

**2. Finns ett helhetsägarskap?** Vem ansvarar för verksamhetsnyttan, de sammanhängande användarflödena och hur kvalitet ska bedömas? Självständiga komponentteam ersätter inte behovet av samlad prioritering och operativ samordning.

**3. Finns tillräcklig drifts- och säkerhetsförmåga?** Det behöver finnas en nivå av automatiserad testning, identitetsstyrning, loggning, övervakning, incidentberedskap och återställning som motsvarar lösningarnas risk. Saknas detta bör det normalt byggas upp innan antalet tjänster eller verksamhetsutvecklade produktionslösningar ökar kraftigt [K001] [K015].

**4. Finns kompetens och långsiktig finansiering?** Nya plattformar kräver produktägarskap, förbättringsarbete och specialistkompetens även efter första införandet. En satsning som bara finansierar installationen men inte förvaltningen får svaga förutsättningar att lyckas.

**5. Finns en hanterbar förändringsyta?** En avgränsad pilot med känd informationsklassning, tydlig ägare, kontrollerade integrationer och begränsad påverkan är oftast ett bättre första steg än att flytta ett stort kritiskt IT-stöd i ett enda projekt.

Ett negativt svar på någon av frågorna behöver inte stoppa all förändring. Det kan däremot innebära att **förberedelserna är nästa steg**, snarare än själva förflyttningen.

## Vilka tekniska förmågor behöver utvecklas – och vem tar ansvar?

Teknikläsaren behöver kunna omsätta beslutet till en sammanhängande förmågekarta, men det är viktigt att skilja mellan sådant som behövs för nästan all modernisering och sådant som bara blir motiverat i vissa arkitekturer.

En första grupp utgörs av **grundförmågor**: versionshantering, automatiska tester, repeterbar driftsättning, hantering av hemligheter och identiteter, övervakning, loggning och verifierad återställning. Dessa skapar nytta även för traditionella system. Utveckling och drift behöver gemensamt äga införandet, medan systemansvarig anger kraven på fungerande tjänst.

En andra grupp är **förmågor för distribuerad drift**: tjänstekontrakt, säker tjänstetill-tjänst-kommunikation, spårbarhet över anrop, tidsgränser, hantering av återförsök, kapacitetsstyrning och tydliga mekanismer för förändringar utan gemensamma stora releaser. Dessa blir allt viktigare när komponenter får oberoende livscykler [K008] [K012]. Respektive tjänsteteam behöver då äga kontrakt och felbeteende, medan någon samordnar hela användarflödet.

En tredje grupp är **plattformens självbetjäning**: automatiserad provisionering, godkända standardvägar, policykontroller, kvoter, kostnadsuppföljning och tjänstekataloger med tydlig användarupplevelse. Målet är att undanröja återkommande friktion, inte att ge varje team fler val att administrera [K017]. Ett plattformsteam ansvarar för förmågan som intern produkt och dess stöd till användande team.

En fjärde grupp är **förmågor för verksamhetsdriven AI-utveckling**: säkra API:er, tydlig dataklassning, åtkomstkontroll på tjänste- och informationsnivå, godkända AI-tjänster, utvärdering av kvalitet, spårbarhet, publiceringskontroller och regler för avveckling. AI-instruktioner och användargränssnitt får aldrig ersätta behörighets- och riskkontroller i tjänsterna [K006] [K019] [K020]. Verksamheten äger ändamålet och den tillåtna informationsanvändningen, medan plattform och säkerhetsfunktion säkerställer kontroller och spårbarhet.

Varje förmåga bör få en ägare, en definierad intern användare, en kvalitetsnivå och en mätbar anledning att existera. Om detta inte går att beskriva är risken stor att organisationen bygger teknik som ingen riktigt efterfrågar eller kan förvalta.

## Vilka organisatoriska förändringar behövs?

Tekniska förbättringar kan sällan kompensera för oklara ansvar när beroendena blir många. Men lösningen är inte att överföra allt driftansvar till utvecklingsteamen eller att göra plattformsteamet ansvarigt för all applikationskvalitet.

Utvecklingsteam behöver äga sina tjänsters kod, beteende, ändringar, diagnos och relevanta operativa kvalitetskrav. Plattformsteam behöver äga gemensamma förmågor, tekniska standardvägar, livscykel och tjänstelöften för plattformen. Säkerhetsfunktionen behöver ange kontrollkrav och stödja uppföljning, medan ansvariga informations- och verksamhetsägare fattar de beslut som hör till deras mandat. Arkitekturfunktionen behöver värna helhet, gränssnitt och långsiktig utvecklingsbarhet. Förvaltningen behöver säkerställa att både system och gemensamma förmågor har varaktiga ägare.

Detta behöver kompletteras med **tvärgående operativ samordning**. En incident i ett användarflöde kan beröra flera komponenter och plattformar. Därför måste en utsedd funktion kunna leda den samlade incidenthanteringen, medan respektive team ansvarar för att åtgärda felet inom sitt område. Tjänstenivåmål bör beskriva vad användaren behöver, inte bara om infrastrukturen är uppe [K018].

Även beslutsmodellen måste förändras. En central arkitekturfunktion som måste granska varje detalj i varje förändring riskerar att bli en flaskhals. Samtidigt kan lokala team inte ensamma avgöra frågor som påverkar gemensam identitet, informationssäkerhet eller andra tjänster. Rätt balans är **frihet inom gemensamma skyddsräcken**, kombinerat med ett begripligt undantags- och riskacceptansförfarande.

## Gör förändringen prövbar innan den görs stor

En förändring bör börja med ett avgränsat försök som kan misslyckas utan att den ordinarie verksamheten utsätts för oacceptabel risk. Utse en ansvarig för den samlade nyttan och en ansvarig för den tekniska leveransen. Dokumentera nuläge och mål innan arbetet påbörjas.

Anta att fem utvecklingsteam ofta väntar på likartade databasmiljöer. En pilot kan erbjuda en enda självbetjänad databastjänst med definierade säkerhetsinställningar, backup och uppföljning. Mät beställningens genomloppstid, antal manuella steg, återställningsförmåga, kostnad och användarupplevelse. Först när den fungerar väl för verkliga användare finns skäl att bredda tjänsten.

En organisation som vill pröva verksamhetsskapade AI-assistenter kan på motsvarande sätt börja med ett lågkritiskt arbetsflöde där informationskällor, behörigheter och livscykel är kända. Bedöm inte bara hur snabbt prototypen skapas. Mät även kvaliteten i resultaten, säkerhetsavvikelser, behov av mänsklig kontroll, kostnader och hur lösningen kan ändras eller stängas av.

En sådan pilot behöver ha **stoppvillkor**. Om lösningen kräver fler manuella undantag än väntat, om återställningen inte kan visas fungera eller om oklara ansvar förblir olösta ska arbetet justeras innan större utrullning. Det är mer ansvarsfullt än att låta en beslutad målbild bli viktigare än faktiska erfarenheter.

## Mät effekten på helheten, inte bara aktiviteten

Det är lätt att visa hur många tjänster som containeriserats, hur många standardvägar som skapats eller hur många AI-assistenter som lanserats. Sådana mått beskriver aktivitet. De säger mindre om organisationen faktiskt blivit bättre.

En balanserad uppföljning bör därför kombinera fem perspektiv:

| Perspektiv | Exempel på relevanta mått | Vad måtten ska visa |
|---|---|---|
| Verksamhetsnytta | Tid till en användbar förändring, avbrott i kritiska användarflöden | Om IT-stödet möter verksamhetens behov |
| Leveransförmåga | Ledtid för förändring, koordinationsbehov, misslyckade driftsättningar | Om teamen blir mer självständiga och säkra |
| Robusthet | Tid till återställning, uppfyllda tjänstenivåmål, lyckade återställningsprov | Om den samlade tjänsten går att lita på |
| Säkerhet och kontroll | Brister i behörighet, policyavvikelser, tid till åtgärd | Om kontrollen förbättras när förändringstakten ökar |
| Ekonomi och förvaltning | Total livscykelkostnad, återanvändning, kompetens- och supportbehov | Om modellen är hållbar på längre sikt |

Måtten ska användas för lärande, inte för att ställa utveckling och drift mot varandra. DORA:s vägledning lyfter särskilt självständig leverans och möjligheten att förändra utan onödiga beroenden; den kopplar resultatet till både organisatorisk struktur och arkitektur [K007]. Plattformsmognad behöver samtidigt bedömas genom användning, kvalitet och effekt, inte enbart vilka funktioner som finns installerade [K014] [K017].

## Ett ärendehanteringsstöd: tre rimliga beslut

Det fiktiva ärendehanteringsstödet som följt boken visar varför samma organisation kan behöva flera vägar samtidigt.

**Bevara och förbättra:** Den centrala ärendemodulen har stabil drift, tydligt dataägarskap och få förändringsbehov. En förbättrad test- och releaseprocess ger nytta utan att modulen bryts ut i flera tjänster. Det blir ett medvetet beslut att behålla en sammanhållen arkitektur.

**Förenkla och standardisera:** Aviseringar och dokumentintegrationer har växt till många specialfall. Organisationen enas om ett fåtal godkända API-kontrakt, standardiserad loggning och en gemensam återställningsrutin. När gränssnitten fungerar blir samordningen enklare utan någon dramatisk omorganisation.

**Genomför en målmedveten förflyttning:** Flera team behöver upprepade gånger nya driftmiljöer och integrationsmöjligheter. En gemensam plattformstjänst införs stegvis, med tydligt produktägarskap, säkerhetskrav och självbetjäning. Verksamhetens första AI-assistenter får använda dokumenterade, behörighetskontrollerade gränssnitt, men inte kringgå ärendesystemets egna kontroller.

Alla tre besluten kan vara rätt samtidigt. Poängen är inte att göra all IT likadan, utan att anpassa graden av självständighet, standardisering och kontroll till behoven.

## När det är klokt att vänta

Att vänta kan vara ett aktivt och välgrundat beslut. Det gäller särskilt om organisationen saknar tydligt ägarskap för viktiga IT-stöd, om säkerhets- och återställningskrav inte kan beskrivas, om tekniska standardvägar saknar förvaltning eller om kompetensen att driva den nya modellen inte är finansierad.

Men väntan behöver vara målmedveten. Formulera vilka förutsättningar som saknas, vem som ansvarar för att utveckla dem och hur ni ska veta när läget har förändrats. Utan detta riskerar "vi är inte redo" att bli en ursäkt för att låta de gamla problemen växa.

Det kan också vara för tidigt därför att behovet är för litet. En organisation med ett fåtal stabila system och låg förändringstakt behöver inte ta på sig kostnaderna för en avancerad utvecklarplattform eller ett stort program för AI-driven verksamhetsutveckling. I den situationen kan enklare verktyg, tydligare arbetsrutiner och selektiv automatisering vara mer effektiva.

## Ett beslut som håller även när tekniken förändras

De fyra generationerna i boken beskriver hur arkitektur, ansvar och arbetssätt kan förändras – inte en trappa som alla organisationer måste klättra uppför. Det mest bestående är inte någon viss teknik, utan förmågan att se hela IT-stödet: vad det gör för användaren, vilka komponenter det bygger på, vem som bär ansvar och hur kvaliteten säkras.

Tekniken kommer fortsätta förändras. AI gör det möjligt för fler att skapa nya lösningar, men gör inte krav på säkerhet, livscykel eller tillgänglighet mindre viktiga. En organisation som har lärt sig att kombinera tydligt ägarskap, gemensamma förmågor och kontrollerad självständighet har bättre förutsättningar att hantera framtida teknikskiften än en organisation som förlitar sig på ett visst verktyg eller en viss organisationsform.

Det mest användbara sista beslutet är därför inte "vi ska bli generation 3" eller "vi ska bli AI-drivna". Det är att beskriva **vad som behöver fungera bättre, vad som redan fungerar väl, vilka förutsättningar som saknas och vilket minsta nästa steg som kan visa att förändringen ger verklig nytta**.

## Sammanfattning

Det finns tre legitima utvecklingsvägar: bevara och förbättra, förenkla och standardisera eller genomföra en målmedveten förflyttning. Valet bör börja i observerade behov och bedömas mot ägarskap, teknisk beredskap, kompetens, ekonomi och risk. Stora förändringar bör göras prövbara och följas upp på verksamhetsnytta, leveransförmåga, robusthet, säkerhet och långsiktig hållbarhet.

En modern IT-organisation behöver inte samma arkitektur överallt. Den behöver förmågan att välja rätt arkitektur och rätt ansvarsfördelning för olika behov – och att ändra dessa när förutsättningarna faktiskt förändras.
