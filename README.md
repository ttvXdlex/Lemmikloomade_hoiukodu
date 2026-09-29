# Lemmikloomade hoiukodu

Süsteem, mis aitab loomaomanikel broneerida oma lemmikule hoiukoha
ajaks, mil nad ise kohal ei ole, ning hoiukodul jälgida, kes ja millal
loomi hoiule toob.

**Tegija:** [Alex Tarakanov]

## Kasutajad ja nõuded
Kaks rolli: loomaomanik ja hoiukodu töötaja. Kuus kasutajalugu on
Issues all, tähtsamad on märgitud `must`.

## Arendusmudel
Töötan inkrementaalselt: kõigepealt vabade kohtade nägemine ja
broneerimine, siis tühistamine ja töötaja vaade, viimasena
meeldetuletused. Nii saan iga osa valmimise järel süsteemi juba
kasutada ja järgmisi samme kohandada. Kosemudel ei sobi, sest kõiki
nõudeid pole alguses täpselt teada — näiteks pole selge, kas
meeldetuletused üldse vajalikud on, ja seda selgub alles kasutamise
käigus.

## Diagrammid
![Kasutusjuhud](diagrammid/Screenshot_2026-09-29_090413.png)
![Klassid](diagrammid/klassid.png)

## Makett
Tegime ekraanid iteratiivselt, sest tahtsime kohe näha, kuidas
broneerimine ja loomade nimekiri kokku sobivad.
![Broneerimine](makett/broneerimine.png)
![Loomade nimekiri](makett/loomade-nimekiri.png)

## Kuidas ma töötasin
Tahvel alguses ja lõpus: `protsess/`. 
[3 lauset retrospektiivi: mis läks hästi, mis oli raske, mida teeksid teisiti]
