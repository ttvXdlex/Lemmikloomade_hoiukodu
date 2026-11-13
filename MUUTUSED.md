# Lemmikloomade hoiukodu muudatuste analüüs

Tegija: Alex Tarakanov

Projekti eesmärk on võimaldada loomaomanikul broneerida oma lemmikule ajutine hoiukoht ning aidata hoiukodu töötajal jälgida broneeringuid ja loomade saabumist ning lahkumist. Tellija soovib, et muudatused oleksid kasutamiseks valmis kahe kuu jooksul alates töö algusest.

## 1. Millised on projekti peamised nõuded?

- Loomaomanik peab saama valida hoiuperioodi, vaadata selleks ajaks vabu kohti ja broneerida sobiva koha.
- Broneeringuga tuleb siduda loomaomaniku kontaktandmed ning looma andmed, sealhulgas liik ja erivajadused.
- Omanik peab saama vaadata oma broneeringu staatust ja broneeringu tühistada. Tühistamisel vabaneb koht selleks perioodiks.
- Töötaja peab saama hallata hoiukohti ja broneeringuid ning märkida, millal loom saabus ja lahkus.
- Süsteem peab kaitsma isikuandmeid, töötama telefonis ja arvutis ning olema tähtajaks testitud ja kasutusvalmis.

## 2. Funktsionaalsed ja mittefunktsionaalsed nõuded

| Liik | Nõue |
| --- | --- |
| Funktsionaalne | Omanik saab registreeruda, sisse logida ja hallata oma lemmiku andmeid. |
| Funktsionaalne | Süsteem kuvab valitud kuupäevadel vabad hoiukohad ja kontrollib saadavust uuesti broneeringu salvestamisel. Kui kaks inimest üritavad sama kohta kattuvaks ajaks broneerida, saab kinnituse ainult üks broneering. |
| Funktsionaalne | Omanik saab vaadata oma broneeringuid ja neid enne hoiuperioodi algust tühistada. |
| Funktsionaalne | Töötaja saab vaadata broneeringute nimekirja, lisada hoiukohti ning registreerida looma saabumise ja lahkumise. |
| Mittefunktsionaalne | Juurdepääs on rollipõhine. Omanik näeb ainult enda loomi ja broneeringuid ning töötaja näeb tööks vajalikke andmeid. |
| Mittefunktsionaalne | Broneerimisvorm ja töötaja vaade peavad olema kasutatavad nii telefonis kui ka arvutis. Puuduvate või vigaste andmete korral kuvatakse selge veateade. |

Kahe kuu tähtaeg on projekti ajapiirang. Enne üleandmist tuleb kontrollida broneerimist, sama koha topeltbroneerimise tõkestamist, tühistamist, töötaja vaadet ja kasutajaõigusi.

## 3. Millised kasutajarollid on süsteemis?

| Roll | Tegevused |
| --- | --- |
| Loomaomanik | Lisab oma lemmiku andmed, otsib vaba hoiukohta, esitab broneeringu ning vaatab või tühistab enda broneeringuid. |
| Hoiukodu töötaja | Haldab hoiukohti ja broneeringuid, vaatab loomade erivajadusi ning registreerib saabumise ja lahkumise. |

## 4. Millist arendusmudelit kasutaksin ja miks?

Kasutaksin inkrementaalset arendusmudelit. Iga etapi lõpus saab tellija proovida valminud osa ja anda tagasisidet. Nii saab broneerimise põhiprotsessi varakult läbi proovida ning jätta viimased nädalad testimiseks ja parandusteks.

| Aeg | Tulemus |
| --- | --- |
| 1.–2. nädal | Täpsustan nõuded, täiendan makette ja andmemudelit ning loon vabade kohtade otsingu. |
| 3.–4. nädal | Lisan broneerimise, kattuvuse kontrolli, broneeringu staatuse kuvamise ja tühistamise. |
| 5.–6. nädal | Lisan töötaja vaate, hoiukohtade halduse ning saabumise ja lahkumise märkimise. |
| 7.–8. nädal | Testin kasutusvooge ja ligipääsuõigusi, parandan vead ning teen tellijaga vastuvõtutesti. |

README-s kavandatud meeldetuletuste ja pangalingi prioriteedi täpsustan tellijaga. Ajakavas on esikohal broneerimine ja hoiukohtade haldus.

## 5. Milliseid olemasoleva süsteemi osi tuleks muuta või täiendada?

| Olemasolev projektiosa | Kavandatav muudatus |
| --- | --- |
| [Broneerimise makett](makett/screen1.png) | Täiendan kuupäevavalikut, vabade kohtade kuvamist, looma valimist ja broneeringu kinnitust. Lisan vaate oma broneeringute vaatamiseks ja tühistamiseks. |
| [Loomade nimekirja makett](makett/screen2.png) | Lisan töötaja vaatesse kuupäeva- ja olekufiltri, looma erivajadused ning saabumise ja lahkumise märkimise. |
| [Kasutusjuhtude diagramm](diagrammid/screen1.png) | Täpsustan omaniku ja töötaja tegevusi ning kirjeldan tühistamise ja koha puudumise juhtumeid. |
| [Klassidiagramm](diagrammid/screen2.png) ja [README](README.md) | Täpsustan broneeringu seoseid omaniku, looma ja hoiukohaga ning kirjeldan olekud. Saadavus tuleb arvutada valitud kuupäevade ja aktiivsete broneeringute järgi. |
| Broneerimisloogika ja ligipääs | Rakendamisel lisan serveripoolse kuupäevade, kattuvuse ja kasutajaõiguste kontrolli. Testin ka kahe samaaegse broneeringu katset. |

**Vastuvõtutest.** Omanik leiab vaba koha ja teeb broneeringu. Teine omanik proovib sama kohta samaks ajaks broneerida ning süsteem keeldub. Esimene omanik tühistab broneeringu ja koht muutub taas valitavaks. Töötaja märgib uue broneeringu puhul looma saabumise ja lahkumise ning kontrollib, et olekud kajastuvad töötaja vaates.
