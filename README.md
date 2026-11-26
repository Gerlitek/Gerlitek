# Hi / Moi

<img src="./assets/gerlitek-mark-tight.png" alt="Gerlitek logo" width="20" height="20">&nbsp;*In Finnish below. Suomeksi alempana.*

I like to start from a small, real problem, prototype it quickly with AI, test it on real data, and keep only what
turns out to be useful. Privacy and "does it actually work?" come first.

Most of my repositories are private. **I can send you a private link to a case study, give read access to a
repository, or walk through the code on a call. Just ask.**

## Selected work

- **[Ylläri-Zombit](https://github.com/Gerlitek/zombiet-peli):** a browser game on Azure, live at
  [zombit.gerlitek.fi](https://zombit.gerlitek.fi) (in Finnish, on a computer). Phaser 4 and TypeScript, the whole Azure side in Bicep.
  - **Cost guards:** budget, anomaly alert and Azure Policy rules that block expensive resources; the API stops itself at a daily cap.
  - **No secrets:** Python API on Functions Flex Consumption with a managed identity, storage keys disabled. GitHub Actions
    signs in with OIDC, is scoped to one resource group, and every deploy waits for approval.
  - **Data in layers:** raw JSON events (30 days) → nightly curated Parquet with versioned cleaning rules → a
    [stats page](https://zombit.gerlitek.fi/tilastot/) from one summary file.
  - **Debugging:** hanging requests traced to Flex's default concurrency.
- **[Kimallus](https://github.com/Gerlitek/kimallus-peli):** a calm, picture-first browser game, live at
  [kimallus.gerlitek.fi](https://kimallus.gerlitek.fi) (in Finnish). AWS deployment in progress.
  - **Front:** TypeScript and Canvas 2D with vector art drawn in code; React for the stats page and a lazily loaded
    leaderboard island fed by `useSyncExternalStore`.
  - **Score API:** Lambda and DynamoDB, built and tested locally. Conditional writes keep each session's best, a sparse
    GSI serves the top ten with one Query, and names are word-list indexes, never free text.
  - **Serverless by design:** Lambda Function URL behind CloudFront (OAC), no fixed-cost resources, daily request caps.
  - **Two IaC tools, clear split:** Terraform for the account baseline (budget, GitHub OIDC role), CDK in TypeScript for the app.
- **[AI Radar](https://ai.gerlitek.fi):** a curated daily view of AI news, research and releases (FI/EN). An hourly
  pipeline collects RSS and API sources, filters by keywords, removes duplicates and scores the items. PHP and MySQL.
  Code is private; happy to go through it on request.
- **[wilmaton-wilma](https://github.com/Gerlitek/wilmaton-wilma):** puts Wilma exams and teachers' messages into
  iCloud calendars with reminders. Messages are interpreted by a local LLM (Ollama), so nothing leaves the machine;
  read-only towards Wilma. Unofficial, in Finnish.
- **[photo-tidy](https://github.com/Gerlitek/photo-tidy):** photo orientation with a local vision model and UTF-8 EXIF captions.

---

## Suomeksi

Aloitan pienestä, oikeasta ongelmasta, teen nopean prototyypin tekoälyn kanssa, testaan sen oikealla datalla ja jätän
jäljelle vain sen, mikä osoittautuu hyödylliseksi. Yksityisyys ja se, että asia oikeasti toimii, tulevat ensin.

Useimmat reponi ovat yksityisiä. **Voin lähettää yksityisen linkin case studyyn, antaa lukuoikeuden repoon tai käydä
koodin läpi näytön jaolla. Kysy vain.**

### Valitut työt

- **[Ylläri-Zombit](https://zombit.gerlitek.fi):** selainpeli Azuressa, koko pilvipuoli koodina (Bicep). Kulusuojat,
  salasanaton kirjautuminen (OIDC, hallittu identiteetti) ja data kahdessa kerroksessa yöajoineen.
- **[Kimallus](https://kimallus.gerlitek.fi):** selainpeli TypeScriptillä, Canvas 2D:llä ja Reactilla. Pistepalvelu
  Lambdalla ja DynamoDB:llä; AWS-julkaisu (Terraform, CDK) työn alla.
- **[AI Radar](https://ai.gerlitek.fi):** päivittäinen näkymä tekoälyuutisiin. Tunneittain ajettava putki kerää,
  suodattaa ja pisteyttää lähteet.
- **[wilmaton-wilma](https://github.com/Gerlitek/wilmaton-wilma):** Wilman viestit ja tapahtumat kalenteriin
  paikallisen kielimallin avulla; mikään ei lähde koneelta.
- **[photo-tidy](https://github.com/Gerlitek/photo-tidy):** kuvien suunnan korjaus paikallisella näkömallilla.
