# Automaattinen tarratulostus kaapelimerkintöihin

Kaapelitarrojen tulostaminen työmaalla voi olla hidasta, jos tunnukset naputellaan yksitellen tarratulostimeen. Projektin tavoitteena oli nopeuttaa tätä työvaihetta tuomalla valmiit tarralistat sovellukseen, tarkistamalla ja muokkaamalla niitä tarvittaessa sekä tulostamalla tarrat suoraan Android-puhelimesta Brother-tarratulostimelle Bluetoothin kautta.

Tavoitteena oli tehdä käytännön työmaatarpeeseen sopiva työkalu, joka vähentää käsin tehtävää naputtelua ja tekee tarralistojen käsittelystä selkeämpää.

## Päädemo: valmis lista tulostukseen

Alla olevassa demossa näkyy tyypillisin käyttötapaus:
- valmis tarralista avataan sovelluksessa
- tarvittavat rivit tarkistetaan
- tarrat tulostetaan Brother-tarratulostimella

[Video tähän tai upotus]

## Ohjelman yleisesittely

Sovellus tukee tarralistojen tuontia, muokkausta ja tulostamista eri käyttötapoihin. Alla oleva video esittelee tarkemmin sovelluksen toimintoja:

- tiedostojen tuonti ja uusien listojen luonti
- tarralistojen muokkaus
- nykyisen ja alkuperäisen datan vertailu
- eri tulostusmoodit, kuten lippu- ja nauhatulostus
- tulostusasetukset
- filttereiden käyttö

[Video tähän tai upotus]

## Käytetyt teknologiat projektissa

- **Android:** sovellus toimii Android-puhelimessa ja sitä käytetään työmaalla tarralistojen käsittelyyn ja tulostamiseen.
- **Brother PT-E720BT:** Bluetooth-tarratulostin, jolle sovellus lähettää tulostettavat tarrat.
- **Brother SDK:** käytössä tulostimen ohjaamiseen Android-sovelluksesta.
- **Bluetooth:** puhelimen ja tarratulostimen välinen tiedonsiirto.
- **Excel / JSON:** tarralistojen tietomuodot. Sovellus voi käsitellä valmiita listoja ja muodostaa niistä tulostettavia tarroja.
- **Android Canvas / Bitmap:** tarrojen ulkoasu muodostetaan kuvana ennen tulostusta.
- **AI / PC-prototyyppi:** projektin aikaisemmassa PC-versiossa testattiin tarralistojen muodostamista tekoälyn avulla esimerkiksi kuvista tai dokumenteista.

## Toteutus lyhyesti

### 1) Tarralistojen tuonti

Tarralista voidaan tuoda sovellukseen valmiista tiedostosta. Tavoitteena on, että työmaalla käytettävä data voidaan siirtää sovellukseen ilman, että tarroja tarvitsee kirjoittaa yksitellen tarratulostimen omalla käyttöliittymällä.

### 2) Listojen tarkistus ja muokkaus

Sovelluksessa käyttäjä voi tarkistaa tarrarivit ennen tulostusta. Lisäksi sovellus voi näyttää eron alkuperäisen datan ja muokatun datan välillä, jolloin automaattiset korjaukset tai käsin tehdyt muutokset ovat helpommin havaittavissa.

### 3) Tulostusmoodit

Sovelluksessa on eri tulostustapoja eri käyttötarpeisiin. Esimerkiksi kaapeleille voidaan tulostaa lippumaisia tarroja, joissa sama tunnus tulostuu kahteen kertaan, tai tavallisia nauhatarroja.

### 4) Tulostus Brother-tarratulostimelle

Tulostus tapahtuu Android-puhelimesta Bluetoothin yli Brother PT-E720BT -tarratulostimelle. Sovellus muodostaa tulostettavan tarran kuvatiedoksi ja lähettää sen tulostimelle Brother SDK:n avulla.

## Tulokset

Projektissa saatiin toimiva Android-sovellus, jolla voidaan:
- tuoda ja käsitellä tarralistoja
- tarkistaa ja muokata yksittäisiä rivejä
- tulostaa tarroja suoraan puhelimesta Bluetoothin yli
- käyttää eri tulostusmuotoja kaapelimerkintöihin

[kuvakaappaus sovelluksesta]

[kuva tulostetuista tarroista]

## Mahdolliset seuraavat käyttötapaukset

Projektissa on useita mahdollisia jatkokehityssuuntia:

- **AI:lla luodut tarralistat kytkentäkuvista:** PC-prototyypissä on jo testattu tarradatan muodostamista tekoälyn avulla.
- **Kytkentäkuvien yhdistäminen tarralistoihin:** sovellus voisi yhdistää tarralistat, johdotuskaaviot ja kytkentäkuvat puoliautomaattisesti.
- **Punakynäkuvien tallennus:** sovellukseen voisi tallentaa kuvia työmaalla tehdyistä punakynämerkinnöistä.
- **Kytkentäkuvien kevyt muokkaus:** sovellus voisi tukea yksinkertaisia merkintöjä tai korjauksia suoraan kytkentäkuviin.
- **Paremmat filtterit ja hakutoiminnot:** tarralistoja voisi suodattaa esimerkiksi tilan, dokumentin, position tai tulostustilan mukaan.

## Testaus ja vianrajaus

- **Bluetooth-yhteys:** varmistin, että Android-sovellus löytää Brother-tarratulostimen ja saa siihen yhteyden.
- **Brother SDK:** testasin SDK:n alustuksen, tulostimen tunnistamisen ja yksittäisen testitarran tulostuksen.
- **Tarran kuvanmuodostus:** testasin eri fonttikokoja, rivivälejä ja tarran mittoja, jotta tulosteesta tuli luettava.
- **Kaksirivinen kaapelitarra:** testasin tulostusta muodossa, jossa kaapelitunnus ja kaapelityyppi tulostuvat omille riveilleen.
- **Käytännön työmaatesti:** sovellusta ja tulostinta testattiin oikeassa käyttötapauksessa työmaalla.
