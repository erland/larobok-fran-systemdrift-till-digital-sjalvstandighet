# Kapitelplan

- Profil: `factbook`, analytisk faktabok
- Inledning: genomarbetad och automatiskt godkänd i revision 0024
- Riktad innehållsrevision i revision 0025: kapitel 2, 4, 5 och 7–11 omgranskade och godkända; dokumentation i `docs/innehallsrevision-r0025.md`
- Kapitel 1: automatiskt granskat och godkänt
- Publiceringsurval revision 0028: bilder i kapitel 1–9 borttagna, endast figurerna i kapitel 10 och 11 kvarstår
- Kapitel 2: automatiskt granskat och godkänt
- Kapitel 3: automatiskt granskat och godkänt
- Kapitel 4: automatiskt granskat och godkänt
- Kapitel 5: automatiskt granskat och godkänt
- Kapitel 6: automatiskt granskat och godkänt
- Kapitel 7–8: automatiskt granskade och godkända
- Kapitel 9: automatiskt granskat och godkänt
- Kapitel 10: automatiskt granskat och godkänt med IMG-10-01 renderad
- Kapitel 11: automatiskt granskat och godkänt, beslutsillustrationen IMG-11-01 verifierad
- Källregister: etablerat som gemensamt register för käll-ID

## Del I – När IT-stödet var en sammanhållen enhet

### Kapitel 1: Den traditionella IT-modellen
- Status: automatiskt granskat och godkänt
- Kärnfråga: Varför fungerade den traditionella modellen väl i många större organisationer?
- Centrala fakta: tydliga systemgränser, standardiserbar drift, hanterbar perimeter, rollspecialisering och begränsningar i form av stora releaser och intern koppling.
- Exempel/case: ärendehanteringssystem i större organisation.
- Käll-/verifieringsbehov: säkerhetsnyansering [K001], releasers samordningskostnader [K002].
- Granskningsprotokoll: `docs/reviews/01-den-traditionella-it-modellen.json`

### Kapitel 2: Förflyttningen till distribuerade IT-stöd
- Status: automatiskt granskat och godkänt
- Kärnfråga: när och varför övergår man från en sammanhållen leveransenhet till flera tjänster?
- Syfte: förklara drivkrafter, nya tekniska förmågor, nya ansvar, fallgropar och beslutskriterier.
- Centrala fakta: teamautonomi, kontrakt, dataägarskap, observabilitet, CI/CD, säker kommunikation och operativ beredskap.
- Fall: ärendehantering med separat aviseringstjänst som begränsat första steg.
- Granskningsprotokoll: `docs/reviews/02-forflyttningen-till-distribuerade-it-stod.json`.
- Källa/verifiering: [K007]–[K011], [K001].

## Del II – När komplexiteten flyttar in mellan tjänsterna

### Kapitel 3: Den distribuerade IT-miljön
- Status: automatiskt granskat och godkänt
- Granskningsprotokoll: `docs/reviews/03-den-distribuerade-it-miljon.json`
- Syfte: visa hur fler tjänster, nätverk, data och driftbeställningar förändrar helheten.
- Kärnfråga: varför kan mindre självständiga tjänster ge en svårare operativ helhet?
- Faktagrund: Microsofts mikrotjänstvägledning [K008], CNCF:s enkät [K004], NIST SP 800-204A [K012] och Microsofts datavägledning [K013].

### Kapitel 4: När ansvar och arkitektur inte längre passar ihop
- Status: automatiskt granskat och godkänt
- Granskningsprotokoll: `docs/reviews/04-nar-ansvar-och-arkitektur-inte-langre-passar-ihop.json`
- Syfte: synliggöra glappet mellan komponentansvar, plattformsansvar, förvaltningsansvar och ansvar för användarupplevelsen som helhet.
- Kärnfråga: vem äger helheten när användarflödet är sammanhängande men den tekniska lösningen och organisationen är uppdelad?
- Faktagrund: DORA/Accelerate [K003], Microsofts mikrotjänstvägledning [K008], NIST SP 800-204A [K012] och CNCF Ecosystem Gaps [K004].

### Kapitel 5: Förflyttningen till plattformsorienterad IT
- Status: automatiskt granskat och godkänt
- Syfte: beskriva teknikförmågor, plattformsarbete, ansvar och beslutsgrindar.
- Kärnfråga: hur kan gemensamma tjänster minska koordination utan att centralisera alla beslut?
- Teknik: IaC, CI/CD, identitet, policy as code, observabilitet, återställning, kataloger och golden paths.
- Organisation: produktifierade plattformsförmågor, specialistdrift, teamansvar, säkerhetskrav och helhetsägarskap.
- Beslutsgrind: återkommande problem, användarbehov, livscykelägarskap, säkerhetsförutsättningar och mätning.
- Källor: [K001], [K012], [K014]–[K016].

## Del III – IT som möjliggörande plattform

### Kapitel 6: Den plattformsorienterade IT-modellen
- Status: automatiskt granskat och godkänt
- Granskningsprotokoll: `docs/reviews/06-den-plattformsorienterade-it-modellen.json`
- Kärnfråga: hur kan återanvändbara plattformsförmågor ge självständiga team utan att helhetsansvar och säkerhet går förlorade?
- Teknik: självbetjäningsgränssnitt, standardvägar, identitet, databaser, driftsättning, säkerhet och isolering.
- Organisation: plattform som intern produkt, komponentägarskap och ägarskap för hela IT-stödet.
- Styrkor och risker: mindre manuellt arbete och jämn kvalitet kontra gemensamma felpunkter, överstandardisering och oklar ansvarsfördelning.
- Beslutsbedömning: nyttan mäts i teamens självständighet, driftsäkerhet och minskad väntetid, inte katalogens omfattning.
- Källor: [K001], [K014]–[K017].

### Kapitel 7: En ny ansvarsfördelning
- Status: automatiskt granskat och godkänt
- Kärnfråga: Hur fördelas mandat och operativt ansvar mellan IT-stöd, applikationer och plattform?
- Innehåll: produkt- och tjänsteägarskap, utveckling, plattform, drift, arkitektur, säkerhet, förvaltning, incidentledning och tjänstenivåmål.
- Faktagrund: DORA [K007], CNCF:s plattformsmognadsmodell [K014], NIST DevSecOps [K015] och Google SRE [K018].
- Granskningsprotokoll: `docs/reviews/07-en-ny-ansvarsfordelning.json`.

### Kapitel 8: Förflyttningen till verksamhetsdriven utveckling
- Status: automatiskt granskat och godkänt
- Kärnfråga: hur kan verksamheten skapa egna lösningar utan att säkerhet, tillgänglighet och förvaltning går förlorade?
- Tekniska förmågor: identitet, datakatalog, godkända API:er, AI-tjänster, styrda verktygsanrop, testning och publicering.
- Ansvar: verksamhetsägare, plattform, arkitektur, säkerhet, professionella utvecklare och informationsförvaltning.
- Beslutsgrind: risknivå, dataåtkomst, ägarskap, kontroller, driftsberedskap och när skalning är för tidig.
- Källor: [K006], [K019], [K020].
- Granskningsprotokoll: `docs/reviews/08-forflyttningen-till-verksamhetsdriven-utveckling.json`.

## Del IV – När verksamheten blir utvecklare

### Kapitel 9: Den AI-drivna och verksamhetsnära IT-modellen
- Status: automatiskt granskat och godkänt
- Granskningsprotokoll: `docs/reviews/09-den-ai-drivna-och-verksamhetsnara-it-modellen.json`
- Kärnfråga: hur kan många verksamhetsbyggda appar och AI-assistenter samexistera med robusta kärnsystem och tydligt ansvar?
- Innehåll: arkitektur, tre riskberoende användningskategorier, AI-agenters befogenheter, dataskydd, tillgänglighet, livscykel, styrkor och fallgropar.
- Källor: [K005], [K019]–[K022].

### Kapitel 10: IT-avdelningens framtida uppgift
- Status: automatiskt granskat och godkänt
- Granskningsprotokoll: `docs/reviews/10-it-avdelningens-framtida-uppgift.json`
- Kärnfråga: hur kan IT-avdelningen både möjliggöra verksamhetens utveckling och fortsätta ansvara för kritiska IT-stöd?
- Innehåll: två kompletterande IT-uppgifter, gemensamma förmågor, beslut och mandat, skillnad mellan utveckling och riskacceptans, drift- och förvaltningsansvar, när förändring är för tidig.
- Exempel: AI-assistent kring ärendehanteringsstödet.
- Källor: [K005], [K006], [K014], [K019].
- Illustration: IMG-10-01 – organisations- och ansvarskarta

### Kapitel 11: Att välja rätt nästa steg
- Status: automatiskt granskat och godkänt
- Granskningsprotokoll: `docs/reviews/11-att-valja-ratt-nasta-steg.json`
- Kärnfråga: när bör organisationen bevara, förenkla eller göra en målmedveten teknisk och organisatorisk förflyttning?
- Innehåll: verifierade behov, tre vägval, fem beredskapsfrågor, tekniska och organisatoriska förmågor, pilot och effektmätning.
- Fiktivt fall: ärendehanteringsstödet används för att jämföra de tre vägarna.
- Faktagrund: DORA [K007], [K017], CNCF [K014], NIST [K001], [K006], [K015], [K019].
- Illustration: IMG-11-01, beslutsflöde med tre alternativ och beredskapsgrind.

## Kvalitetsgräns

Varje generation behandlar arkitektur, ansvar, styrkor, fallgropar och tillämpbarhet. Varje förflyttning behandlar teknikförmågor, ansvar, nytta, förutsättningar och när förändring är för tidig.

## Bokövergripande granskning

Genomförd i revision 0024; se `docs/slutgranskning-r0024.md`. Kapitel 1–11 och deras versionsbundna granskningsprotokoll har bevarats oförändrade. Nästa fas är omslag och provsättning.
