# Offering "almost any song" legally — copyright strategy for Piano Dojo

Research ticket: GitHub issue #4 (part of #1). **Not legal advice** — a developer-oriented map of the copyright line and the safe paths, with the spots where a real lawyer is needed flagged. Jurisdiction focus: US law, with a note for EU/France (the user is French).

## TL;DR — the working model already exists

A commercial app has been doing exactly this for 15+ years: **iReal Pro**. Its entire legal theory is the premise of this ticket — it stores **only chord symbols, no melody and no lyrics**, ships with **no songs at all**, and lets the community share chord charts in its forum (charts with lyrics are removed) ([iReal Pro Help Center](https://technimo.helpshift.com/hc/en/3-ireal-pro/faq/128-melody-lyrics/), [iReal Pro forum – Copyrights and rules](https://forums.irealpro.com/threads/copyrights-and-rules.48/)). Piano Dojo should copy this posture: **be a tool for chords the user plays, not a catalog of transcribed songs.** Do that and "almost any song" is reachable with near-zero licensing exposure. The exposure appears the moment you add **melody, lyrics, tab, or printed sheet music** — those are the protected parts.

## 1. The copyright line

A song carries **two separate copyrights**: the **musical work / composition** (melody + harmony + lyrics) and the **sound recording** (the master), listed as distinct categories in **17 U.S.C. § 102(a)(2) and (a)(7)** ([Cornell LII](https://www.law.cornell.edu/uscode/text/17/102)). The owner's exclusive rights (reproduce, make derivatives, distribute, perform, display) are **§ 106**; the sound-recording right is narrowed by **§ 114**. Copyright never covers "any idea, procedure, process, system, method of operation, concept, principle" — **§ 102(b)** — and protection requires **originality**: independent creation plus a minimal spark of creativity (*Feist Publications v. Rural Telephone*, 499 U.S. 340 (1991)). Ranked from least to most protectable:

- **Chord progressions / lead-sheet chord grids — effectively NOT protectable.** They are common musical building blocks below the originality line. This is now strong, recent authority: in **Structured Asset Sales v. Sheeran** the courts held that a four-chord progression plus a syncopated harmonic rhythm is "ubiquitous in pop music" and too commonplace to protect, even as a "selection and arrangement" — the claim "fails as a matter of law" (S.D.N.Y. 2023, affirmed **2d Cir., Nov. 2024**, [Justia](https://law.justia.com/cases/federal/appellate-courts/ca2/23-905/23-905-2024-11-01.html)). *Skidmore v. Led Zeppelin* (9th Cir. en banc, 2020) reinforces that common musical elements are free to all. **Caveat:** a genuinely *original, distinctive* reharmonization copied slavishly from one arranger *could* cross into protected "selection and arrangement." Plain diatonic/pop grids do not.
- **Melody transcription — protectable.** The melody is the part courts actually protect (it drove *Blurred Lines* and the Sheeran suits). Transcribing it into notation reproduces protected expression; it does not create a fresh clean right. This is why the ticket's framing — chords the user plays and embellishes, *not necessarily the printed melody* — is the safe line.
- **Printed lead sheets / sheet music — protectable.** A printed lead sheet is a *copy* of the composition (and often adds an original arrangement/engraving). Distributing it is reproduction under § 106 and needs a **print license** from the publisher (Hal Leonard, Musicnotes / Sheet Music Direct, etc.).
- **Chord/tab sheets — treated as protected derivatives by publishers.** In 2006 the NMPA/MPA sent takedowns to tab sites arguing that even inaccurate transcriptions are unauthorized arrangements. Ultimate Guitar survived (then Russia-hosted) and *later signed licenses* with Sony, EMI, Hal Leonard, Music Sales, etc. ([Wikipedia: Ultimate Guitar](https://en.wikipedia.org/wiki/Ultimate_Guitar), [Computerworld, 2006](https://www.computerworld.com/article/1679484/publishers-no-heroes-to-aspiring-guitarists-in-ip-fight.html)). Lesson: those catalogs are *licensed to those platforms*, not free to redistribute — and the tab-vs-bare-chords distinction matters. Bare chord symbols (à la iReal Pro) have never been the target; full tabs with melody/lyrics were.
- **Lyrics — fully protectable literary works.** Displaying lyrics needs a license (LyricFind, Musixmatch — the reason Genius and UG pay for lyrics). Keep lyrics out and a whole rights layer disappears.
- **Audio recordings (masters) — fully protectable, two layers.** Using a real recording needs a **master license** (label) *and*, if synced to anything, a **sync license** (publisher). Not realistic for a free indie app. § 115's mechanical license explicitly does **not** let you duplicate someone else's sound recording ([§ 115, Cornell LII](https://www.law.cornell.edu/uscode/text/17/115)).

**EU / France.** French *droit d'auteur* protects "les compositions musicales avec ou sans paroles" — **CPI Art. L112-2, 5°** ([Légifrance](https://www.legifrance.gouv.fr/codes/article_lc/LEGIARTI000006278875)) — and any reproduction/représentation without consent is *contrefaçon* (Art. L122-4). Two differences from the US raise caution: (a) **there is no fair use** — only narrow statutory exceptions (courte citation, copie privée, Art. L122-5); (b) France has **no explicit "building blocks"/scènes-à-faire doctrine** — protection turns on *originalité* ("empreinte de la personnalité de l'auteur"), assessed case by case, and French courts lean composition-protective. A bare chord grid almost certainly lacks *originalité*, but this is **less litigated than the US Sheeran line — flag for a French avocat before monetizing.** Distributing actual compositions (e.g. rendered audio) in France runs through **SACEM/SDRM**.

## 2. Where a song→chords dataset can come from — ranked (legal safety × practicality)

| Rank | Source | Legal safety | Practicality (solo dev, free app) |
|---|---|---|---|
| 1 | **User chord entry (UGC)** — users type/confirm the chords; app is a tool | Highest — chords unprotectable; add a DMCA/takedown policy; strip lyrics | High. The iReal Pro model. Zero catalog to license. |
| 2 | **Public-domain songs** — US: published **1929 or earlier** (rolls forward yearly); plus trad/folk/classical | Highest — melody + chords + lyrics all free | High for a *coaching* app; great teaching repertoire, though thin on modern pop |
| 3 | **App-generated progressions & your own reharmonizations** | Highest — it's your content | High; also powers exercises/etudes |
| 4 | **McGill-Billboard dataset** — expert chord annotations for ~1,000 Billboard songs, **CC0** (cite the ISMIR paper) | High — CC0 chords-only; underlying songs stay ©, but you're using only chord labels | Medium; clean and citable but limited size |
| 5 | **MusicBrainz** — **CC0** core metadata ([Data License](https://musicbrainz.org/doc/About/Data_License)) | High — but **no chord data**; metadata only | Medium; use it for song identity/search scaffolding, not chords |
| 6 | **Hooktheory Trends API** — aggregate chord-transition statistics only | Medium — within ToS if you use the published API; **ToS forbids scraping/redistributing TheoryTab**, and there is **no full per-song API** ([API docs](https://www.hooktheory.com/api/trends/docs), [Terms](https://www.hooktheory.com/terms)) | Low for "song→chords"; it gives theory stats, not song sheets |
| 7 | **Chordonomicon** — 666k song chord progressions, chords-only ([arXiv 2410.22046](https://arxiv.org/abs/2410.22046), [GitHub](https://github.com/spyroskantarelis/chordonomicon)) | Medium/low — **scraped from user-generated sources; dataset license/provenance not clearly stated.** Chords lower the copyright risk, but the scraping provenance is a ToS/ethics problem | Medium; big and tempting — verify license on the HF repo before any use |
| 8 | **Scraping Ultimate Guitar / Chordify / e-chords** | **Avoid** — breaches ToS; possible contract/CFAA exposure; those catalogs are publisher-licensed to *them* | N/A |
| 9 | **License properly** — publisher print licenses / HFA / MLC / LyricFind | Highest if you add melody, tab, lyrics, or sheet music | Low — cost + admin overkill for a free solo app; only if you productize sheet music/lyrics |

**Recommended stack:** #1 + #2 + #3 as the core (user-entered + public-domain + your own progressions), optionally seeded with #4 (McGill-Billboard CC0) and #5 (MusicBrainz for song search/metadata). This gives "almost any song" — users can enter the chords for anything — while you personally ship only unprotectable or public-domain content.

## 3. Backing audio — ranked

1. **App-synthesized backing from chord symbols** (Web Audio / Tone.js, a soundfont or MIDI engine, drums/bass/comping generated live). **Best.** No master rights (you generate the audio), and if it's built only from chord symbols it reproduces **no protected melody** — so it also stays outside the composition copyright. This is precisely what iReal Pro does, and users may use its generated backing tracks freely.
2. **Your own recordings** of public-domain tunes or generic progressions — fully yours.
3. **Royalty-free / production-music loops** under a license that permits redistribution inside an app (read the license — many bar redistribution as a "sample pack").
4. **§ 115 mechanical (MLC blanket) rendering of actual compositions.** § 115 lets you make and distribute "phonorecords," including digital deliveries, of a nondramatic musical work; the arrangement privilege is narrow — "shall not change the basic melody or fundamental character of the work" — and grants no derivative-work rights ([§ 115, Cornell LII](https://www.law.cornell.edu/uscode/text/17/115)). **Only relevant if you render a specific song's actual melodic arrangement.** Legal but administrative; unnecessary if your backing is chord-only.
5. **Real commercial recordings** — master + sync licenses. **Avoid** for a free indie app.

## 4. Where you genuinely need a lawyer

- Confirming that *your specific* chord grids stay on the unprotectable side of "selection and arrangement" (unusual, distinctive reharmonizations copied from one source are the risk).
- **The French/EU position on bare chord grids** — no fair use, no building-blocks doctrine, *originalité* judged case-by-case. Get a French *avocat* / SACEM guidance before monetizing in France.
- Any move to add **melody, tab, lyrics, or sheet music**, or to use **any scraped dataset commercially** — that's licensing territory (publishers, HFA/MLC, LyricFind/Musixmatch).

## Sources
- 17 U.S.C. § 102 (subject matter; idea/expression) — https://www.law.cornell.edu/uscode/text/17/102
- 17 U.S.C. § 115 (compulsory mechanical license; arrangements; MLC) — https://www.law.cornell.edu/uscode/text/17/115
- *Feist Publications v. Rural Telephone Service*, 499 U.S. 340 (1991) (originality standard)
- *Structured Asset Sales, LLC v. Sheeran* (2d Cir. 2024) — https://law.justia.com/cases/federal/appellate-courts/ca2/23-905/23-905-2024-11-01.html
- Ultimate Guitar / NMPA-MPA takedowns — https://en.wikipedia.org/wiki/Ultimate_Guitar ; https://www.computerworld.com/article/1679484/publishers-no-heroes-to-aspiring-guitarists-in-ip-fight.html
- iReal Pro (chords-only legal posture; forum rules) — https://technimo.helpshift.com/hc/en/3-ireal-pro/faq/128-melody-lyrics/ ; https://forums.irealpro.com/threads/copyrights-and-rules.48/
- Hooktheory Terms + Trends API — https://www.hooktheory.com/terms ; https://www.hooktheory.com/api/trends/docs
- MusicBrainz Data License (CC0 core data) — https://musicbrainz.org/doc/About/Data_License
- McGill-Billboard chord dataset (CC0) — https://ddmal.ca/research/The_McGill_Billboard_Project_(Chord_Analysis_Dataset)/
- Chordonomicon dataset — https://arxiv.org/abs/2410.22046 ; https://github.com/spyroskantarelis/chordonomicon
- France: CPI Art. L112-2 (works protected, incl. musical compositions) — https://www.legifrance.gouv.fr/codes/article_lc/LEGIARTI000006278875
