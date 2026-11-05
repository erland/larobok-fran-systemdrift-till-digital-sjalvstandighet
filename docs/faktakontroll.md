# Faktakontroll

Använd detta som arbetsregister. Det är inte automatiskt en publicerad källförteckning.

| ID | Kapitel | Påstående/faktaområde | Status | Källa/verifiering | Kontrollerad | Kommentar |
|---|---|---|---|---|---|---|
| F001 | Kapitel 1 | Nätverksperimeter ger inte ensam tillräckligt skydd; intern tillit behöver också hanteras | Verifierad | [K001] NIST SP 800-207 | 2026-11-04 | Används som nyansering av traditionell säkerhetsmodell |
| F002 | Kapitel 1 | Stora releaser ökar samordningsbehov och riskkoncentration | Verifierad | [K002] Continuous Delivery | 2026-11-04 | Används deskriptivt, inte som absolut regel |
| F003 | Kapitel 1 | Den traditionella modellen kan fortfarande vara rationell i vissa sammanhang | Verifierad | Författarens syntes med stöd i kapitlets resonemang | 2026-11-04 | Analytisk slutsats; inte ett statistiskt påstående |
| F004 | Kapitel 2 | Oberoende leverans och teamautonomi som arkitektoniska framgångskriterier | Verifierad mot publicerad vägledning | [K007] DORA löst kopplade team | 2026-11-04 | DORA framhåller tekniska och organisatoriska förutsättningar; påstår inte att en särskild topologi är nödvändig |
| F005 | Kapitel 2 | Distribuerade tjänster tillför data-, nätverks- och koordinationskomplexitet | Verifierad mot vägledning | [K008] Microsoft Architecture Center | 2026-11-04 | Vägledning, inte jämförande studie för varje organisation |
| F006 | Kapitel 2 | Test-, driftsättningsautomation och snabbt återkopplingsflöde som förmågor | Verifierad mot publicerad vägledning | [K009] DORA kontinuerlig leverans | 2026-11-04 | Forskningen gäller kontinuerlig leverans i flera arkitekturstilar |
| F007 | Kapitel 2 | Grundförmågor som provisionering, övervakning och deployment bör finnas innan tjänsteantalet ökar | Verifierad mot expertkälla | [K010] Fowler, Microservice Prerequisites | 2026-11-04 | Expertresonemang från 2014, inte populationstal |
| F008 | Kapitel 2 | Beredskap i applikation, infrastruktur, DevOps och team bör bedömas före uppdelning | Verifierad mot leverantörsvägledning | [K011] Microsoft readiness assessment | 2026-11-04 | Relevanta bedömningsdimensioner |
| F009 | Kapitel 3 | Mikrotjänster innebär flera rörliga delar, större operativ komplexitet, datakonsistens- och latensutmaningar | Verifierad mot publicerad arkitekturvägledning | [K008] Microsoft Learn, Microservices architecture style | 2026-11-04 | Vägledning, inte jämförande statistik |
| F010 | Kapitel 3 | Säker tjänstekommunikation kräver autentisering, auktorisation och motståndskraft | Verifierad mot NIST | [K012] NIST SP 800-204A | 2026-11-04 | Service mesh är ett möjligt sätt, inte ett obligatoriskt krav |
| F011 | Kapitel 3 | Cloud-native-enkät identifierade säkerhet, kostnad, kompetens, komplexitet, interoperabilitet och observability som gap | Verifierad mot publicerad enkät | [K004] CNCF Ecosystem Gaps 2024 | 2026-11-04 | Resultaten gäller tillfrågade molnnativa utvecklare |
| F012 | Kapitel 3 | Direkt delning av databasscheman skapar beroenden vid ändringar | Verifierad mot leverantörsvägledning | [K013] Microsoft Learn, data considerations | 2026-11-04 | Normativ rekommendation, inte absolut omöjlighet att dela databasserver |
| F013 | Kapitel 3 | Driftbeställningar och delade säkerhetszoner kan bli problem i större organisationer | Analytisk slutsats | Syntes av arkitekturexempel och [K004], [K008], [K012] | 2026-11-04 | Beskrivs som möjliga mönster, inte generell statistik |
| F014 | Kapitel 4 | Distribuerad arkitektur behöver både lokalt komponentägarskap och tvärgående samordning | Verifierad vägledning och författarsyntes | [K007], [K008], [K012] | 2026-11-04 | Slutsatsen kombinerar forsknings- och vägledningskällor |
| F015 | Kapitel 4 | Otydliga gränser mellan utveckling, drift och säkerhet kan bidra till utdragen incidentfelsökning | Analytisk slutsats | Konstruerat fall, syntes av [K004] och [K012] och kapitlets resonemang | 2026-11-04 | Formuleras som återkommande mönster, inte som universell regel |
| F016 | Kapitel 4 | Lokala mätetal kan vara otillräckliga när användarvärde produceras över flera tjänster | Verifierad/analytisk syntes | [K003] Accelerate och kapitelresonemang | 2026-11-04 | Baseras på samband mellan teamförmågor och leveransresultat, inte på en specifik måttmodell |

| F020 | Kapitel 5 | Plattformar bör ses som interna produkter med användarfokus och olika mognadsdimensioner | Verifierad mot publicerat ramverk | [K014] CNCF Platform Engineering Maturity Model | 2026-11-04 | Normativ mognadsmodell, inga kausalitetspåståenden |
| F021 | Kapitel 5 | IaC, policy as code, observerbarhet och automatiserade leveransflöden är relevanta i molnnativ DevSecOps | Verifierad mot standardvägledning | [K015] NIST SP 800-204C | 2026-11-04 | Gäller NIST:s referensarkitektur; inte krav att använda service mesh |
| F022 | Kapitel 5 | Interna utvecklarplattformar har blandade samband med produktivitet, stabilitet och genomströmning | Verifierad mot undersökningsrapport | [K016] DORA 2024 | 2026-11-04 | Enkätresultat; ingen generell kausal effekt |
| F023 | Kapitel 5 | Plattformen bör standardisera återkommande behov men behålla explicita ägar- och riskgränser | Analytisk rekommendation | Syntes av [K001], [K012], [K014]–[K016] | 2026-11-04 | Beskrivs som vägledande princip, inte universell organisationsmodell |

| F024 | Kapitel 6 | Plattform som intern produkt och utvecklarcentrerade standardvägar | Underlag kontrollerat | [K014], [K017] CNCF/DORA | 2026-11-04 | Vägledning, inte universell organisationsstruktur |
| F025 | Kapitel 6 | Plattformar kan gynna produktivitet men även påverka genomströmning och stabilitet negativt | Underlag kontrollerat | [K016] DORA 2024 | 2026-11-04 | Resultat av undersökning; ingen kausal garanti |
| F026 | Kapitel 6 | Säkerhet och drift kräver plattformskontroller och applikationsspecifikt ansvar | Underlag kontrollerat | [K001], [K015] NIST | 2026-11-04 | Exempel på ansvarsfördelning; konkreta ansvar fastställs lokalt |

| F027 | Kapitel 7 | Teamautonomi kräver att arkitektur och teamgränser medger oberoende leverans | Verifierad mot vägledning | [K007] DORA | 2026-11-04 | Rekommendation och observerade samband, inte universell topologi |
| F028 | Kapitel 7 | Plattformar behöver långsiktig produktledning och användaråterkoppling | Verifierad mot CNCF | [K014] CNCF Platform Engineering Maturity Model | 2026-11-04 | Normativ mognadsmodell |
| F029 | Kapitel 7 | Integrerad säkerhetsstyrning kan stödjas av DevSecOps | Verifierad mot NIST | [K015] NIST SP 800-204C | 2026-11-04 | Vägledning för arbetssätt, inte specifik ansvarsmatris |
| F030 | Kapitel 7 | SLO och incidentrutiner skiljer plattformskvalitet från användarflödets kvalitet | Verifierad mot fackvägledning | [K018] Google SRE | 2026-11-04 | Praktik som behöver anpassas till verksamhetskrav |

| F031 | Kapitel 8 | NIST beskriver livscykelbaserad hantering av risker i generativ AI | Verifierad mot primärkälla | [K019] NIST AI 600-1 | 2026-11-04 | Ramverk, inte en skyldighet att använda viss teknisk produkt |
| F032 | Kapitel 8 | Prompt injection och alltför omfattande agentmandat är kända riskkategorier | Verifierad mot publicerad vägledning | [K020] OWASP LLM Top 10 2025 | 2026-11-04 | Vägledning om hotkategorier, inte incidentfrekvens |
| F033 | Kapitel 8 | Riskklassning efter information, befogenhet och konsekvens samt successiv delegering | Analytisk rekommendation | Syntes med [K006], [K019], [K020] | 2026-11-04 | Tre nivåer är bokförfattarens exempel, inte officiell klassificering |
| F034 | Kapitel 8 | Kvalitet, identitet, integrationer och avveckling behöver hanteras vid verksamhetsbyggd IT | Analytisk syntes | [K019], [K020] och tidigare plattformskapitel | 2026-11-04 | Uppställningen av teknikförmågor är författarens rekommendation |

| F035 | Kapitel 9 | AI förstärker organisationers förutsättningar och kan ge kvalitetsrisker | Verifierad mot publicerad rapport | [K005] DORA 2025 | 2026-11-04 | Empiriska samband avser undersökningens respondenter |
| F036 | Kapitel 9 | Generativ AI kräver riskhantering genom hela livscykeln | Verifierad mot NIST-ramverk | [K019] NIST AI 600-1 | 2026-11-04 | Ramverk, inte en bindande juridisk klassning |
| F037 | Kapitel 9 | Prompt injection, överprivilegierade verktyg och informationsläckor är relevanta AI-risker | Verifierad mot OWASP | [K022] OWASP 2026 | 2026-11-04 | Hotkatalog som vägledning, inte empirisk incidensstatistik |
| F038 | Kapitel 9 | Tre nivåer för verksamhetsbyggd IT är författarens illustrativa beslutsstöd | Analytisk syntes | [K019] och bokens principer | 2026-11-04 | Ej officiell klassificering |

| F039 | Kapitel 10 | Interna plattformar behöver långsiktigt produktägarskap och användarorienterad utveckling | Verifierad mot publicerad modell | [K014] CNCF Platform Engineering Maturity Model | 2026-11-04 | Vägledning, inte universell organisationskarta |
| F040 | Kapitel 10 | AI förstärker organisationens styrkor och svagheter, bland annat kopplat till plattformens kvalitet | Verifierad mot empirisk rapport | [K005] DORA 2025 | 2026-11-04 | Gäller rapportens respondenter och samband |
| F041 | Kapitel 10 | AI-styrning kräver explicit ansvar och livscykelbaserad riskhantering | Verifierad mot NIST | [K006], [K019] | 2026-11-04 | Ramverk, inte specifik juridisk klassificering |
| F042 | Kapitel 10 | Dubbla IT-uppgifter och nivåindelad ansvarskarta kan minska ansvarsglapp | Analytisk syntes | Kapitlets resonemang, [K014] och [K019] | 2026-11-04 | Författarens rekommendation, inte empiriskt kausalsamband |

| F043 | Kapitel 11 | Arkitektur ska bedömas efter teamens självständiga leveransförmåga, inte en viss teknik | Stöds av publicerad vägledning | [K007] DORA Loosely Coupled Teams | 2026-11-04 | Riktlinje, inte bindande arkitekturkrav |
| F044 | Kapitel 11 | Plattform bör utvecklas som användarcentrerad intern produkt | Stöds av publicerad vägledning | [K014], [K017] | 2026-11-04 | Används för slutsatsen att efterfrågan och effekt ska mätas |
| F045 | Kapitel 11 | Grundläggande säkerhets- och AI-riskkontroller behöver ingå i beredskapsbedömning | Stöds av ramverk | [K001], [K006], [K015], [K019] | 2026-11-04 | Avser riskstyrning, inte universell checklista |
| F046 | Kapitel 11 | Tre möjliga vägval och fem beredskapsfrågor | Analytisk syntes | Bokens kapitel 1–10 och författarens beslutsmodell | 2026-11-04 | Ingen etablerad certifierad mognadsmodell; bedömningsstöd |

## Statusvärden
- Ej kontrollerad
- Verifierad
- Behöver uppdateras
- Osäker/omstridd
- Ej relevant

## Öppna verifieringspunkter
- Lägg till kapitelvisa verifieringspunkter i takt med att nya kapitel skapas.

## Publiceringskontroll
- [ ] Alla högprioriterade påståenden är verifierade.
- [ ] Statistik har årtal/definition där det behövs.
- [ ] Tidskänsliga uppgifter har kontrollerats på nytt.
- [ ] Källnoteringar som inte ska publiceras ligger utanför kapiteltexten.
