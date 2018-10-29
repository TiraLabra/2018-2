# Dokumentaatio

**Huom:** kaikki dokumentit palautetaan joko GitHubin tukemassa markdown-muodossa, katso tuetut formaatit [täältä](https://github.com/github/markup) tai .pdf-muodossa! Sijoita dokumentit omaan hakemistoonsa projektin juureen.
 
Koodin lisäksi tehtävänä on neljä dokumenttia: määrittelydokumentti, toteutusdokumentti, käyttöohje ja testausdokumentti. Dokumenttien merkitys kurssilla on kuitenkin vähäisempi; olennainen asia on toimiva ja tehokas koodi. 

Huomaa että jokaisen dokumentin pituus on n. 1-2 A4, poislukien kuvat ja taulukot (todellinen pituus voi olla siis jopa 3-4 sivua).

## Vaaditut dokumentit:
 
 
#### Määrittelydokumentti
* Mitä algoritmeja ja tietorakenteita toteutat työssäsi
* Mitä ongelmaa ratkaiset ja miksi valitsit kyseiset algoritmit/tietorakenteet
* Mitä syötteitä ohjelma saa ja miten näitä käytetään
* Tavoitteena olevat aika- ja tilavaativuudet (m.m. O-analyysit)
* Lähteet
 
#### Toteutusdokumentti
* Ohjelman yleisrakenne
* Saavutetut aika- ja tilavaativuudet (m.m. O-analyysit pseudokoodista)
* Suorituskyky- ja O-analyysivertailu (mikäli työ vertailupainotteinen)
* Työn mahdolliset puutteet ja parannusehdotukset
* Lähteet

#### Testausdokumentti
* Mitä on testattu, miten tämä tehtiin
* Minkälaisilla syötteillä testaus tehtiin (vertailupainotteisissa töissä tärkeää)
* Miten testit voidaan toistaa
* Ohjelman toiminnan empiirisen testauksen tulosten esittäminen graafisessa muodossa.
* Testaus on ideaalitapauksessa suoritettava ohjelma. Tällöin testi on helposti toistettavissa, mikä helpottaa toteutuksen tekoa jo varhaisessa vaiheessa. Javalla tehdyissä töissä on erittäin suositeltavaa käyttää testaukseen JUnitia.
 
#### Käyttöohje
* Miten ohjelma suoritetaan, miten eri toiminnallisuuksia käytetään
* Minkä muotoisia syötteitä ohjelma hyväksyy
* Missä hakemistossa on jar ja ajamiseen tarvittavat testitiedostot.
 

Työn tekemisessä ja arvostelussa painotetaan laitoksen muita harjoitustöitä vähemmän dokumentointia. Ohjelmakoodin on kuitenkin oltava mahdollisimman selkeää, metodien on oltava lyhyitä, luokkien, muuttujien ja metodien on oltava kuvaavasti nimettyjä ja ohjelman rakenteen muutenkin kaikin puolin selkeä.

Koodin tulee olla kirjoitettu mahdollisimman selkeästi ja ymmärrettävästi. Kommentoi koodiasi kattavasti, mutta napakasti. Jokainen luokka, metodi ja attribuutti ei välttämättä kaipaa kommenttia, mutta kaikki olennainen ja vähemmän kuin itsestään selvä on oltava selostettu kommenteissa. Sisällytä metodien kommentteihin niiden parametrien ja paluuarvon merkitykset. Metodien sisäinen kommentointi ei ideaalitapauksessa pitäisi olla tarpeen, sillä metodien tulee olla kuvaavasti nimettyjä, kompakteja ja yksinkertaisia, helposti hahmotettavia kokonaisuuksia. Mikäli metodin toimintaa kuitenkin on vaikea hahmottaa pelkän koodin ja metodin yleiskommentin perusteella, voidaan sen koodia kommentoida sisäisestikin.
 
JavaDoc-kommentointia käytetään kaikissa töissä, jotka toteutetaan Javalla. NetBeans toteuttaa pyydettäessä luokille ja metodeille JavaDoc-kommenttien pohjat. Mikäli teet työsi jollakin muulla kielellä, sovi käytetystä kommentoitityylistä ohjaajan kanssa. Luokkakaaviot saat lisättyä JavaDoc:iisi suoraan käyttämällä YWorks-nimistä työkalua, joka generoi suoraan NetBeans-projektista kaaviot.