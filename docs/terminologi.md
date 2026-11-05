# Terminologi
| Term | Definition | Första användning | Kommentar |
|---|---|---|---|
| Monolit | Ett system där stora delar av lösningen utvecklas, testas och driftsätts tillsammans | Kapitel 1 | Kan vara välstrukturerad eller dåligt strukturerad; ordet är inte i sig värderande |
| Perimeter | Den yttre skyddsgränsen runt ett system eller en miljö | Kapitel 1 | Ofta nätverksgränser, men inte hela säkerhetsmodellen |
| Applikationslager | Den del av systemet där verksamhetslogiken körs | Kapitel 1 | Kan bestå av en eller flera applikationsservrar |
| Lastbalanserare | Komponent som fördelar trafik mellan noder eller instanser | Kapitel 1 | Vanlig del av den traditionella driftmiljön |
| Förvaltningsobjekt | Organisatoriskt objekt för prioritering, livscykel och verksamhetsnytta | Kapitel 1 | Används olika i olika organisationer |
| Digital förmåga | En gemensam teknisk tjänst eller kapabilitet som flera lösningar använder | Inledning | Blir viktigare i senare generationer |
| Plattform | Ett organiserat utbud av gemensamma tekniska förmågor och arbetsvägar | Inledning | Förklaras mer utförligt i kapitel 5–7 |
| Modulär monolit | En gemensamt driftsatt applikation med tydliga interna modulgränser | Kapitel 2 | Alternativ eller steg före distribuerad uppdelning |
| Tjänstekontrakt | Överenskommelse om beteende och kompatibilitet vid ett tjänstegränssnitt | Kapitel 2 | Exempelvis API eller händelseschema |
| Kontinuerlig leverans | Förmåga att säkert driftsätta förändringar på begäran genom repeterbara processer | Kapitel 2 | Kräver bl.a. tester och automation |
| Idempotens | Egenskap där upprepad behandling av en händelse inte ger oavsiktliga ytterligare effekter | Kapitel 2 | Viktigt för meddelandeflöden |
| Distribuerat IT-stöd | Ett IT-stöd som realiseras med flera samverkande, separat driftsatta komponenter | Kapitel 3 | Kan ha både synkrona och asynkrona beroenden |
| Tjänsteidentitet | Identitet som används för att autentisera en teknisk tjänst | Kapitel 3 | Behövs för åtkomstkontroll mellan tjänster |
| Observerbarhet (även observabilitet) | Förmåga att förstå systembeteende genom exempelvis loggar, mätvärden och spår | Kapitel 2–3 | I texten används främst observerbarhet; inte detsamma som enbart serverövervakning |
| Komponentansvar | Ansvar för en specifik teknisk del, exempelvis en tjänst eller databas | Kapitel 4 | Behöver skiljas från ansvar för verksamhetsstödet som helhet |
| Operativ helhet | Hur ett sammanhängande IT-stöd fungerar i produktion över flera komponenter och team | Kapitel 4 | Centralt begrepp när användarflödet korsar flera ansvarszoner |
| Ansvarsglapp | Skillnaden mellan behovet av samordning och den faktiska ansvarsfördelningen | Kapitel 4 | Uppstår ofta mellan komponentnivå och användarperspektiv |
| Användarflöde | Den kedja av steg som användaren upplever som en sammanhängande funktion | Kapitel 4 | Kan spänna över flera tjänster och team |
| Intern utvecklarplattform | Sammanhållen uppsättning tjänster och arbetssätt som gör gemensamma tekniska förmågor användbara för utvecklingsteam | Kapitel 5 | Produkten omfattar även dokumentation, stöd och livscykel |
| Infrastruktur som kod | Versionsstyrd och automatiserbar beskrivning av tekniska resurser och konfigurationer | Kapitel 5 | IaC |
| Policy as code | Maskinläsbara och automatiserade policykontroller i exempelvis leverans- eller körmiljö | Kapitel 5 | Ersätter inte riskbedömning eller undantagshantering |
| Golden path (standardväg) | Rekommenderat och väl underhållet arbetssätt för ett återkommande utvecklings- eller driftsbehov | Kapitel 5 | Bör vara enkelt att använda och tillåta motiverade undantag |
| Självbetjäning | Användaren kan begära och hantera en godkänd förmåga utan manuell hantering i normalfallet | Kapitel 5 | Portal är ett gränssnitt, inte ett krav |
| Tjänstenivåmål (SLO) | Mätbart mål för en tjänsts tillförlitlighet eller prestanda | Kapitel 7 | Kan formuleras på plattforms- och användarflödesnivå |
| Incidentledare | Roll med mandat att samordna hantering av en viss incident över teamgränser | Kapitel 7 | Behöver inte vara permanent tjänsteägare |
| Tjänstelöfte | Beskrivning av en plattformstjänsts funktion, gränser, kvalitet och ansvar | Kapitel 7 | Klargör förväntningar mellan plattform och konsumerande team |
| Verksamhetsdriven utveckling | När verksamhetsmedarbetare initierar eller själva bygger digitala lösningar med godkända förmågor | Kapitel 8 | Kräver riskbaserat ansvar och tydliga gränser |
| AI-gateway | Gemensam åtkomstpunkt som kan styra anrop till godkända AI-tjänster | Kapitel 8 | Ersätter inte applikationens eget skydd |
| Verktygsanrop | När en AI-assistent använder ett externt system eller en funktion | Kapitel 8 | Åtgärder ska kontrolleras utanför språkmodellen |
| Riskbaserad delegering | Mandat och skydd anpassas efter datakänslighet, möjliga åtgärder och konsekvenser | Kapitel 8 | Inte en universell tredelad riskklassificering |
| AI-assistent | Lösning som använder en AI-modell för att stödja användaren inom avgränsade uppgifter | Kapitel 9 | Kan ha olika grad av autonomi och verktygsåtkomst |
| Prompt injection | Försök att styra en AI-modell med manipulerade instruktioner i indata eller externa källor | Kapitel 9 | AI-instruktionen utgör inte en säkerhetsgräns |
| Verksamhetsnära utveckling | Utveckling av digitala hjälpmedel och lösningar nära verksamhetens egna behov | Kapitel 9 | Kräver riskbaserad styrning och livscykelansvar |
| Möjliggörande IT | Gemensamma förmågor, tjänster och stöd som gör det möjligt för andra att skapa digitala lösningar | Kapitel 10 | Kompletterar, men ersätter inte, professionell systemleverans |
| Tjänsteägarskap | Ansvar för att ett IT-stöd levererar nytta och har tydlig livscykel, krav och beroenden | Kapitel 10 | Behöver skiljas från drift av enskilda komponenter |
| Beslutsgrind | Bedömning av förutsättningar, nytta och risk före större förändring | Kapitel 11 | Ska ge underlag för beslut, inte ett automatbeslut |
| Livscykelkostnad | Sammanlagd kostnad för införande, drift, förvaltning, vidareutveckling och avveckling | Kapitel 11 | Hjälper jämföra alternativ bortom investeringen |
