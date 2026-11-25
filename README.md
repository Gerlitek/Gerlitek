# Hi / Moi

<img src="./assets/gerlitek-mark-tight.png" alt="Gerlitek logo" width="20" height="20">&nbsp;*In Finnish below. Suomeksi alempana.*

I like to start from a small, real problem, prototype it quickly with AI, test it on real data, and keep only what
turns out to be useful. Privacy and "does it actually work?" come first.

Most of my repositories are private. **I can send you a private link to a case study, give read access to a
repository, or walk through the code on a call. Just ask.**

## Selected work

- **[Ylläri-Zombit](https://github.com/Gerlitek/zombiet-peli):** a small browser game I built with AI, running on Azure
  with the whole cloud side written as code. It's live for anyone: [play it](https://zombit.gerlitek.fi) on a computer (in Finnish). Behind it runs
  this game's service with a score table:
  - **Costs under control:** a budget, an anomaly alert, and Azure Policy rules that block expensive resources and
    settings before they can be created. The API also counts its own requests and stops itself for the rest of the
    day if a daily cap is reached, and logging has a daily cap too.
  - **No passwords:** a Python API on Azure Functions' pay-per-use Flex Consumption plan (scales to zero, capped at one instance), reaching storage through a
    managed identity. Storage account keys can't be used at all, so there is no key to leak.
  - **Least privilege:** GitHub Actions signs in with OIDC, no secrets, and can only touch the game's own resource
    group. Subscription-level rights and policies stay with the owner, and every deploy waits for an approval.
  - **All as code:** the whole Azure side is Bicep, budget and policies included. The deploy pipeline previews each
    change with `what-if` and never deletes resources that are missing from the template.
  - **Data in two layers:** game events land as raw JSON in Blob Storage and are deleted after 30 days. A nightly
    function turns them into a curated layer (Parquet, partitioned by day): it drops test sessions, duplicates and
    implausible games (broken event order, more kills than the game can spawn), and leaves nicknames out. The
    cleaning rules are versioned, so a rules change rebuilds the affected days. The score table lives in Table Storage.
  - **Dashboard:** a [statistics page](https://zombit.gerlitek.fi/tilastot/) (Chart.js) reads one summary file the
    nightly run writes. No database queries per visitor, no third-party analytics.
  - **Debugging:** requests hung, and the cause turned out to be Flex's default concurrency.
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

- **[Ylläri-Zombit](https://github.com/Gerlitek/zombiet-peli):** pieni selainpeli, jonka tein tekoälyn kanssa ja joka
  pyörii Azuressa, koko pilvipuoli koodina. Peli on kaikkien saatavilla netissä: [pelaa](https://zombit.gerlitek.fi) tietokoneella.
  Azuressa pyörii tämän pelin palvelu pistetaulukkoineen:
  - **Kulut kuriin:** budjetti, poikkeamahälytys ja Azure Policy -säännöt, jotka estävät kalliit resurssit ja asetukset
    jo ennen kuin ne ehtivät syntyä. API laskee myös omat pyyntönsä ja pysäyttää itsensä loppupäiväksi, jos
    vuorokausikatto täyttyy. Lokeilla on oma päiväkatto.
  - **Ei salasanoja:** Python-API pyörii Azure Functionsin käytönmukaisella Flex Consumption -tasolla (skaalautuu nollaan, enintään yksi instanssi) ja käyttää
    tallennustilaa hallitulla identiteetillä. Tallennustilaan ei pääse avaimilla ollenkaan, joten vuotavaa avainta ei ole.
  - **Pienet oikeudet:** GitHub Actions kirjautuu OIDC:llä, ilman salasanoja, ja pääsee vain pelin omaan
    resurssiryhmään. Tilaustason oikeudet ja policyt ovat vain omistajalla, ja jokainen julkaisu odottaa hyväksyntää.
  - **Kaikki koodina:** koko Azure-puoli on Bicepiä, myös budjetti ja policyt. Julkaisuputki esikatselee jokaisen
    muutoksen `what-if`illa eikä koskaan poista resursseja, jotka puuttuvat mallista.
  - **Data kahdessa kerroksessa:** pelin tapahtumat tallentuvat raakadatana (JSON) Blob Storageen ja poistuvat
    30 päivän kuluttua. Yöllinen ajo jalostaa ne curated-kerrokseksi (Parquet, päiväkohtaiset osiot): se pudottaa
    testipelit, tuplat ja epäuskottavat pelit (rikkinäinen tapahtumajärjestys, enemmän tappoja kuin peli ehtii tuottaa
    zombeja) eikä vie nimimerkkejä mukanaan. Siivoussäännöt on versioitu, joten sääntömuutos rakentaa vanhat päivät
    uudelleen. Pistetaulukko on Table Storagessa.
  - **Tilastot:** [tilastosivu](https://zombit.gerlitek.fi/tilastot/) (Chart.js) lukee yhden valmiin yhteenvedon,
    jonka yöajo kirjoittaa. Ei tietokantakyselyitä kävijää kohden eikä kolmannen osapuolen analytiikkaa.
  - **Debuggausta:** pyynnöt jumittuivat, ja syyksi löytyi Flexin oletusrinnakkaisuus.
- **[AI Radar](https://ai.gerlitek.fi):** kuratoitu päivittäinen näkymä tekoälyuutisiin, tutkimukseen ja julkaisuihin (FI/EN).
  Tunneittain ajettava putki kerää RSS- ja API-lähteet, suodattaa avainsanoilla, poistaa toistot ja pisteyttää.
  PHP ja MySQL. Koodi ei ole julkinen; käyn sen läpi pyydettäessä.
- **[wilmaton-wilma](https://github.com/Gerlitek/wilmaton-wilma):** vie Wilman kokeet ja opettajien viestit
  iCloud-kalentereihin muistutuksineen. Viestit tulkitsee paikallinen kielimalli (Ollama), joten mikään ei lähde
  koneelta; vain luku Wilmaan päin, 149 testiä. Epävirallinen, suomenkielinen.
- **[photo-tidy](https://github.com/Gerlitek/photo-tidy):** kuvien suunnan korjaus paikallisella näkömallilla ja UTF-8-kuvatekstit EXIFiin.
