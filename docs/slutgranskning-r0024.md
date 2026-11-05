# Bokövergripande manusgranskning – revision 0024

**Bok:** Från systemdrift till digital självständighet  
**Författare:** Erland Lindmark  
**Granskning:** 4 november 2026  
**Omfattning:** Inledning, elva kapitel, källregister, samtliga tolv illustrationer och projektets stödregister.

## Bedömning

Den röda tråden är konsekvent: först beskrivs en generation, sedan dess begränsningar och därefter den tekniska respektive organisatoriska förflyttningen. Generationerna beskrivs som analysmodeller, inte en universell mognadstrappa. De tre avsedda läsargrupperna får relevant material i samma huvudberättelse. Boken håller isär etablerad praxis, rekommenderade arbetssätt och framtidsbedömningar om AI.

**Status:** Manusets struktur och inre konsekvens är redaktionellt genomgångna. De elva tidigare godkända kapitlen har inte ändrats. Inledningen har omarbetats och fått ett separat versionsbundet automatiskt godkännande. Det är inte detsamma som oberoende vetenskaplig sakkunniggranskning eller godkänd färdig PDF/EPUB.

## Genomförda rättningar

| Område | Iakttagelse | Åtgärd |
|---|---|---|
| Inledning | För kort orientering för de tre läsarsätten; figurernas begränsningar outtalade | Inledningen utvecklad med läsvägar, generationsbegreppet, fyra delar, fiktivt exempel och skillnaden mellan etablerat och prognos |
| Terminologi | Begreppen intern utvecklarplattform, självbetjäning och tjänstenivåmål återkom i listan; standardväg/golden path hade överlappande definition | Dubbletter borttagna, standardväg samordnad, observerbarhet/observabilitet förklarade som synonymer |
| Källregister | K022 angav fel månad för OWASP:s 2026-utgåva | Ändrat till september 2026 och direktlänk till OWASP:s resurs; K020 fått direktlänk till 2025-utgåvan |
| Projektstatus | Äldre formuleringar beskrev den samlade manusgranskningen som ännu inte genomförd | Projektindex, kapitelplan och status uppdaterade |

## Områden som granskats

**Progression:** Kapitel 1–2 beskriver äldre IT och första uppdelningen; 3–5 det distribuerade landskapets problem och vägen till plattform; 6–8 plattformsmodellen, ansvar och förberedelser för verksamhetsutveckling; 9–11 AI-scenariot, IT:s dubbla roll och beslut. Övergångarna fungerar och slutkapitlet sammanfattar utan att göra generation 4 till obligatoriskt mål.

**Upprepningar:** Ingen identisk längre löptext återkommer mellan kapitlen. Återkommande begrepp som helhetsansvar, självbetjäning och riskbaserad styrning har olika funktion i respektive kapitel (problem, förflyttning, etablerad modell respektive beslut). Vissa sammanfattningar återger tidigare argument, men det är en del av kapitlens vägledande struktur och bedöms inte kräva omfattande strykningar i denna revision.

**Källor:** 22 identifierade poster med unika K-ID; 21 hänvisas uttryckligen i boktexten och en är en kompletterande fördjupningskälla. Samtliga hänvisningar i manus återfinns i registret. DORA:s teamkoppling, CNCF:s plattformsmognadsmodell, NIST:s AI-agentinitiativ och OWASP:s 2026-utgåva har dessutom stickprovskontrollerats mot primärkällor denna revisionsomgång. Källregistret skiljer mellan undersökningar, ramverk, vägledning och författarsyntes. Fullständig ny kontroll av alla originalkällors varje sakuppgift är inte genomförd i denna övergripande omgång; tidigare kapitelprotokoll kvarstår.

**Illustrationer:** 12 SVG-källor och 12 genererade SVG-filer finns. Alla har kontrollerats i en gemensam översiktsrendering samt genom projektets SVG-säkerhetsvalidering. Schematiska flöden och ansvarsillustrationer motsvarar bokens modeller. En del figurer har mycket små etiketter när de minskas till en enda boksida; det är en **sättningsfråga**, och bör kontrolleras i faktiskt PDF/EPUB-format innan release (eventuellt större figurplacering, helsidesillustration eller landskapsbilaga).

**Teknisk konsistens:** Sammanfogning i `book.yaml`-ordning har kontrollerats; alla stabila figur-ID:n finns, alla bildreferenser går till faktiska SVG-filer och inga interna K-ID saknas. Projektets automatiska validering och revisionsintegritet ska köras efter incheckningen av denna granskningsrapport.

## Återstående steg före publiceringsklar bok

1. Ta fram omslaget när manus och bildspråk är fastställda, i enlighet med författarens önskemål.
2. Skapa faktiska PDF- och EPUB-provbyggen och granska deras läsbarhet, figurernas detaljstorlek, sidbrytningar, länkar, innehållsförteckning och navigation.
3. Kontrollera tidskänsliga källor igen inför utgivning och gör vid behov extern ämnessakkunniggranskning.
4. Genomför en sista korrekturläsning av de färdigformgivna utgåvorna.

**Sammanfattande beslut:** Redaktionsgranskning av manus och interna projektreferenser genomförd; godkänt att gå vidare till omslag och provsättning, **inte** ännu att publicera som slutlig utgåva.
