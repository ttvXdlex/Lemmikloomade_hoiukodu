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
```mermaid
classDiagram
  class Loomaomanik {
    +String nimi
    +String epost
    +String telefon
    +registreeru()
    +broneeri()
  }
  class Lemmikloom {
    +String nimi
    +String liik
    +int vanus
    +String erivajadused
  }
  class Broneering {
    +Date algusKuupäev
    +Date lõppKuupäev
    +String staatus
    +kinnita()
    +tühista()
  }
  class Hoiukojukoht {
    +int number
    +boolean vaba
    +kontrolliVabadust()
  }
  class HoiukoduTöötaja {
    +String nimi
    +String roll
    +lisaHoiukoht()
    +vaataLoomad()
  }

  Loomaomanik "1" --> "*" Broneering
  Broneering "*" --> "1" Hoiukoht
  Broneering "1" --> "1" Lemmikloom
  HoiukoduTöötaja "1" --> "*" Hoiukoht
```

### Liidestuse skeem (Pangalingiga maksmine)
```mermaid
sequenceDiagram
  autonumber
  actor Kasutaja as Loomaomanik
  participant Hoiukodu as Hoiukodu süsteem
  participant Pank as Pangalink (Montonio)

  Kasutaja->>Hoiukodu: Vali kuupäevad ja klõpsa "Maksa pangalingiga"
  Hoiukodu->>Pank: Broneeringu ID, summa (EUR), loomaomaniku e-post, tagasisuunamise URL-id
  Pank-->>Kasutaja: Suuna panga makselehele (Swedbank, SEB, LHV)
  
  alt Makse õnnestub (tavapärane voog)
    Kasutaja->>Pank: Kinnita makse pangas PIN-koodiga
    Pank-->>Hoiukodu: Webhook: tehingu ID, staatus "PAID", digiallkiri
    Hoiukodu->>Hoiukodu: Valideeri digiallkiri ja märgi broneering "Kinnitatud"
    Pank-->>Kasutaja: Suuna tagasi hoiukodu lehele (success_url)
    Hoiukodu-->>Kasutaja: Kuva kinnitus: "Broneering tasutud ja kinnitatud!"
  else Makse ebaõnnestub või aegub (veaolukord)
    Pank-->>Hoiukodu: Webhook: staatus "FAILED" või timeout (15 min)
    Hoiukodu->>Hoiukodu: Vabasta broneeritud hoiukoht ja märgi "Tühistatud"
    Pank-->>Kasutaja: Suuna tagasi veateatega (cancel_url)
    Hoiukodu-->>Kasutaja: Teade: "Makse ebaõnnestus. Hoiukoht vabastati. Palun proovi uuesti."
  end
```
![Kasutusjuhud](diagrammid/screen1.png)
![Klassid](diagrammid/screen2.png)

## Makett
Tegin ekraanid iteratiivselt, sest tahtsin kohe näha, kuidas
broneerimine ja loomade nimekiri kokku sobivad.
![Broneerimine](makett/screen1.png)
![Loomade nimekiri](makett/screen2.png)
  
## Kuidas ma töötasin
Tahvel alguses ja lõpus: `protsess/`. 
[Ekraani paigutuse väljamõtlemine oli keeruline. Probleemid, mis olid märgitud kui "Kohustuslikud", olid kergesti lahendatavad. Ekraanipaigutuse väljamõtlemine oli keeruline. „Kohustuslikuks“ olid probleemid kergesti lahendatavad. Mudel valiti välja suuremate raskusteta.]
