# Lemmikloomade hoiukodu muudatuste analüüs

Tegija: Alex Tarakanov

Hoiukodu süsteem aitab loomaomanikul broneerida lemmikule ajutise hoiukoha. Kooli söökla ülesande neli muudatust on siin kohandatud hoiukodu tööle. Tellija soovib, et muudatused oleksid kasutamiseks valmis kahe kuu jooksul.

## 1. Projekti peamised nõuded

| Kooli söökla nõue | Lemmikloomade hoiukodu nõue |
| --- | --- |
| 1. Õpilane broneerib lõunasöögi telefonist. | Loomaomanik saab telefoni brauseris valida kuupäevad ja lemmiku, vaadata vabu hoiukohti ning teha broneeringu. |
| 2. Õpilane näeb toidu koostisosi ja allergeene. | Loomaomanik näeb enne broneerimist hoiukoha tingimusi ning hoiukodu pakutava sööda koostisosi ja märgitud allergeene. |
| 3. Söökla töötaja muudab päevamenüüd. | Hoiukodu töötaja saab muuta valitud päeva hoiukohtade saadavust ja sel päeval pakutava sööda infot. Muudatused kuvatakse omaniku vaates. |
| 4. Õpilane saab kinnitatud broneeringu teavituse. | Kui broneering saab oleku „Kinnitatud“, saadab süsteem omanikule e-kirja broneeringu numbri, lemmiku nime ja hoiuperioodiga. |

## 2. Funktsionaalsed ja mittefunktsionaalsed nõuded

**Funktsionaalsed nõuded**

- Omanik saab otsida vabu kohti, broneerida hoiukoha, vaadata oma broneeringuid ja broneeringu enne hoiuperioodi algust tühistada. Salvestamisel kontrollitakse saadavust uuesti, et sama kohta ei broneeritaks kattuvaks ajaks kaks korda.
- Süsteem kuvab enne kinnitamist hoiukoha tingimused ja valitud päevade sööda info. Puuduv koostise või allergeenide info kuvatakse kui „Info puudub“.
- Töötaja saab muuta kuupäevapõhist saadavust ning sööda nimetust, koostisosi ja allergeene. Saadavuse muutmisel kontrollib süsteem, kas see läheks vastuollu kinnitatud broneeringuga.
- Süsteem saadab kinnituskirja automaatselt pärast broneeringu kinnitamist. Korduv kinnitussündmus ei tohi tekitada teist kirja. Saatmisvea korral jääb broneering kinnitatuks ja kirja saatmist saab korrata.

**Mittefunktsionaalsed nõuded**

- Broneerimisvaade kohandub telefoni ja arvuti ekraanile. Telefonis peab saama kogu broneeringu teha ilma lehte külgsuunas kerimata.
- Omanik pääseb ligi ainult enda broneeringutele ja lemmikute andmetele. Päevapõhist saadavust ja sööda infot saab muuta ainult töötaja.
- Vormidel kuvatakse selged veateated ning hoiukoha ja sööda info on loetav ka väikesel ekraanil.

Kahe kuu tähtaeg on projekti ajapiirang. Selleks ajaks peavad kõik neli muudatust olema testitud ja kasutusvalmis.

## 3. Kasutajarollid

| Roll | Tegevused |
| --- | --- |
| Loomaomanik | Vaatab hoiukoha tingimusi ja sööda infot, broneerib telefonist, haldab enda broneeringuid ning saab kinnituskirja. |
| Hoiukodu töötaja | Haldab broneeringuid, muudab päevade kaupa kohtade saadavust ja sööda infot ning registreerib looma saabumise ja lahkumise. |

## 4. Arendusmudel ja ajakava

Kasutaksin inkrementaalset arendusmudelit. Tellija saab iga etapi lõpus valminud osa proovida ja anda tagasisidet. Nii saab telefonis broneerimist testida enne ülejäänud muudatuste valmimist.

| Aeg | Tulemus |
| --- | --- |
| 1.–2. nädal | Täpsustan nõuded ja täiendan broneerimise maketti. Valmib mobiilivaade koos kuupäevavaliku ja saadavuse kontrolliga. |
| 3.–4. nädal | Lisan hoiukoha tingimused ning sööda koostise ja allergeenide kuvamise. Töötaja saab muuta päevapõhist infot. |
| 5.–6. nädal | Lisan broneeringu kinnituskirja ja kontrollin saatmise veaolukordi. |
| 7.–8. nädal | Testin nelja muudatust koos, parandan vead ja teen tellijaga vastuvõtutesti. |

## 5. Muudetavad või täiendatavad süsteemiosad

| Projektiosa | Muudatus |
| --- | --- |
| [Broneerimise makett](makett/screen1.png) | Lisan telefonis kasutatava kuupäevavaliku ning hoiukoha ja sööda detailid enne broneeringu kinnitamist. |
| [Töötaja vaate makett](makett/screen2.png) | Lisan valitud päeva saadavuse ja sööda info muutmise vormi. |
| [Kasutusjuhtude diagramm](diagrammid/screen1.png) | Lisan telefonist broneerimise, sööda info vaatamise, päevaandmete muutmise ja kinnituskirja saatmise. |
| [Klassidiagramm](diagrammid/screen2.png) ja andmemudel | Lisan hoiukoha tingimused, kuupäevapõhise saadavuse ja sööda andmed. Seon teavituse broneeringu ning selle omanikuga. |
| Broneerimise ja teavitamise loogika | Lisan saadavuse korduskontrolli broneerimisel ning käivitan e-kirja saatmise, kui kinnitatud olek on salvestatud. |

### Vastuvõtutest

1. Omanik avab süsteemi telefonis, valib lemmiku ja kuupäevad ning esitab broneeringu.
2. Enne esitamist näeb omanik hoiukoha tingimusi, sööda koostisosi ja märgitud allergeene.
3. Töötaja muudab valitud päeva sööta ja vaba koha saadavust. Omaniku vaates kuvatakse sama päeva uuendatud andmed.
4. Kui broneering on kinnitatud, saab omanik ühe e-kirja õigete broneeringuandmetega.
