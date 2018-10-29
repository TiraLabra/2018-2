# Git ohje

Git on laajalti käytetty versionhallinnan työkalu, jota tarvitset esimerkiksi harjoitustöitä tehdessäsi. Versionhallinnan avulla tiedostoihin tekemäsi muutokset ovat aina tallessa, ja voit palata edelliseen versioon, jos jokin menee pieleen.

Verkossa on paljon loistavaa, paremmin kuvitettua ja jopa videoilla varustettua kunnollista materiaalia gitin käytöstä. Suosittelemme ennemmin tutustumaan siihen, mikäli englanninkielinen materiaali ei tuota liikaa vaikeuksia.

Alkuun pääsee hyvin seuraamalla GitHubin ohjetta [TryGit](http://try.github.io/) .

Suosittelemme myös lukemaan:

[Aloita lukemalla GitHubin ohje gitin käytöstä](https://help.github.com/articles/set-up-git)

[Repon luominen githubiin](https://help.github.com/articles/create-a-repo)

[Repositorion forkkaaminen](https://help.github.com/articles/fork-a-repo)

[Kattavan ohjeen kaikkeen](http://git-scm.com/documentation)

Näiden jälkeen voi alla olevaa ohjettakin vilkaista, mutta siinä ei oikeastaan ole enää mitään uutta gitistä. 

## Yksityiskohtainen “kädestä pitäen” -ohje Gitin käyttöön
Alkuperäinen ohje: Mika Huttunen ja Silja Polvi

### Aloittaminen

*ÄLÄ* käytä Netbeansin tarjoamaa Git-lisäosaa *ÄLÄKÄ* graafisia ohjelmia. Tähän asti kaikki kurssilla päivän koodaustyönsä menettäneiden ongelmat ovat johtuneet näistä. Käytä aina Linuxissa/OSX:ssä terminaalia tai Windowsissa Git Bashia, ja tee Commitit sekä Pushit käsin.

1.  Jos et ole koulun koneella ja koneessasi ei ole valmiiksi Gitiä, voit ladata sen täältä: [http://help.github.com/win-set-up-git/](http://help.github.com/win-set-up-git/). Ohje on Windowsille, mutta sen alussa on linkit myös muita käyttöjärjestelmiä varten.
2.  Mene osoitteeseen [Github.com/plans](www.Github.com/plans)
3.  Paina oikealla ylhäällä olevaa nappia “Create a free account”
4.  Täytä vaadittavat neljä kenttää ja klikkaa “Create an account”
5.  Paina oikealla olevaa harmaata nappia “New repository”
6.  Laita repositorion nimeksi esimerkiksi "HarjoitusRepo", harjoitustyösi aihe tai oma nimiehdotuksesi ohjelmalle
** Valitse pallura “Public”
** Valitse ruutu “Initialize this repository with a README”
7. Klikkaa lopuksi “Create repository”.

### SSH-avaimen luominen omalla koneella

Katso ohje [tästä](https://help.github.com/articles/generating-ssh-keys). Mikäli latasit Gitin yllä olevan linkin takaa Githubin sivuilta, käytä komentorivinä Git Bashia!

### SSH-avaimen luominen laitoksen koneella

*Huomaa:* Laitoksen sivuilla on tähänkin vähän lyhyemmät [ohjeet](http://www.cs.helsinki.fi/group/kuje/compfac/ssh_avain.html).
SSH-avaimen luominen ei ole pakollista, mutta helpottaa versionhallinnan käyttöä. Toisinaan joillakin henkilöillä Github on evännyt yhteydenotot ilman SSH-avaimen luomista.

1.  Avaa komentorivi (Konsole tai Terminal)
2.  Anna komento _ssh-keygen_
3.  Ohjelma kysyy, mihin tiedostoon avain tallennetaan. Oletus on hyvä, joten hyväksy painamalla _enter_.
4.  Ohjelma pyytää asettamaan salasanan avaimellesi. Anna salasana, jonka varmasti muistat. Salasana on pakollinen, muuten laitoksen ylläpito poistaa ssh-avaimesi.
5.  Aseta ssh-hakemiston oikeudet antamalla ensin komento _chmod u=rwx,go= .ssh_ ja antamalla seuraavaksi komento _chmod u=rwx,go= .ssh/*_
6.  Lisää avaimen julkinen pari Githubiin: anna ensin komento _less .ssh/id_rsa.pub_ tai _gedit .ssh/id_rsa.pub_ niin pääset tarkastelemaan tiedostoa
7.  Kopioi koko tiedoston sisältö (eli teksti)
8.  Avaa nettiselaimella Github ja kirjaudu sisään (jos et jo ole kirjautuneena)
9.  Paina oikeassa yläkulmassa olevaa jakoavaimen ja ruuvimeisselin kuvaa (“Account Settings”)
10.  Klikkaa vasemmalta “SSH Keys” ja sitten oikealta nappia “Add SSH key”
11.  Anna nimeksi (Title) vaikka “Laitoksen avain” ja liitä Key-kenttään kohdassa 10 kopioimasi teksti. Poista tekstin seasta mahdolliset rivinvaihdot ja välilyönnit, jotta avaimesi sekaan ei jää “white spaceja”. Paina lopuksi nappia “Add key”.
12.  Anna confirm-kentälle Githubin salasanasi
13.  Avaimesi on nyt lisätty Githubiin!

*HUOM.* Joudut tekemään tämän jokaisella koneella, josta haluat käyttää Githubia. Laitoksella riittää, että ssh-avaimen luomisen tekee kerran yhdellä koneella.

### Repositorion valmisteleminen käyttöä varten

*HUOMAA:* Tässä ohjeessa komentorivillä tarkoitetaan Linuxilla terminaalia ja Windowsin tapauksessa Git Bashia! Windowsin omat komentorivit eivät tunnista git-alkuisia komentoja, mikäli otit Gitin käyttöön yllä olevan linkin takana olevan Windows-ohjeen mukaan. Käytä Git Bashia.

1.  Hankkiudu Githubin sivulla luomasi repositorion näkymään. Sinne pääsee vaikkapa etusivulta kun olet kirjautunut, klikkaamalla repositorion nimeä.
2.  Kopioi melko ylhäällä olevassa kentässä oleva osoite, joka on suunnilleen muotoa _git@github.com:käyttäjätunnuksesi/HarjoitusRepo.git_
3.  Avaa komentorivi ja anna komento tyyliin _git clone git@github.com:käyttäjätunnuksesi/HarjoitusRepo.git_
4.  Seuraavaksi ohjelma pyytää vahvistamaan äskeisen komennon (yes/no) - vastaa yes
** Jos git push sanoo “Permission denied (publickey)”, kokeile ssh-avaimen generointia uudestaan tai komentoa ssh-add
5.  Mene komentorivillä äsken kloonaamaasi kansioon (esim. HarjoitusRepo) komennolla _cd HarjoitusRepo_ tms. Kaikki tiedostot voit listata komennolla _ls_.
6.  Komennon _cd HarjoitusRepo_ jälkeen olet kansiossa, johon tulet tallentamaan projektisi. Nyt komennolla _ls_ tulisi näkyä tiedosto README.

### Pieni repotreeni

1.  Varmista, että olet komentorivillä repositoriokansiossasi (esim. HarjoitusRepo)
2.  Avaa README-tiedosto vaikkapa komennolla _notepad README.md_ (Windowsissa), _nano README_(koulun koneella), tai ihan millä tekstieditorilla haluat
3.  Tiedoston pitäisi aueta valitsemassasi editorissa. Kirjoita tiedostoon jotakin ja tallenna se. Nanossa tallenna tiedosto painamalla _Ctrl + o_, ja vahvista tallennus painamalla _enter_.
4.  Anna komentorivillä komento _git status_. Nyt näet luettelon tiedostoista, joita olet muokannut (modified), tässä tapauksessa README-tiedosto.
5.  Anna komento git commit -am “eka muokkaus”. Jos viesti (tässä eka muokkaus) unohtuu, avautuu editori. Poistu editorista komennolla :q. Anna antamasi commit-komento uudelleen, tällä kertaa viestin kera.
6.  Nyt tekemäsi muokkaukset (README-tiedoston muokkaus) ovat paikallisessa repositoriossasi. Sieltä ne pitää vielä työntää verkossa olevaan Githubin repoosi komennolla _git push_.
** Jos git push sanoo "Permission denied (publickey)", kokeile ssh-avaimen generointia uudestaan tai komentoa _ssh-add_
7.  Mene Githubin sivulla olevaan repositoriosi näkymään (kuten edellisen ohjeen kohdassa 1) ja päivitä näkymä. Huomaat, että README-tiedostoon tekemäsi muokkaukset ovat nyt Githubissa asti, antamasi viestin kera!

### Toinen repotreeni

1.  Hankkiudu komentorivillä repositorion kansioosi (esim. HarjoitusRepo). Anna komento _mkdir testikansio_ luodaksesi uuden kansion. 
2.  Lisää testikansioosi jokin tiedosto: etsi tietokoneeltasi luomasi kansio ja luo tai siirrä sinne vaikkapa tekstitiedosto.
3.  Lisää luomasi kansio versionhallinnoitavaksi antamalla komentoriville komento _git add testikansio_. Nyt versionhallinta seuraa kansiotasi siinä mielessä, että se näkyy status-komennolla, ja sen voi siirtää paikalliseen versionhallintaan (commit). Huomaa, että typötyhjä kansio ei tule hallinnoitavaksi add-komennolla.
4.  Anna commit-komento (_git commit -m “uusi testitiedosto ja -kansio lisatty”_).
5.  Anna push-komento (_git push_). Tarkista Githubin nettisivulta, että uusi kansiosi ja sen sisältämä tiedosto ilmestyvät repositorionäkymääsi.

*Huom:* Jos haluat lisätä useita tiedostoja kerralla, se onnistuu komennolla _git add ._

Nyt osaat lisätä Githubiin tiedostoja ja kansioita: add - commit - push! Tee samaan malliin harjoitustyöllesi dokumentaatiokansio ja sinne ensimmäisellä viikolla tarvittava dokumentointi.

### Kolmas repotreeni: pull

Jos työskentelet useammalla kuin yhdellä koneella, voit versionhallinnan avulla pitää projektin ajan tasalla ilman että joudut siirtämään tiedostoja koneelta toiselle esimerkiksi muistitikulla. Sehän on yksi versionhallinnan hyödyistä! Tässä harjoituksessa pääset harjoittelemaan tiedostojen kopioimista Githubista koneellesi toisen repositoriokloonikansion avulla. Todellisessa tilanteessa harjoituksessa luotava toinen kloonikansio vastaa eri koneella olevaa kloonikansiota. Et siis tarvitse toista kloonia (varjorepo) muuhun kuin tähän harjoitukseen.

1.  Luo uudella nimellä (esim. varjorepo) toinen klooni repositoriosta antamalla komentorivillä komento tyyliin _git clone git@github.com:käyttäjätunnuksesi/HarjoitusRepo.git varjorepo_. Klooni luodaan siis muuten kuten kohdassa “Repositorion valmistelu käyttöä varten”, paitsi että nyt kloonikansio nimetään itse.
2.  Muokkaa alkuperäisessä repossa (esim. HarjoitusRepo) olevaa tiedostoa README. Anna add-komento, commit-komento ja push-komento alkuperäisessä repositoriokloonikansiossasi (HarjoitusRepo), jotta äsken tehty muutos päätyy Githubiin asti.
3.  Mene tämän harjoituksen alussa luomaasi varjorepoon. Avaa nyt README-tiedosto tässä uudessa repossa, jolloin huomaat että se ei ole muuttunut.
4.  Vedä alkuperäisessä kansiossasi (HarjoitusRepo) tekemäsi muutokset varjorepoon Githubista komennolla _git pull_. Huomaat, että README-tiedosto päivittyy niiden muutosten mukaan, jotka teit alkuperäisessä kloonissa (HarjoitusRepo)! Tarkista tämä vielä varjorepossa olevasta README-tiedostosta.

### Git & Netbeans

Git ja Netbeans ovat hyviä kavereita. Käytä Netbeans-projektin tallennuspaikkana koneellasi olevaa repositoriokloonikansiota: aseta Netbeansissa kohtaan “Project Location” koneella oleva repositorion kansio (esim. HarjoitusRepo). Nyt tallennat projektiasi koko ajan repositorion kansioon.
1.  Anna (kun olet ensin siirtynyt komentorivillä repositoriokansioosi) komentoriville komento _git status_. Huomaat kaksi uutta tiedostoa: harjoitustyösi lisäksi tiedoston .gitignore. Viimeksi mainittu on Netbeansin luoma tiedosto, joka antaa listan versionhallintaan kuulumattomista tiedostoista. Se pitää lisätä versionhallinnoitavaksi. Tiedostosta ei tarvitse ymmärtää enempää, mutta jos haluat tai tiedosto ei generoitunut automaattisesti, lue tämän dokumentin lopusta lyhyt .gitignore selite.
2.  Anna komento _git add harkkatyöprojektisiNimi_ ja sen jälkeen komento _git add .gitignore_.
3.  Nyt komennon git status pitäisi näyttää sekä harkkatyöprojektisi sisältöineen että .gitignore
Anna commit-komento ja push-komento. Nyt harjoitustyösi löytyy Githubistasi!

Nyt voit aloittaa harjoitustyösi tekemisen. 

### Nyrkkisäännöt

* Uudella koneella aloittaessasi luo ssh-avain ja kloonaa (clone) haluamasi repositorio koneelle
* Työskentelyn aluksi vedä (pull) Githubista projektisi
* Tehdessäsi muutoksia, lisää (add) uudet tiedostot ja muutetut tiedostot, sekä tee commit kuvaavalla kommentilla.
* Add + Commit yhdistelmää voit ajatella työn tallentamisena.
** Tee mieluummin liikaa kuin liian vähän committeja
** git status komennolla voit kysellä mitä olet muuttanut ja mitä olet commitoimassa
** Ongelmatilanteissa on mahdollista palata vanhaan committiin, vaikka viikon takaa!
* Viimeistään lopettaessasi työskentelyn työnnä (push) muutoksesi Githubiin.
* Tarkista selaimesta, että KAIKKI muutokset menivät repositorioosi: Muuten ohjaajat eivät niitä näe
* Repositorio on myös varmuuskopio työstäsi - jos tietokoneesi hajoaa tai laitoksen palvelimet reistailevat, on kaikki vaivalla tekemäsi työ tallessa Githubissa!
* Tiedoston poistaminen repositoriosta tehdään git rm tiedostonnimi komennon avulla. HUOM ole huolellinen tämän käytössä, sillä komento poistaa tiedoston myös paikallisesta repositoriosta (siis omalta koneeltasi)
* MUISTA: Github-repositoriosi on julkinen. Sen näkee koko maailma. ÄLÄ pistä sinne esimerkiksi opiskelijanumerosi.

Nyt voit jatkaa harjoitustyötäsi miltä tahansa tietokoneelta aina siitä mihin lopetit edellisellä kerralla.

### Lyhyt .gitignore -ohje

.gitignore on tiedosto, joka sisältää tiedon niistä tiedostoista ja kansioista, joita ei haluta versionhallintaan eikä Githubiin. Nämä esitetään sääntöinä, jokainen sääntö omalla rivillään. Yleensä nämä tiedostot ovat kehitysympäristöjen joka ajokerralla generoitavia tai arkaluontoista tietoa sisältäviä tiedostoja, joita ei haluta versionhallintaan viemään tilaa tai kaikkien nähtäville. *.gitignore tiedosto itsessään halutaan Githubiin.*

Netbeans luo .gitignore -tiedoston automaattisesti, kun Netbeans-projektin luo kansioon, joka on repositorio. Netbeans lisää sinne säännön _/projektikansiosi_nimi/nbproject/private/_, joka estää versionhallintaan menemästä tiedostoja, jotka Netbeans luo aina kun käännät ja ajat ohjelmasi. _git status_ komento ei siis huomaa lainkaan, vaikka private/ -kansion sisällä tapahtuu muutoksia.

Jos Netbeans jostain syystä ei tehnyt tällaista tiedostoa, voit luoda sen itse.
1.  Tee tekstitiedosto, jolle annat nimeksi ".gitignore"
** Tiedostolla ei ole tiedostopäätettä
2.  Lisää tekstitiedostoon rivi _/projektikansiosi_nimi/nbproject/private/_
3.  Lisää myös rivi _/projektikansiosi_nimi/nbproject/dist/_

Vastaavasti .gitignore-tiedostoon voi lisätä omia sääntöjä. Jokainen sääntö tulee omalle rivilleen. 

Säännöistä löytää lisää esimerkkejä osoitteissa:

[http://git-scm.com/docs/gitignore](http://git-scm.com/docs/gitignore)

[https://help.github.com/articles/ignoring-files](https://help.github.com/articles/ignoring-files)

[http://cfmumbojumbo.com/cf/index.cfm/coding/git-giving-files-the-cold-shoulder-gitignore/](http://cfmumbojumbo.com/cf/index.cfm/coding/git-giving-files-the-cold-shoulder-gitignore/)