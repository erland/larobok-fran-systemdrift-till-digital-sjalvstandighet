# 6. Den plattformsorienterade IT-modellen

En utvecklare behöver en ny testmiljö. Tidigare krävdes flera beställningar: nätverk, server, databas, behörigheter, certifikat och loggning. Nu beskriver utvecklaren den önskade tjänsten i en standardiserad mall och får en miljö där grundläggande säkerhets- och driftförmågor redan ingår. Det är en väsentlig förändring – men den viktigaste skillnaden ligger inte i knappen som skapar miljön. Den ligger i **vem som behöver förstå och hantera komplexiteten**.

I en plattformsorienterad IT-modell kan många utvecklingsteam arbeta självständigt utan att varje team behöver bli specialist på all underliggande infrastruktur. Gemensamma förmågor paketeras som tjänster med tydliga gränssnitt, begripliga kvalitetskrav och ett ansvar för hela deras livscykel. Utvecklarna får större handlingsutrymme; de gemensamma specialisterna kan koncentrera sig på att göra de återkommande behoven säkra, tillförlitliga och enkla att använda.

Detta är generation 3 i bokens analysmodell. Den ersätter inte distribuerade tjänster med något nytt. Den gör det möjligt att **hantera ett växande antal tjänster som en sammanhållen och styrbar miljö**. Det är skillnaden mot generation 2, där varje nytt behov lätt ledde till ytterligare en beställning, speciallösning eller informell överenskommelse.

## Hur arkitekturen brukar se ut

Det är användbart att betrakta plattformen i fyra nivåer. Underst finns den faktiska kör- och lagringsmiljön: datorresurser, nätverk, databasmotorer och ibland containerorkestrering. Ovanpå den ligger gemensamma tekniska förmågor, till exempel identitet, certifikat, köer, hemlighetshantering, loggning, övervakning och säkerhetskopiering. Nästa nivå är de standardiserade gränssnitt genom vilka förmågorna används: API:er, automatiserade mallar, deklarativa konfigurationer, CLI-verktyg och ibland en utvecklarportal. Överst finns applikationerna och de utvecklingsteam som använder plattformen.

Arkitekturen behöver inte vara byggd kring en viss produkt. Den kan bestå av molntjänster, egen drift, hanterade tjänster eller en kombination. Den viktiga egenskapen är att **gemensamma behov har gemensamma lösningar**, medan applikationens särskilda verksamhetslogik fortsatt ägs nära den verksamhet som behöver den. CNCF:s mognadsmodell beskriver detta som en utveckling av bland annat investering, användning, gränssnitt, drift och mätning – inte enbart införande av verktyg [K014].

När plattformen växer behöver systemgränserna bli tydligare: vilka delar tillhör ett visst IT-stöd, vilka är gemensamma tjänster och vem ansvarar för respektive helhet? Gemensam körmiljö innebär inte att alla applikationer ska dela databas, behörigheter eller nätverksåtkomst.

## Självbetjäning är mer än ett formulär

En självbetjäningsportal som bara skapar ett ärende till drift är i praktiken en ny front för det gamla arbetssättet. Verklig självbetjäning innebär att vanliga och godkända åtgärder kan genomföras utan att en central grupp manuellt måste översätta, granska och utföra varje beställning.

Anta att ett team ska skapa en tjänst med databas. En användbar standardväg behöver kunna skapa rätt miljö, tilldela en unik teknisk identitet, begränsa nätverksåtkomsten, aktivera loggning och övervakning, sätta resursgränser och tillämpa regler för säkerhetskopiering. Den ska också tala om vem som äger instansen, vilka kostnader den medför och hur den avvecklas. Teamet behöver inte känna till varje teknisk detalj; däremot måste det kunna förstå vilka krav och begränsningar som följer med valet.

I plattformsutveckling kallas sådana genomarbetade vägar ofta *golden paths*: rekommenderade sätt att åstadkomma vanliga saker, där repetitiva och riskfyllda moment redan är hanterade. En golden path är inte ett förbud mot alternativ. Den är ett bättre standardval, med en tydlig väg för undantag när verksamhetens behov kräver något annat. DORA beskriver interna utvecklarplattformar just som en kombination av verktyg, arbetsflöden, självbetjäning och återanvändbara standardvägar [K017].

En viktig konsekvens är att utvecklarnas **självständighet kan öka samtidigt som variationen i driftsmiljön minskar**. Det är en av plattformsmodellens mest intressanta styrkor.

## Säkerhet och robusthet som gemensamma förmågor

Den traditionella modellen byggde mycket av skyddet kring ett IT-stöds yttre gräns. I generation 3 blir säkerhet oftare en kombination av underliggande segmentering och tydliga regler för varje tjänst, identitet och informationsflöde.

Plattformen kan utfärda tjänsteidentiteter, lagra hemligheter, styra vilka tjänster som får kommunicera, samla säkerhetsloggar och kontrollera konfigurationer i leveransflödet. Säkerhetsfunktionen kan formulera krav som prövas automatiskt; utvecklingsteamen ansvarar för att deras applikationer använder mekanismerna rätt. Det motsvarar principen att kontroll ska finnas på flera nivåer, inte enbart i det nätverk där applikationen råkar köras [K001] [K015].

Samma uppdelning behövs för tillgänglighet och återställning. Plattformen kan tillhandahålla redundanta instanser, automatisk omstart, lagringsreplikering och säkerhetskopiering. Men den vet inte utan vidare vilka verksamhetstransaktioner som kan avbrytas, hur mycket data som får gå förlorad eller vilken återställningstid användarna kan acceptera. Det måste fastställas för IT-stödet och sedan översättas till tekniska krav och verifierade rutiner.

Ett särskilt misstag är att likställa en lyckad säkerhetskopiering med förmåga att återställa verksamheten. Återställningsmål, beroendeordning och faktiska återställningsövningar behöver hanteras tillsammans av tjänsteägare, applikationsteam och plattform.

## Vad som blir enklare

När plattformen fungerar väl behöver ett nytt team inte upprepa arbetet med nätverk, identitet, certifikat, loggning och driftsättning. Nya miljöer skapas snabbare och med jämnare kvalitet. Samma kontroller kan tillämpas på många tjänster utan att specialister måste granska varje enskilt handgrepp.

Det ger också mer förutsägbar drift. Gemensamma standardkomponenter kan uppdateras centralt. Applikationernas egna bibliotek och beroenden behöver däremot fortfarande hanteras av ansvariga team. Avvikelser i konfiguration kan upptäckas automatiskt. Incidenter kan undersökas med gemensamma loggar, mätvärden och distribuerade spår. Gemensamma lösningar gör det lättare att beskriva stödnivåer och åtgärdstider.

**Samnyttjande blir dessutom enklare att förena med isolering.** Flera applikationer kan nyttja samma underliggande kapacitet men separata identiteter, nätverkspolicyer, databaser eller lagringsytor. Det kan förbättra resursutnyttjandet utan att säkerheten måste bygga på en gemensam, bred tillitszon. Isoleringen behöver dock testas och följas upp; den uppstår inte automatiskt för att plattformen använder containrar eller virtuella maskiner.

DORA:s undersökning 2024 visade positiva samband mellan interna plattformar och produktivitet, men också risker för sämre leveransstabilitet och genomströmning. Det är en påminnelse om att värdet beror på plattformens faktiska användbarhet och på att team kan arbeta självständigt [K016].

## Det nya beroendet: plattformen själv

När många IT-stöd använder samma gemensamma förmågor blir de samtidigt beroende av att dessa förmågor fungerar. Ett fel i identitetstjänsten eller en central nätverkskomponent kan påverka många tidigare fristående IT-stöd. Fel i leveransplattformen kan i stället främst hindra nya driftsättningar utan att redan körande applikationer nödvändigtvis stannar. Plattformsmodellen avskaffar alltså inte operativa risker. Den **samlar vissa risker för att kunna hantera dem mer systematiskt**.

Det kräver kapacitetsplanering, tydlig förändringshantering och medveten utformning av felgränser. Plattformen bör så långt möjligt kunna uppdateras utan att alla anslutna applikationer måste förändras samtidigt. Tillgängligheten för plattformens gemensamma förmågor behöver följas upp separat från tillgängligheten för varje sammanhängande IT-stöd. Versionsgränser och kompatibilitetslöften blir viktiga. När en gemensam tjänst ska förändras måste dess användare förstå hur lång tid äldre gränssnitt stöds och vilka tester som krävs.

Det finns också en ekonomisk sida. En gemensam plattform behöver finansieras och underhållas även när enskilda utvecklingsprojekt avslutas. Om budgeten bara täcker det initiala teknikinförandet och inte plattformens fortsatta produktutveckling försämras tjänsterna över tid. Plattformsteamets viktigaste arbete är ofta inte att bygga mer teknik, utan att hålla standardvägarna enkla, säkra och relevanta när behoven förändras.

## Nya fallgropar

Den första fallgropen är **portalen utan verklig självbetjäning**: den ser modern ut men leder fortfarande till manuella köer. Den andra är **den alltför omfattande plattformen**, där ett centralt team försöker tillgodose varje tänkbart specialfall innan någon standardväg är riktigt användbar.

En tredje fallgrop är att skapa ett plattformsmonopol. Om alla team måste använda samma verktyg, oavsett behov och risk, kan standardisering bli ett hinder för förändring. En bra plattform ger begripliga standardval och en hanterad undantagsväg, inte en teknisk låsning för sin egen skull.

En fjärde fallgrop är att **gömma ansvar bakom automatiken**. Att en databas kan beställas självständigt betyder inte att någon annan automatiskt tar ansvar för dess informationsinnehåll, kapacitet, återställningskrav eller kostnader. Självbetjäning måste därför kopplas till tydligt ägarskap. Slutligen kan en plattform utvecklas till en ny central flaskhals om alla nya standardvägar, undantag och förändringar kräver plattformsteamets manuella arbete. CNCF:s mognadsmodell skiljer uttryckligen mellan standardiserade verktyg och faktisk självbetjäning [K014].

## Organisationen kring plattformen

I en etablerad plattformsmodell ansvarar ett eller flera plattformsteam för gemensamma förmågor som **interna produkter**. Det innebär en tydlig målgrupp, dokumenterade tjänster, utvecklingsplan, supportmodell och regelbunden återkoppling. Utvecklingsteamen ansvarar för sina applikationer och deras produktionsbeteende inom plattformens ramar. Driftens specialistkompetens behövs fortsatt, men används mer till att bygga och driva återanvändbara förmågor än till att manuellt konfigurera varje ny instans.

Arkitekturfunktionen behöver arbeta med begripliga principer för gränssnitt, data, identitet och beroenden snarare än med godkännande av varje teknikval. Säkerhetsfunktionen behöver formulera testbara krav och skapa möjlighet till riskbaserade undantag. Förvaltningen och verksamhetsägarna behöver fastställa vilka användarflöden som är kritiska och vilket ansvar som gäller för hela IT-stödet.

Det finns ingen enda organisationskarta som fungerar överallt. Några organisationer har ett gemensamt plattformsteam, andra flera specialiserade tjänsteteam. Avgörande är inte vad de heter utan **vilka förmågor de levererar, vem som får fatta beslut och hur avvikelser hanteras**. Den mer detaljerade ansvarsfördelningen behandlas i nästa kapitel.

## Ett ärendehanteringsstöd på plattformen

Det fiktiva ärendehanteringsstödet från tidigare kapitel kan nu bestå av flera tjänster som utvecklas av olika team. Tidigare behövde varje team samordna nya miljöer, brandväggsregler, databaser och övervakning med driftorganisationen. I den plattformsorienterade miljön väljer teamen en godkänd tjänstetyp, deklarerar sina beroenden och får automatiskt en miljö med rätt grundskydd.

När dokumenttjänsten behöver en ny databasinstans sker det med standardiserade kapacitets- och återställningsval. När en aviseringstjänst behöver kommunicera med ärendetjänsten fastställs identitet och åtkomst genom explicita policyer. När användaren inte kan slutföra ett ärende kan den sammanhängande transaktionen följas genom de berörda tjänsterna. Plattformen ger förutsättningarna, men den ansvarige för IT-stödet måste fortfarande säkerställa att hela ärendeflödet fungerar och prioriteras rätt.

Detta är också gränsen för plattformsmodellen: den gör gemensamma problem lättare att lösa en gång för många, men den kan inte ersätta förståelsen för verksamhetslogiken.

## När modellen är lämplig – och när den bör begränsas

En etablerad plattformsorienterad modell passar särskilt väl när flera team återkommande behöver likartade tekniska förmågor och manuella specialbeställningar är en väsentlig källa till väntetider och variation. Den förutsätter att organisationen kan finansiera och bemanna en långlivad intern tjänst och att utvecklarna faktiskt väljer att använda den.

Den bör däremot inte göras mer avancerad än behovet kräver. Om organisationen har få IT-stöd, låg förändringstakt eller otillräcklig drifts- och utvecklingskompetens kan enklare standardmiljöer och förbättrad automatisering vara ett bättre första val än att bygga en omfattande intern plattform. Den viktigaste kontrollfrågan är inte hur många plattformsfunktioner som finns, utan om de minskar friktionen och samtidigt förbättrar kontrollen över riskerna.

Ett praktiskt sätt att bedöma nyttan är att följa hur lång tid det tar att få en fungerande miljö, hur mycket manuellt arbete som återstår, hur ofta förändringar orsakar störningar och hur självständiga utvecklingsteamen faktiskt är. Man bör också följa kostnader, säkerhetsavvikelser och hur snabbt ett IT-stöd kan återställas. Framgång är inte hög kataloganvändning i sig, utan bättre förmåga att leverera och förvalta digital nytta.

## Sammanfattning

Den plattformsorienterade modellen bygger på ett tydligt byte av perspektiv. Tidigare organiserades mycket av driften kring beställningar för enskilda system. Nu erbjuds gemensamma förmågor genom återanvändbara gränssnitt och säkra standardvägar, så att utvecklingsteam kan förändra sina tjänster utan att varje steg blir ett nytt manuellt ärende.

Det ger snabbare och mer enhetliga leveranser, men också nya beroenden till plattformen och ett större behov av explicita ansvar. **Plattformen tar ansvar för det gemensamma; applikationsteamen för det applikationsspecifika; tjänsteägaren för att det samlade IT-stödet fungerar för verksamheten.** Hur dessa ansvar kan organiseras utan nya stuprör är nästa kapitels huvudfråga.
