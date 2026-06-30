Kaapelitarrojen tulostaminen työmaalla voi olla hidasta ja melko puuduttavaa puuhaa, jos tunnukset naputellaan yksitellen tarratulostimeen. Tästä syntyi ajatus puhelin-/tablettisovelluksesta, jossa tietyn työvaiheen tarrat voidaan hakea listana ja lähettää tulostukseen yhdellä painalluksella.

Tavoitteena oli toteuttaa käytännön työmaatarpeeseen sopiva työkalu, jolla tarralistojen tulostaminen olisi nopeampaa ja vaivattomampaa kuin tunnusten naputtelu yksitellen tarratulostimen omalla käyttöliittymällä.

## Tarralistan haku ja tulostus

Alla olevassa demossa näkyy sovelluksen tyypillisin käyttötapaus omissa työtehtävissäni: oikea tarralista haetaan sovelluksesta, tulostus käynnistetään ja tulostuksen edetessä valmiita tarroja voidaan jo asettaa kaapeleiden merkintätaskuihin.

Käytännössä tulostuksen aloittaminen voi olla hyvin nopeaa. Usein riittää, että hakukenttään kirjoitetaan esimerkiksi listan tunnuksen loppunumerot ja painetaan tulostuspainiketta. Videolla työnkulku näytetään tavallista rauhallisemmin, jotta vaiheet ja sovelluksen ulkoasu erottuvat selvästi.

<div style="max-width:360px; margin: 1rem auto;">
  <iframe
    width="360"
    height="640"
    src="https://www.youtube.com/embed/owtXGNnSl0o"
    title="Automaattinen tarratulostus - listan haku ja tulostus"
    frameborder="0"
    allowfullscreen>
  </iframe>
</div>

## Sovelluksen toiminnot ja käyttöliittymä

Sovellus tukee tarralistojen tuontia, muokkausta ja tulostamista eri käyttötapoihin. Alla oleva video esittelee tarkemmin sovelluksen toimintoja ja käyttöliittymää:

[Video tähän tai upotus]

### Ominaisuudet

- **Tiedostojen tuonti ja uusien tarralistojen luonti:** tarratietoja voidaan tuoda sovellukseen valmiista tiedostoista (esim. JSON ja Excel).
- **Tarralistojen muokkaus:** yksittäisiä rivejä ja listoja voidaan muokata ennen tulostamista.
- **Nykyisen ja alkuperäisen datan vertailu:** käyttäjä voi nähdä, miten listan tiedot ovat muuttuneet alkuperäiseen tuontidataan verrattuna. Alkuperäiset tiedot voidaan tarvittaessa palauttaa joko yksittäiselle riville tai koko tarralistalle.
- **Filtterit:** tarralistojen näkyvyyttä sovelluksessa voidaan rajata listan tilan ja käyttäjän määrittämien tunnisteiden perusteella.
- **Tulostusasetukset:** tulostusasetuksissa voidaan muuttaa fonttia, fontin kokoa ja tarran pituutta sekä valita käytössä olevan tarranauhan leveys.
- **Eri tulostusmoodit:** sovellus tukee tavallista tarratulostusta, kaapelilippuja ja nauhatulostusta. Kaapelilipussa sama tunnus tulostetaan tarraan kahteen kertaan, jolloin tarra voidaan kiinnittää kaapeliin lipun tapaan. Nauhatulostuksessa useat tarrat tulostetaan yhtenä pidempänä nauhana, jolloin esimerkiksi saman listan tarrat saadaan yhteen tulosteeseen. Lisäksi sovelluksessa on tuki Nauhat numeroittain -tulostukselle, jossa tarrat jaetaan erillisille nauhoille tunnuksen viimeisen numeron perusteella. Tätä käsitellään tarkemmin myöhemmin.
- **Kytkentäkuvat:** käyttöliittymässä on jo tuki kytkentäkuvien näyttämiselle testidatan avulla. Varsinainen tuotantokäyttö vaatisi vielä tavan yhdistää oikeat kytkentäkuvat oikeisiin tarralistoihin. Yksi mahdollinen ratkaisu olisi projektikansion tuonti, jossa sovellus lukee samasta kansiosta tarralistat ja kytkentäkuvat sekä yhdistää ne tiedostonimien perusteella. Tämä olisi teknisesti melko suoraviivaista, jos tiedostot on nimetty saman tunnuksen, esimerkiksi position tai keskuksen tunnuksen, mukaan.

### Suunnitteluperiaatteet

Sovelluksen käyttöliittymässä on pyritty siihen, että ohjelman käyttö olisi mahdollisimman nopeaa ja vaivatonta. Tämän vuoksi yleisten toimintojen pitää olla helposti saatavilla. Esimerkiksi yläosan valikko voidaan pitää koko ajan auki, jolloin useita asetuksia voidaan muuttaa ilman jatkuvaa valikoissa liikkumista.

Nopeassa käyttöliittymässä on kuitenkin tärkeää miettiä myös virheistä palautumista. Jos toimintoja suojataan jatkuvilla varmistusikkunoilla, käyttö hidastuu. Jos varmistuksia taas vähennetään, käyttäjälle pitää tarjota hyvä tapa kumota vahingossa tehdyt muutokset.

Tästä syystä sovellukseen on kehitteillä undo- ja redo-toiminnot. Niiden avulla esimerkiksi vahingossa tehty poisto, muokkaus tai muu kosketusvirhe voitaisiin kumota ilman, että normaalia käyttöä tarvitsee hidastaa jatkuvilla varmistuksilla.


## Käytetyt teknologiat projektissa
- **Android / Kotlin:** sovellus on Kotlinilla toteutettu Android-sovellus, joka toimii Android-puhelimessa tai tabletissa. Sovellusta käytetään työmaalla tarralistojen tuontiin, muokkaamiseen ja tulostamiseen.
- **Brother PT-E720BT:** projektissa käytetty kannettava tarratulostin, jossa on Bluetooth-yhteys, akkukäyttö ja automaattinen leikkuri. Näiden ominaisuuksien ansiosta tulostinta voidaan käyttää työmaalla suoraan puhelimen tai tabletin kanssa ilman erillistä tietokonetta.
- **Brother SDK:** Brotherin tarjoama ohjelmistokirjasto, jonka avulla Android-sovellus voi ohjata tulostinta. SDK:n kautta sovellus voi muodostaa tulostustyön, määrittää tulostusasetuksia ja lähettää tulostettavan tarran tulostimelle ilman, että käyttäjän tarvitsee käyttää tarratulostimen omaa käyttöliittymää.

## Käytännön huomioita tulostuksesta

### Tarratulostimen valinta

Projektissa käytetty Brother-tarratulostin on toiminut hyvin omasta sovelluksesta kutsuttuna. Muiden valmistajien tulostimien osalta toimivuus riippuisi siitä, tarjoavatko ne vastaavan tavan ohjata tulostusta omasta ohjelmasta.

Käytännön kannalta automaattinen leikkaus on tärkeä ominaisuus. Jos käyttäjän täytyy itse katkaista jokainen tarra, osa työkalun tuomasta hyödystä menetetään.

### Tarralistojen muodostaminen

Jotta sovelluksesta saadaan oikeaa ajansäästöä, tarratietojen täytyy tulla jostain valmiista lähteestä. Tällainen lähde voi olla esimerkiksi johdotuslista, kytkentäkaavio, Excel-tiedosto tai muu projektidokumentti.

Käytännössä sovelluksen pitäisi pystyä tuomaan tällainen lähdedata ja muuntamaan se ohjelman ymmärtämäksi tarralistaksi mahdollisimman automaattisesti. Jos lähtödata on selkeässä muodossa, tämä voi onnistua suoraan Excel-tuonnilla tai muulla vastaavalla muunnoslogiikalla. Tällöin tarralistojen luonti on käyttäjän näkökulmasta helppoa ja vaivatonta.

Toinen mahdollinen suunta on tekoälyyn tai kuvantunnistukseen perustuva tarradatan poiminta esimerkiksi kytkentäkuvista.

### Milloin työkalusta on eniten hyötyä?

Suurin hyöty syntyy tilanteissa, joissa tarrojen alkuosat vaihtelevat paljon. Käsin tarratulostimella tulostettaessa tällaiset tunnukset täytyy naputella yksi kerrallaan, mikä tekee työstä hidasta ja virhealtista.

Sama ongelma korostuu myös silloin, kun samalla kertaa halutaan tulostaa useita pieniä tarralistoja. Tällöin tunnukset vaihtuvat luonnostaan listasta toiseen, ja käsin naputtelu muuttuu helposti katkonaiseksi työksi.

Sovelluksen kannalta tunnusten vaihtelu ei itsessään lisää työmäärää, jos tarratiedot saadaan tuotua ohjelmaan valmiina listana.

### Tarrojen ryhmittely käytännössä

Kun tarroja tulostetaan paljon, pelkkä tulostusnopeus ei ratkaise koko ongelmaa. Tärkeää on myös se, että tarrat saadaan jaettua sellaisiin eriin, joista oikea tarra löytyy nopeasti työmaalla. Jos kaikki tarrat päätyvät samaan kasaan, oikean tarran etsimiseen voi mennä turhaa aikaa.

Nauhatulostusta voidaan käyttää tarrojen pitämiseen erillään. Jos samalla kertaa tulostetaan usean eri tarralistan tarroja, jokainen lista voidaan tulostaa omana nauhanaan. Tällöin eri listojen tarrat eivät sekoitu keskenään. Samaa ajatusta voidaan hyödyntää myös yhden suuren tarralistan kanssa: iso lista voidaan jakaa pienempiin osiin esimerkiksi tunnuksen loppunumeron perusteella, jolloin oikeaa tarraa ei tarvitse etsiä yhdestä suuresta tarrajoukosta.

Sovelluksessa on tuki sille, että tarrat voidaan tulostaa loppunumeron mukaan järjestettynä. Lisäksi yksittäinen tarralista voidaan tulostaa useana erillisenä nauhana loppunumeron perusteella (**Nauhat numeroittain** -tulostus). Tällöin samasta tarralistasta syntyy erilliset nauhat tunnuksen viimeisen numeron mukaan. Esimerkiksi tunnukseen `3067` kuuluva tarra löytyy nauhasta `7`.

<p align="center">
  <a href="./assets/images/ordering_example.jpg">
    <img src="./assets/images/ordering_example.jpg"
         alt="Esimerkki tarrojen ryhmittelystä loppunumeron mukaan"
         style="width:250px; height:auto;">
  </a>
  <br>
  <em>Esimerkki tarrojen ryhmittelystä loppunumeron mukaan.</em>
</p>
