# 9. Den AI-drivna och verksamhetsnära IT-modellen

En verksamhetsmedarbetare behöver få bättre överblick över inkommande ärenden. I en traditionell organisation skulle behovet sannolikt ha formulerats som ett utvecklingsuppdrag. I en plattformsorienterad miljö kan utvecklingsteamet snabbt bygga funktionen med redan godkända tjänster. I en allt mer AI-stödd miljö kan medarbetaren själv beskriva behovet, få hjälp att skapa en första lösning och pröva ett första utkast utan att först beställa en traditionell utvecklingsinsats.

Det är en verklig möjlighet. Det är däremot inte ett bevis för att vem som helst kan skapa och förvalta ett kritiskt IT-stöd utan specialistkompetens. **Generation 4 handlar därför mindre om att IT-avdelningen försvinner och mer om att kretsen av dem som kan skapa digitala lösningar vidgas.** För att detta ska bli hållbart måste organisationen kunna skilja mellan snabb idéprövning och långsiktigt ansvar för information, processer och produktionsmiljöer.

I det här kapitlet betraktas generation 4 som en analytisk framtidsmodell. AI-assistenter, low-code och AI-stödd programmering används redan. Men en organisation där verksamheten utan omfattande IT-inblandning själv kan skapa, publicera och förvalta många verksamhetslösningar är fortfarande ett scenario med varierande mognad och betydande osäkerhet. Skillnaden mellan etablerad praktik och framtida potential behöver hela tiden vara synlig [K005].

## När verksamheten blir en aktiv producent

De tidigare generationerna har ändrat hur IT byggs, levereras och drivs. Generation 4 ändrar dessutom **vem som kan ta initiativet hela vägen till en fungerande lösning**. En ekonom kan bygga ett underlag för budgetuppföljning. En handläggare kan skapa en assistent för att sammanställa ärendefakta. En verksamhetsspecialist kan beskriva ett arbetsflöde och låta en AI-tjänst föreslå användargränssnitt, regler och integrationer.

Denna utveckling har föregångare i kalkylblad, makron, low-code och automatiserade arbetsflöden. AI tillför framför allt en mer tillgänglig dialog med tekniken och kan sänka tröskeln för att skriva kod, bearbeta information och skapa användbara prototyper. Att koden fungerar i en prototyp innebär dock inte att dess säkerhet, tillförlitlighet eller förvaltningsbarhet har verifierats. Samtidigt kan den höja takten i produktionen av både väl fungerande och bristfälliga lösningar. DORA:s studie från 2025 beskriver AI som en förstärkare av organisationens befintliga styrkor och svagheter [K005].

Det ger två samtidiga perspektiv. För verksamheten blir det möjligt att pröva idéer utan långa startsträckor. För organisationen som helhet blir det desto viktigare att avgöra när en idé övergår till en tjänst som andra måste kunna lita på.

## En teknisk arkitektur för många självständiga lösningar

I en hållbar generation 4 bygger man inte varje assistent eller app från grunden. Verksamhetsnära utveckling vilar på gemensamma digitala förmågor som tillhandahålls och förvaltas av professionella team. Det gäller särskilt identitet, behörigheter, datatjänster, API:er, AI-modeller, loggning, kostnadskontroll, publicering och återställning.

Arkitekturen kan förstås i fyra nivåer:

1. **Verksamhetens lösningar.** Personliga assistenter, avdelningsappar, arbetsflöden och professionellt utvecklade IT-stöd. Dessa kan ha olika risknivå, livslängd och krav på kvalitet.
2. **Godkända gränssnitt och utvecklingsvägar.** Mallar, byggmiljöer, kataloger, AI-gränssnitt och publiceringsflöden som avgör vilka funktioner användaren får nyttja.
3. **Gemensamma kontroll- och plattformsförmågor.** Identitet, databehörigheter, spårbarhet, tester, policykontroller, säkerhetsövervakning och kostnadsgränser.
4. **Befintliga verksamhetssystem och grundläggande infrastruktur.** Transaktionssystem, informationskällor, integrationstjänster och de driftmiljöer som fortsatt måste vara robusta och förvaltningsbara.

Antalet digitala lösningar kan växa utan att varje mindre app behöver bli en självständig produktionsplattform. Även en enkel app kan vara beroende av avancerade gemensamma skydd. Det som ska vara lätt är att **använda** dessa skydd, inte att välja bort dem.

Det är inte heller nödvändigt att en och samma plattform hanterar allt. Olika tekniska miljöer kan samexistera om organisationen har tillräckligt tydliga gränssnitt, ägarskap och gemensamma principer. Arkitekturmålet är återanvändbara förmågor och tydliga kontrollpunkter, inte teknisk likformighet för dess egen skull.

## Tre typer av lösningar – tre olika kravbilder

Den viktigaste skillnaden inom generation 4 är inte vilken AI-modell som används. Det är vilken **konsekvens en lösning får om den gör fel, blir otillgänglig eller hanterar information felaktigt**.

### Personliga hjälpmedel

En personlig assistent som hjälper en medarbetare att sammanfatta tillåtet material kan ofta användas med relativt enkla kontroller. Centralt är att datakällor, sekretess och rättigheter är korrekta, att den som använder hjälpen kan granska resultatet och att assistenten inte får större befogenheter än användaren själv. En sammanfattning ska inte behandlas som ett fastställt beslut.

### Gemensamma verksamhetslösningar

När en app eller assistent börjar användas av en hel enhet ändras ansvaret. Då behövs en utsedd ägare, versionshantering, stöd vid incidenter, regler för åtkomst, förändringskontroll och en plan för avveckling. Att det gick snabbt att skapa lösningen gör inte dess framtida underhåll kostnadsfritt.

### Verksamhetskritiska IT-stöd

När lösningen kan fatta eller verkställa beslut, påverka andra system, hantera känsliga uppgifter eller störa kritiska processer krävs starkare kontroll. Det kan innebära professionell utveckling, formaliserad testning, säkerhetsgranskning, tillgänglighetsmål, återställningsövningar, spårbarhet och tydlig incidentledning. Vissa verksamhetsbyggda prototyper kan bli underlag för sådana system, men behöver då gå igenom en annan kvalitetssäkrings- och förvaltningsprocess.

En riskbaserad indelning i personliga hjälpmedel, gemensamma verksamhetslösningar och verksamhetskritiska IT-stöd är ett beslutsstöd, inte ett officiellt klassningssystem eller en fullständig juridisk riskbedömning. Samma lösning kan kräva en annan hantering när den får fler användare, nya integrationer eller större befogenheter. Klassningen bör därför omprövas under livscykeln.

## Säkerhet kan inte byggas enbart med uppmaningar

En AI-assistent kan verka väl avgränsad genom sin instruktion, men instruktioner är inte en säkerhetsgräns. En språkmodell kan påverkas av innehåll i dokument, webbsidor eller andra externa källor. Sådan *prompt injection* kan försöka få modellen att avvika från sin avsedda uppgift. Om modellen också får tillgång till verktyg som skriver data, skickar meddelanden eller initierar transaktioner växer konsekvensen av ett fel [K020], [K022].

En robust lösning använder därför kontroller utanför själva AI-modellen: autentisering, behörighetskontroll vid varje dataåtkomst, begränsade verktygsrättigheter, validerade åtgärder, loggning och ibland mänskligt godkännande. Rättigheterna bör knytas till den aktuella användaren eller en särskilt begränsad tjänsteidentitet, inte till en generell överprivilegierad robot.

Även svarens kvalitet är en säkerhets- och verksamhetsfråga. En assistent kan ge ett rimligt men felaktigt svar, förlora en viktig reservation eller använda en inaktuell källa. Därför behövs utvärderingar mot representativa arbetsuppgifter, tydliga gränser för automatiska beslut och förmåga att upptäcka när kvaliteten försämras. NIST:s profil för generativ AI framhåller behovet av att hantera risker genom hela livscykeln, inte bara vid första införandet [K019].

## Tillgänglighet, backup och bakåtkompatibilitet försvinner inte

När en verksamhet själv skapar en app är det lätt att fokusera på dess omedelbara funktion. Men en lösning som används dagligen blir snabbt ett beroende. Den kan behöva återställas efter ett misstag, tåla att en underliggande modell byts eller fortsätta fungera när ett API förändras.

Plattformen kan erbjuda säkerhetskopiering, versionshantering, driftsättning, återställningsmekanismer och övervakning. Men någon måste fortfarande bestämma **vilken data som får gå förlorad, hur länge tjänsten får vara otillgänglig och vilka förändringar som måste vara bakåtkompatibla**. Dessa krav kan inte härledas enbart ur valet av verktyg. De måste komma från användningen och verksamhetsansvaret.

En AI-tjänst innebär dessutom särskilda förändringsrisker: modellversioner kan ge olika resultat, externa leverantörer kan ändra villkor och ett nytt informationsunderlag kan förändra hur assistenten svarar. Därför behöver kritiska lösningar testas på nytt när modeller, datakällor, verktyg eller instruktioner ändras. Rollback kan vara nödvändig men kan inte alltid återställa en redan genomförd extern åtgärd.

## Ansvar och organisation i generation 4

Verksamheten kan få mandat att skapa och förvalta fler lösningar, men behöver samtidigt acceptera ett tydligt ägarskap. Den som beställer eller bygger en lösning måste veta vem som ansvarar för dess syfte, data, användare, kostnader och avveckling. IT-funktionen tillhandahåller godkända tekniska vägar och stödjer drift, säkerhet och integration. Informationsägare och riskansvariga avgör vilka uppgifter och åtgärder som får användas inom gällande regler.

Det innebär inte att varje avdelning behöver få en egen driftorganisation. Snarare behöver utvecklingen kunna ske nära verksamheten medan gemensamma förmågor och specialistansvar återanvänds. För kritiska lösningar behöver professionella team fortsatt ta ett större tekniskt ansvar.

En användbar princip är att **mandatet att skapa en lösning ska vara större än mandatet att ge den nya rättigheter eller publicera den för andra**. Ett experiment kan ofta genomföras med begränsade data och utan produktionsintegrationer. Att öppna samma lösning för många användare eller låta den ändra uppgifter i ett kärnsystem kräver starkare kontroll.

## Nya styrkor – och nya fallgropar

Den största styrkan är förmågan att omsätta små, lokala förbättringsidéer till fungerande hjälpmedel utan att belasta en central utvecklingskö med varje experiment. Det kan ge snabb återkoppling från användare och göra verksamhetskompetens till en mer direkt del av digital utveckling. För vissa behov räcker en enkel, kortlivad lösning; då är det ineffektivt att behandla den som ett nytt stort system.

Samma styrka kan däremot skapa ett växande landskap av lösningar som ingen har full överblick över. Det kan handla om dubbletter, bristande dokumentation, oklar licens- och modellkostnad, leverantörsberoenden och appar som lever kvar efter att skaparen har bytt arbetsuppgift. Snabb utveckling kan alltså förvandla en utvecklingskö till en förvaltningsskuld om organisationen saknar register, ägarskap och avvecklingsvägar.

Det finns också en risk att verksamhetsnära utveckling används som argument för att kringgå professionell IT i stället för att dra nytta av den. Resultatet blir då inte ökad självständighet utan en ny sorts skugg-IT. Ett framgångsrikt arbetssätt gör tvärtom den godkända vägen så enkel att den blir det naturliga förstahandsvalet.

## Ett återkommande exempel: ärendehanteringen

Tänk tillbaka på det fiktiva ärendehanteringsstödet som följt boken. I generation 1 bestod det av en sammanhållen applikation med tydlig driftmiljö. I generation 2 delades funktionalitet upp i flera tjänster. I generation 3 kunde teamen bygga och drifta tjänsterna genom gemensamma plattformsförmågor.

I generation 4 kan en handläggare själv skapa en assistent som sammanfattar ärendehistorik med hjälp av ett godkänt läs-API. En annan medarbetare kan bygga en enkel vy som visar ärendebalanser. Båda kan ge värde utan att kärnsystemet behöver förändras. Men om assistenten ska fatta beslut, uppdatera ärendestatus eller skicka externa meddelanden måste den använda kontrollerade gränssnitt och gå igenom en starkare prövning.

Det avgörande är alltså inte om lösningen har skapats av en professionell utvecklare eller med hjälp av AI. Det avgörande är dess konsekvenser, beroenden och krav på långsiktig tillförlitlighet.

## När modellen är lämplig – och när den bör begränsas

Verksamhetsnära utveckling lämpar sig bäst där behov kan avgränsas, dataåtkomsten är kontrollerad och det finns gemensamma tjänster som kan användas utan speciallösningar. Den bör börja med uppgifter som är lätta att testa, där fel är upptäckbara och där man kan avbryta eller återställa utan omfattande konsekvenser.

Organisationen bör däremot vara försiktig med bred utrullning om den saknar överblick över data, möjlighet att begränsa verktygsrättigheter, tydligt ägarskap eller stöd för uppföljning och avveckling. Utan dessa förutsättningar kan den ökade utvecklingstakten bygga upp större risker än nyttan motiverar.

Det finns heller ingen anledning att tvinga all traditionell IT till denna generation. Kärnsystem med strikta transaktionskrav och lång livslängd kan fortsätta fungera bäst med professionell utveckling och särskilt utformad drift. Generation 4 är därför ett nytt sätt att **komplettera** organisationens digitala förmåga, inte ett krav att ersätta alla andra modeller.

## Framtidens öppna frågor

Den fortsatta utvecklingen av AI-agenter kan ge verksamheten mer avancerade möjligheter att samordna arbete och utföra åtgärder. Men det är ännu osäkert hur snabbt organisationer kan etablera tillräckligt robusta modeller för behörighet, ansvar, kvalitet och återställning. Standardisering av agentkommunikation och verktygsanrop är lovande, men löser inte i sig frågor om vem som får fatta beslut, vilka data som får användas och hur en incident ska hanteras [K021].

Det rimliga framtidsperspektivet är därför inte gränslös automation. Det är en gradvis förskjutning där fler människor kan skapa lösningar, medan allt mer av organisationens ansvar för kvalitet och säkerhet behöver kunna uttryckas i återanvändbara tjänster och kontroller.

## Sammanfattning

I bokens scenario för generation 4 kan fler skapa digitala lösningar nära verksamhetens behov. Det kan korta vägen från idé till användbar funktion, men skapar också nya krav på informationsstyrning, livscykel, tillgänglighet, kvalitet och ansvar. Skillnaden mellan ett personligt hjälpmedel och ett verksamhetskritiskt IT-stöd är större än skillnaden mellan olika utvecklingsverktyg.

Den hållbara modellen kombinerar verksamhetens initiativkraft med godkända plattformar, tydliga mandat och riskanpassade kontroller. IT-avdelningens roll blir då inte mindre viktig. Den förändras. Hur den förändringen påverkar organisationens framtida uppgift är ämnet för nästa kapitel.
