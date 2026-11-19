# Hi / Moi

*In Finnish below. Suomeksi alempana.*

I like to start from a small, real problem, prototype it quickly with AI, test it on real data, and keep only what
turns out to be useful. Privacy and "does it actually work?" come first.

Most of my repositories are private. **I can send you a private link to a case study, give read access to a
repository, or walk through the code on a call. Just ask.**

## Selected work

- **[zombiet-peli](https://github.com/Gerlitek/zombiet-peli):** a small browser game I built with AI, and where I show my
  Azure work. It's live for anyone: [play it](https://zombit.gerlitek.fi) on a computer (in Finnish). Behind it runs
  this game's service with a score table:
  - **Costs under control:** a budget, an anomaly alert, and Azure Policy rules that block expensive resources and
    settings before they can be created.
  - **No passwords:** a Python API on Azure Functions' pay-per-use Flex Consumption plan (scales to zero, capped at one instance), reaching storage through a
    managed identity. Storage account keys can't be used at all, so there is no key to leak.
  - **Least privilege:** GitHub Actions signs in with OIDC, no secrets, and can only touch the game's own resource
    group. Subscription-level rights and policies stay with the owner, and every deploy waits for an approval.
  - **All as code:** the whole Azure side is Bicep, budget and policies included. The deploy pipeline previews each
    change with `what-if` and never deletes resources that are missing from the template.
  - **Data:** events land as raw files in Blob Storage and a lifecycle rule deletes them after 30 days. The score table
    lives in Table Storage.
  - **Debugging:** the project had real debugging across the Azure platform, the game code and the browser, and in the end the cause was found:
    Flex's default concurrency made requests hang.
- **[AI Radar](https://ai.gerlitek.fi):** a curated daily view of AI news, research and releases (FI/EN). An hourly
  pipeline collects RSS and API sources, filters by keywords, removes duplicates and scores the items. PHP and MySQL.
  Code is private; happy to go through it on request.
- **[wilmaton-wilma](https://github.com/Gerlitek/wilmaton-wilma):** puts Wilma exams and teachers' messages into
  iCloud calendars with reminders. Messages are interpreted by a local LLM (Ollama), so nothing leaves the machine;
  read-only towards Wilma, 149 tests. Unofficial, in Finnish.
- **[photo-tidy](https://github.com/Gerlitek/photo-tidy):** photo orientation with a local vision model and UTF-8 EXIF captions.

---

## Suomeksi

Aloitan pienestä, oikeasta ongelmasta, teen nopean prototyypin tekoälyn kanssa, testaan sen oikealla datalla ja jätän
jäljelle vain sen, mikä osoittautuu hyödylliseksi. Yksityisyys ja se, että asia oikeasti toimii, tulevat ensin.

Useimmat reponi ovat yksityisiä. **Voin lähettää yksityisen linkin case studyyn, antaa lukuoikeuden repoon tai käydä
koodin läpi näytön jaolla. Kysy vain.**

### Valitut työt

- **[zombiet-peli](https://github.com/Gerlitek/zombiet-peli):** pieni selainpeli, jonka tein tekoälyn kanssa ja jolla
  näytän Azure-osaamista. Peli on kaikkien saatavilla netissä: [pelaa](https://zombit.gerlitek.fi) tietokoneella.
  Azuressa pyörii tämän pelin palvelu pistetaulukkoineen:
  - **Kulut kuriin:** budjetti, poikkeamahälytys ja Azure Policy -säännöt, jotka estävät kalliit resurssit ja asetukset
    jo ennen kuin ne ehtivät syntyä.
  - **Ei salasanoja:** Python-API pyörii Azure Functionsin käytönmukaisella Flex Consumption -tasolla (skaalautuu nollaan, enintään yksi instanssi) ja käyttää
    tallennustilaa hallitulla identiteetillä. Tallennustilaan ei pääse avaimilla ollenkaan, joten vuotavaa avainta ei ole.
  - **Pienet oikeudet:** GitHub Actions kirjautuu OIDC:llä, ilman salasanoja, ja pääsee vain pelin omaan
    resurssiryhmään. Tilaustason oikeudet ja policyt ovat vain omistajalla, ja jokainen julkaisu odottaa hyväksyntää.
  - **Kaikki koodina:** koko Azure-puoli on Bicepiä, myös budjetti ja policyt. Julkaisuputki esikatselee jokaisen
    muutoksen `what-if`illa eikä koskaan poista resursseja, jotka puuttuvat mallista.
  - **Data:** tapahtumat tallentuvat raakadatana Blob Storageen, ja elinkaarisääntö poistaa ne 30 päivän kuluttua.
    Pistetaulukko on Table Storagessa.
  - **Debuggausta:** projektiin kuului vian etsimistä Azuren alustasta, pelin koodista ja selaimesta, ja lopulta syy löytyi:
    Flexin oletusrinnakkaisuus jumitti pyyntöjä.
- **[AI Radar](https://ai.gerlitek.fi):** kuratoitu päivittäinen näkymä tekoälyuutisiin, tutkimukseen ja julkaisuihin (FI/EN).
  Tunneittain ajettava putki kerää RSS- ja API-lähteet, suodattaa avainsanoilla, poistaa toistot ja pisteyttää.
  PHP ja MySQL. Koodi ei ole julkinen; käyn sen läpi pyydettäessä.
- **[wilmaton-wilma](https://github.com/Gerlitek/wilmaton-wilma):** vie Wilman kokeet ja opettajien viestit
  iCloud-kalentereihin muistutuksineen. Viestit tulkitsee paikallinen kielimalli (Ollama), joten mikään ei lähde
  koneelta; vain luku Wilmaan päin, 149 testiä. Epävirallinen, suomenkielinen.
- **[photo-tidy](https://github.com/Gerlitek/photo-tidy):** kuvien suunnan korjaus paikallisella näkömallilla ja UTF-8-kuvatekstit EXIFiin.
