# Aiheet

Aiheen voi keksiä itse, tai valita alla olevasta listasta itselleen mielenkiintoinen aihe. Listalla olevat aiheet ovat vain ehdotuksia, niitä voi muokata ja kehittää - lopullinen aihe sovitaan yhdessä ohjaajan kanssa. Aiheita voi katsoa myös kurssin aiemman version [sivuilta](https://github.com/TiraLabra/2017-loppukesa/wiki/Aiheita).

## Verkot ja polunesintä

* Miten löydetään tehokkaasti nopein/lyhin reitti labyrintistä ulos. Labyrintti voi olla tehty esimerksi ascii-merkeistä tai piirretty kuva.

* Miten löydetään tehokkaasti nopein/lyhin reitti verkossa kahden pisteen välillä. Verkon pisteet voivat olla esimerkiksi katuosoitteita, joukkoliikenteen pysäkkejä tai koordinaatteja. Hyvä artikkeli aiheesta: http://theory.stanford.edu/~amitp/GameProgramming/AStarComparison.html
* huom: pelkkä A-star ei riitä aiheeksi, vaan esim. vähintään kahden eri reitinhakualgoritmin vertailu.

* Karttoja reitinhakutöihin löytyy esimerkiksi [Moving AI Lab](http://www.movingai.com/benchmarks/):in sivuilta tai maanminttauslaitoksen karttojen [lataus](http://kartat.kapsi.fi/) sivustolta.

## Tiedon tiivistys

* Tiedosto tulisi saada mahtumaan pienempään tilaan, miten tämä onnistuu? Toivottava lopullinen koko on 40-60% alkuperäisestä koosta. Tiedosto pitää myös pystyä avaamaan alkuperäiseen muotoon myöhemmin. Kuinka hyvin ohjelma suoriutuu suhteessa olemassa oleviin ohjelmiin.
    * Huffman
    * Lempel Ziv

## Tekoälyt

* Shakki, go, laajennettu risti-nolla jne  ovat hauskoja ja haastavia pelejä. Niitä olisi kiva pelata tietokonetta vastaan, tehtävänäsi on kehittää valitsemallesi pelille tekoäly. Tekoälyn pitää pystyä pelaamaan niin ihmistä kuin itseään vastaan.

* Kivi-sakset-paperi on kaikille tuttu peli. Onnistutko toteuttamaan tekoälyn, joka päihittää ohjaajan? Kun tekoälysi on hyvä voit jatkaa kehitystä ottamalla mukaan vielä kaksi vaihtoehtoa: Lisko ja Spock. http://upload.wikimedia.org/wikipedia/commons/a/ad/Pierre_ciseaux_feuille_l%C3%A9zard_spock_aligned.svg sekä http://www.youtube.com/watch?v=x5Q6-wMx-K8

* 15-pelin ratkaisija. Kaikille tuttu 15-peli voi olla haastava ratkaistava. Saatko kehitettyä ohjelman joka ratkaisee pelin kuin pelin? http://en.m.wikipedia.org/wiki/15_puzzle

* [halite](https://halite.io/) tekoäly. Tai muu internetistä löytyvä tekoälyhaaste.

## Luolastogeneraattori
* Suosituksi noussut aihe on esimerkiksi rogue-peleissä käytettävien luolien generointi. Tähän on tarjolla valmiita algoritmejä joita voi toteuttaa, mutta oma toteutus on myös täysin mahdollinen. Luolaston generointi voi joko olla etukäteen tapahtuva tai dynaamisesti pelin aikana kehittyvä pelaajan liikkumisen mukaan.


## Tietorakennevertailut
Tietorakenteita on monenlaisia, mikä olisi paras kuhunkin ongelmaan? Vertaile neljää eri tietorakennetta (esimerkiksi puita tai kekoja), joita ei ole käsitelty Tietorakenteet ja algoritmit -kurssilla. Tutki missä tilanteessa kukin on paras, eli missä tilanteessa käyttäisit kutakin rakennetta.


## Salaus ja Tietoturva
* Tietoturva on tänä päivänä tärkeämpää kuin koskaan monien toimintojemme siirryttyä verkkoon. Salausta voi tehdä monilla eri tavoin ja moniin käyttötarkoituksiin, oheinen sivusta tarjoaa paljon kokeiltavaa aiheesta: http://rumkin.com/tools/cipher/index.php

* Salauksia ja tiivistyksiä voi myös purkaa. Ylläolevan linkin kautta löydät paljon ideoita - voit myös ryhtyä tutkimaan esimerkiksi merkkein frekvenssejä ja analysoida sitä kautta salattua tiedostoa. Tämä liittyy läheisesti myös Huffmann-tiivistettyyn dataan: http://rumkin.com/tools/cipher/frequency.php


## Signaalinkäsittely (kuva, ääni)
Toteuta yksi (tai useampi, riippuen vaativuudesta) signaalinkäsittelyalgoritmi ja raportoi tuloksista. Useat signaalinkäsittelyn algoritmit hyödyntävät matriisilaskentaa ja lineaarialgebraa, joten niiden tunteminen on hyödyksi.

### Muuta kivaa
* Rahtifirma NopsaToimitus haluaa optimoida konttikuljetuksissa käytettävän tilan. Suunnittele miten voidaan täyttää yksi tai useampi kontti mahdollisimman tehokkaasti, jos tiedetään pakettien määrä ja koot. Ideaa voi hakea kuutiopalapelin ratkaisijasta.

* Suunnittele säännöllisten lauseiden tulkki. Miksi? Loistava vastaus: http://blog.stevenlevithan.com/archives/10-reasons-to-learn-and-use-regular-expressions
