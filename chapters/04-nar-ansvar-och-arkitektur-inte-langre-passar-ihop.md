# 4. När ansvar och arkitektur inte längre passar ihop

När organisationer går från ett mindre antal sammanhållna IT-stöd till många mindre tjänster förändras inte bara den tekniska arkitekturen. Även själva logiken för ansvar förändras. Problemet är att detta ofta sker ojämnt. Arkitekturen delas upp först, medan ansvar, styrning, budget, driftmodeller och förvaltningsformer i hög grad fortsätter att vara organiserade som om IT-stödet fortfarande vore en sammanhållen leveransenhet.

Det är då friktionen uppstår.

Ingen enskild grupp behöver göra ett uppenbart misstag för att helheten ska bli svår att styra. Utvecklingsteam kan ta rimligt ansvar för sina tjänster. Driftsorganisationen kan arbeta seriöst med nätverk, databaser, övervakning och säkerhetskrav. Arkitekturfunktionen kan försöka skapa ordning genom principer och granskningar. Förvaltningen kan ta ansvar för budget, prioritering och verksamhetskontakt. Ändå kan användaren möta ett IT-stöd där förändringar tar lång tid, incidenter är svåra att felsöka och ingen riktigt äger hela användarresan.

Detta kapitel diagnostiserar glappet mellan en distribuerad arkitektur och en äldre ansvarskarta. Hur ansvar sedan kan fördelas i en plattformsmodell behandlas i kapitel 7.

## Från tydlig systemägare till splittrat delansvar

I den traditionella modellen kunde ett IT-stöd ofta förstås som ett system med en tydlig insida och utsida. I den distribuerade miljön blir det i stället vanligt att en och samma användarfunktion bygger på flera tjänster med olika livscykler, olika ägare och olika operativa beroenden.

En användare som registrerar ett ärende kan till exempel möta en enda knapp eller ett enda arbetsflöde, men i bakgrunden passerar informationen genom ett API-lager, en ärendetjänst, en dokumenttjänst, en notifieringstjänst, en sökfunktion och kanske en integrationskomponent mot ett annat system. Någon ansvarar för användargränssnittet, någon annan för själva ärendehanteringen, någon tredje för identitet eller behörighet och någon fjärde för infrastrukturen där allt körs.

Det innebär att det som tidigare uppfattades som ett system allt oftare fungerar som en **sammansatt tjänst**. För användaren är det fortfarande ett sammanhängande IT-stöd, men internt är det uppdelat i flera komponenter och ansvarsytor. Därmed uppstår en central fråga: **vem ansvarar för helheten när helheten inte längre sammanfaller med en teknisk komponent?**

Samma användarflöde kan vila på flera ansvarsnivåer. Ett utvecklingsteam kan äga sin tjänst, plattformsteamet kan ansvara för gemensamma driftförmågor och säkerhetsfunktionen kan ange krav och kontrollera efterlevnaden. Om ingen uttryckligen samordnar det sammanhängande IT-stödets funktion i produktion blir användarperspektivet lätt underrepresenterat i vardagen.

## Fyra typer av ansvar som ofta blandas ihop

En orsak till problemen är att ordet *ansvar* används för flera olika saker på samma gång. I diskussioner om distribuerad arkitektur blir det därför viktigt att skilja mellan åtminstone fyra typer av ansvar.

### 1. Ansvar för en teknisk komponent

Detta är ansvaret för att en viss tjänst, databas eller integrationskomponent fungerar, kan förändras och kan driftsättas. Det är ofta detta ansvar som utvecklingsteamen tydligast tar när mikrotjänstarkitektur eller teamautonomi införs. Komponenten får en ägare, ett repo, en releaseprocess och en tydlig teknisk livscykel [K008].

### 2. Ansvar för en gemensam teknisk förmåga

Vissa delar av miljön används av många tjänster samtidigt: nätverk, identitet, observabilitet, databasmotorer, CI/CD-plattformar, containerplattformar, certifikat, hemligheter och säkerhetskontroller. Dessa förmågor ägs sällan av ett enskilt produktteam, utan av drift-, infrastruktur- eller plattformsteam.

### 3. Ansvar för verksamhetsnyttan

Ett IT-stöd finns inte för att enskilda komponenter ska fungera var för sig. Det finns för att stödja ett verksamhetsflöde. Därför behövs någon form av ansvar för prioriteringar, kvalitet, livscykel och avvägningar utifrån verksamhetens behov. I en enkel systemvärld kunde detta ansvar ofta samlas i ett förvaltningsobjekt eller runt en systemägare. I en distribuerad miljö riskerar motsvarande ansvar att bli svagare om det inte ges en tydlig form.

### 4. Ansvar för den operativa helheten

Detta ansvar handlar om hur den samlade lösningen fungerar i produktion: tillgänglighet, övervakning, incidenthantering, återställning, beroenden och tvärgående förändringar. I praktiken är detta ofta det ansvar som faller mellan stolarna. Varje team kan övervaka sin tjänst, men ingen har nödvändigtvis mandat att snabbt samordna alla beroenden när användarflödet som helhet påverkas.

När dessa fyra ansvarstyper blandas ihop uppstår lätt missförstånd. Ett team kan exempelvis säga att det "äger tjänsten", medan verksamheten uppfattar att teamet därmed också äger hela användarupplevelsen. Drift kan uppfatta att säkerhet är central infrastruktur, medan utveckling ser säkerhet som något som främst ska byggas in i tjänsterna. Båda kan ha delvis rätt och ändå tala om olika ansvarsnivåer.

## Varför glappet uppstår

Ansvarsglappet är inte bara en följd av att organisationen är dåligt strukturerad. Det uppstår ofta därför att flera rimliga principer drar åt olika håll samtidigt.

### Teamautonomi ökar den lokala tydligheten

Många moderna arkitekturmodeller strävar efter att ge team större självständighet. Det är ofta klokt. Team som kan testa och leverera med få beroenden till andra team har bättre förutsättningar för snabb förändring [K007]. Teamstorlek eller en viss tjänsteindelning garanterar däremot inte detta. Men ju mer ansvar som förs närmare komponentnivån, desto viktigare blir det att också ordna ansvar på system- eller tjänstenivå.

### Gemensam infrastruktur kräver central samordning

Samtidigt går det sällan att låta varje team bygga allt själv. Nätverk, IAM, säkerhetsramverk, hemlighetshantering, backup, loggning och containerplattformar behöver ofta standardiseras. Det leder naturligt till centralisering eller åtminstone specialiserade team. Därmed skapas nya beroenden mellan produktteam och gemensamma förmågor.

### Ekonomi och styrning följer inte alltid arkitekturen

Budget, bemanning och uppföljning organiseras ofta enligt äldre strukturer: system, förvaltningsobjekt, organisatoriska enheter eller projektkategorier. Men den nya arkitekturen skär tvärs igenom dessa gränser. Det kan innebära att ett team optimeras för sin egen backlogg medan den verksamhetskritiska användarresan korsar flera budget- och beslutslinjer.

### Säkerhet och drift vill minska variation

Drift- och säkerhetsfunktioner har ofta starka skäl att vilja begränsa variation. Färre plattformar, färre mönster och färre specialfall kan förenkla kontroll och minska den operativa variationen. Utvecklingsteam vill samtidigt kunna välja lösningar som passar deras problem. Om denna motsättning inte hanteras med tydliga principer kan central styrning uppfattas som byråkratisk, medan lokal autonomi kan uppfattas som riskabel eller odisciplinerad. Det är en organisatorisk riskbedömning; CNCF:s rapport [K004] beskriver närliggande teknik- och kompetensutmaningar, inte ett universellt orsakssamband.

## Symtom på att ansvar och arkitektur inte längre passar ihop

Det finns flera återkommande tecken på att organisationens ansvarsfördelning inte längre matchar dess tekniska verklighet.

### Incidenter studsar mellan grupper

När en användarnära funktion slutar fungera börjar ofta en felsökning som hoppar mellan flera parter. Utvecklingsteam pekar på infrastruktur. Infrastruktur pekar på applikationslogik. En integrationstjänst pekar på en underliggande beroendetjänst. Återkommande pendlande felsökning kan vara ett tecken på att ansvar finns för delarna men inte fullt ut för helheten. En enstaka incident räcker däremot inte som bevis för bristande ansvarsfördelning.

### Ingen har hela bilden av beroenden

I distribuerade landskap växer beroendena snabbt. Om ingen samlar och underhåller en gemensam bild av kritiska kedjor, återställningsordning och beroendekritikalitet blir organisationen sårbar. Detta gäller särskilt när olika tjänster utvecklas av olika team men tillsammans levererar samma användarvärde.

### Förändringar samordnas informellt

Ett annat tecken är att viktiga förändringar kräver personberoende koordination. Teamen lyckas leverera, men bara därför att erfarna nyckelpersoner känner till vem som måste kontaktas, vilka beroenden som finns och hur man får saker att fungera i praktiken. När mycket vilar på sådan informell kunskap är ansvarskartan för svag.

### Mätetal speglar lokala mål men inte helheten

Ett team kan mäta ledtid, releasefrekvens eller svarstider för sin egen tjänst. Drift kan mäta plattformstillgänglighet. Säkerhet kan mäta patchnivå eller sårbarheter. Men om ingen samtidigt mäter användarflöden, tvärgående tillgänglighet och faktisk återställningsförmåga riskerar organisationen att optimera lokalt medan helheten försämras.

### Förvaltningen blir osäker på sin roll

Många organisationer har väl etablerade former för förvaltning av system. Men när ett verksamhetsstöd blir en sammansatt tjänst av flera delar blir det oklart vad som egentligen ska förvaltas. Är det komponenterna var för sig, de gemensamma förmågorna eller hela användarflödet? Om denna fråga inte besvaras blir också budget, prioriteringar och förändringsansvar otydliga.

## Vanliga feltolkningar

När ansvarsglappet blir synligt finns det några vanliga men otillräckliga slutsatser som ofta dras.

### "Utveckling måste ta allt ansvar"

Detta låter ibland attraktivt eftersom komponentägarna då också förväntas bära det operativa ansvaret. Problemet är att utvecklingsteam sällan ensamma kan äga nätverk, plattform, IAM, gemensamma säkerhetskontroller och många tvärgående beroenden. Om allting formellt flyttas till utveckling utan att stödstrukturen förändras skapas mest en ny otydlighet.

### "Drift måste återta kontrollen"

Den motsatta slutsatsen är att central drift måste återta mer ansvar för samordning och kvalitet. Det kan lösa vissa ordningsproblem på kort sikt, men riskerar att återinföra manuella beställningsmönster, lokala köer och en ansvarsfördelning som inte skalar när många team behöver förändra snabbt.

### "Vi behöver bara tydligare processer"

Processförbättringar kan hjälpa, men de räcker inte om själva arkitekturen och teamstrukturen drar åt olika håll. Ett återkommande problem i distribuerade miljöer är just att processen försöker kompensera för att den underliggande ansvarskartan inte passar verkligheten.

Det är därför mer hjälpsamt att se situationen som ett **designproblem**. Både arkitektur och organisation måste utformas så att ansvar kan tas på rätt nivå.

## Vad ett fungerande ansvarsmönster behöver innehålla

Ett moget distribuerat landskap behöver inte att allting ägs av en enda funktion. Däremot behöver det tydliga och kompletterande ansvarsnivåer.

### Ett uttalat ägarskap för verksamhetsstödet

Någon måste ha mandat att företräda det sammanhängande IT-stödet som verksamheten faktiskt använder. Detta ansvar behöver inte innebära att samma part bygger alla komponenter, men det måste innebära att någon kan prioritera användarflöden, avvägningar, tvärgående kvalitet och större förändringsbehov.

### Tydligt komponentansvar

Varje tjänst eller komponent behöver tydligt ägarskap för kod, schemaförändringar, releaser, observerbarhet och initial felsökning. Det behöver framgå vem som agerar när en tjänst påverkar andra, även om själva komponentansvaret är väl definierat.

### Tydliga gemensamma förmågor

Plattform, drift och säkerhet behöver definiera vad de ansvarar för och på vilka villkor dessa förmågor används. Om ansvar för exempelvis certifikat, backup, nätverksregler eller loggning är tvetydigt blir gränssnitten mellan team snabbt konfliktytor.

### En gemensam incident- och förändringsmodell

När flera team bidrar till samma användarvärde behöver organisationen ha ett gemensamt sätt att hantera störningar och större förändringar. Det gäller särskilt tvärgående incidenter, beroendeuppdateringar och återställningsövningar. En praktisk modell kan utse en incidentledare för det drabbade användarflödet, en ansvarig för att kalla in berörda team och en utsedd person som kommunicerar med verksamheten. NIST:s vägledning behandlar hur säker kommunikation och motståndskraft kan genomföras enhetligt mellan mikrotjänster [K012]; den föreskriver inte någon viss organisationskarta.

## Exempel: när ett ärendeflöde bryts

Föreställ dig att en användare inte längre kan slutföra ett ärende i en större ärendehanteringsmiljö. Följande är ett konstruerat exempel, inte en dokumenterad incident. Webbgränssnittet fungerar fortfarande. Ärendetjänsten svarar ibland långsamt. Dokumenttjänsten har nyligen uppdaterats. En notifieringstjänst ligger i samma nätverkszon som flera andra delade tjänster. Identitetstjänsten har samtidigt fått en ny certifikatkonfiguration.

Ur användarens perspektiv är detta ett fel i ett enda IT-stöd. Men internt finns flera möjliga orsaker och flera ansvariga funktioner. Om organisationen saknar ett tydligt ägarskap för hela ärendeflödet riskerar felsökningen att organiseras runt komponentgränser i stället för runt det faktiska användarproblemet.

Den här typen av situation visar varför distribuerad arkitektur nästan alltid behöver kompletteras med en mer medveten ansvarskarta. Annars får organisationen det sämsta av två världar: teknisk uppdelning utan motsvarande operativ tydlighet.

## Vad detta betyder för nästa steg

När ansvar och arkitektur inte längre passar ihop uppstår ett tryck mot nya arbetssätt. Organisationen behöver skapa former där gemensamma tekniska förmågor kan tillhandahållas standardiserat, samtidigt som produkt- eller utvecklingsteam får tillräcklig självständighet för att arbeta effektivt. Det är här nästa stora förflyttning tar form: från distribuerad komplexitet till plattformsorienterad IT.

Poängen är inte att återgå till den gamla världen, utan att bygga en ny modell där lokalt ansvar, gemensamma förmågor och helhetsansvar stödjer varandra i stället för att konkurrera.

## Centrala slutsatser

- Distribuerad arkitektur behöver hantera flera ansvarsnivåer samtidigt: komponent, plattform, verksamhetsnytta och operativ helhet.
- Problem uppstår ofta inte därför att ansvar saknas helt, utan därför att olika ansvarstyper blandas ihop.
- Ett sammanhängande användarflöde kan bygga på flera tjänster med olika ägare, vilket kräver tydligare samordning än i en traditionell systemmodell.
- Lokalt optimerade mål och mätetal räcker inte om ingen samtidigt ansvarar för det samlade IT-stödets funktion i produktion.
- En fungerande modell kräver både komponentägarskap och någon form av uttalat ägarskap för verksamhetsstödets helhet.

## Begrepp att känna till

- **Komponentansvar:** Ansvar för en specifik teknisk del, exempelvis en tjänst eller en databas.
- **Operativ helhet:** Hur ett sammanhängande IT-stöd fungerar i produktion över flera komponenter och team.
- **Gemensam teknisk förmåga:** En plattformstjänst eller infrastrukturtjänst som används av flera team eller system.
- **Användarflöde:** Den kedja av steg som användaren upplever som en sammanhängande funktion.
- **Ansvarsglapp:** Skillnaden mellan den tekniska strukturens behov av samordning och den organisatoriska ansvarsfördelning som faktiskt finns.

## Sammanfattning

Kapitel 3 visade att den distribuerade IT-miljön skapar fler beroenden, fler tjänster och större operativ komplexitet. Detta kapitel har visat den organisatoriska konsekvensen av samma utveckling: ansvar börjar fördelas på fler nivåer än tidigare, medan användarens behov fortfarande är sammanhängande.

När komponentansvar, plattformsansvar och ansvar för verksamhetsnyttan inte hålls isär blir det lätt otydligt vem som ska ta ansvar för den operativa helheten. Det leder till incidenter som studsar mellan grupper, informell samordning och mätetal som optimerar delarna snarare än IT-stödet som helhet.

Nästa steg är därför inte att välja mellan utveckling eller drift, utan att skapa en modell där gemensamma förmågor blir tydliga och självbetjäning kan införas med bibehållet sammanhang. Det är utgångspunkten för den plattformsorienterade förflyttningen i nästa kapitel.
