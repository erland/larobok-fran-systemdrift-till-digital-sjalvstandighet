# Provsättning och layoutkontroll – revision 0027

**Bok:** Från systemdrift till digital självständighet  
**Datum:** 2026-11-04  
**Underlag:** verifierad revision 0026, med författarens godkända omslagsbild.

## Genomförd provexport

- PDF producerad med Pandoc och XeLaTeX: **124 sidor**, **170 × 240 mm**.
- EPUB3 producerad med Pandoc, omslag och inbyggd navigationsförteckning.
- EPUB-validering: **16 XHTML-dokument, 115 interna länkar**; 12 SVG-illustrationer och omslagsbilden finns i paketet.
- PDF innehåller 12 vektorillustrationer, fungerande länkar och sökbar text.
- Bokkapitel, inledning, källregister och deras tidigare granskningsprotokoll är oförändrade.

## Upptäckta och åtgärdade layoutbrister

1. **Tom första sida:** PDF-mallens `\newgeometry` skapade en blank sida före omslaget. Omslaget ritas nu direkt på första sidan.
2. **Oproportionerligt lång innehållsförteckning:** PDF-mallens innehållsdjup har minskats från två till en rubriknivå under kapitel. Den tryckta innehållsförteckningen visar fortfarande kapitel och huvudavsnitt.
3. **Ofullständiga publiceringsmetadata:** PDF innehåller nu titel, författare och ämne. En permanent projektbunden UUID-identifierare har lagts till i `book.yaml` för EPUB.

## Kontrollerade utfall

- Förstasida och titelsida, innehållsförteckning, inledning, kapitelstarter, ett urval illustrationssidor och källregistrets sista sida har visuellt granskats i renderad PDF.
- Textblock i PDF ligger inom sidytan enligt automatisk sidgränskontroll.
- EPUB har separat nav.xhtml med kapitelankare och omslag; navigationssidan ligger inte som vanlig lässida.
- Sökbara/klickbara PDF-länkar samt interna EPUB-länkar finns; lokal exportvalidering godkänd.
- Samtliga 12 käll-SVG och genererade SVG godkända av diagramskriptet.
- Det godkända omslaget är oförändrat; inga nya bilder har skapats.

## Kvarstående publiceringskontroll

- **Små etiketter i flera tekniska illustrationer.** Vektor-PDF och EPUB går att förstora, men vissa diagramtexter uppskattas till omkring 3–5 punkter på den tryckta sidan. För en slutlig tryckutgåva rekommenderas förenklade figurer eller särskilda uppslag/större figurformat. Detta blockerar inte en digital provutgåva men bör åtgärdas inför tryckrelease.
- Kontrollera läsupplevelsen i minst två faktiska EPUB-läsare och utför ett sista visuellt korrektur av den kompletta PDF-utgåvan före publicering.
- Ingen extern sakkunniggranskning har utförts inom denna layoutrevision.

**Status:** Godkänd teknisk **provutgåva**, inte ännu slutligt tryck-/publiceringsgodkännande.
