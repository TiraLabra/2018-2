# Maven ja Gradle

Alla Mahdollisimman yksinkertaistettu tapa saada pystyyn java gradle tai maven projekti. Jos tiedät jo mitä teet ja sinulla on tapa jota mielummin käytät, niin voit vapaasti sivuuttaa tämän ohjeen.

[Maven](https://en.wikipedia.org/wiki/Apache_Maven) ja [Gradle](https://en.wikipedia.org/wiki/Gradle) on javalle tehtyjä [Build automation](https://en.wikipedia.org/wiki/Build_automation) -työkaluja. Molemmat helpottavat esimerkiksi testikattavuusraporttien tekemistä tai jarin rakentamista. 

### 1. Luo Projektin repostorio

Käytettäessä netbeanssia on yleensä näpprä luoda ensin repositorio johon projekti luodaan koska netbeans osaa usein päivittää automaattisesti ```.gitignore``` tiedostoa kun projektin kehittyy.

![Git projekti](http://saskeli.kapsi.fi/create.png)

Kannataa ainakin ruksia "Initialize repository with README.md" että voi projektin kloonata heti luonnin jälkeen.

### 2. Kloonaa repositorio

Kopioi repostiroion linkki

![clone](http://saskeli.kapsi.fi/clone.png)

Aja ```git clone <linkki repoon>```

### [vain GRADLE] 3a. Luo netbeansilla gradle projekti

Tarkasta ```Tools -> Plugins``` takaa valikosta että neatbeansiin on asennettu gradle tuki.

![plugin](http://saskeli.kapsi.fi/gradle_plugin.png)

Jos tukea ei ole asennettu niin asenna se "available plugins välilehdeltä".

Luo normaalisti uusi projekti netbeansilla mutta valitse asetuksista ```Gradle -> Sinlge Gradle Project```.

![gradle create](http://saskeli.kapsi.fi/gradle_create1.png)

Aseta projektin sijainniksi kloonaamasi repo.

![location](http://saskeli.kapsi.fi/gradle_create2.png)

Lisää `build.gradle` tiedostoon ainakin seuraavat rivit. Tiedosto kannattaa muutenkin pitää ajantasalla. (Lisää rivit oikeaan kohtaan tiedostoa. Tiedostossa valmiiksi olevat rivit kyllä kertoo paikat)

```
apply plugin: 'jacoco'

jacocoTestReport {
    reports {
        xml.enabled = true
        html.enabled = true
    }
}

check.dependsOn jacocoTestReport

```

### [vain MAVEN] 3b Luo netbeansilla Maven projekti

Projekti luodaan normaalisti NetBeansin **New Project**-nappulasta. Nyt kuitenkin ei valita kategoriaa **Java**, vaan hieman alempaa etsitään kohta **Maven**. Oikeasta valikosta voidaan nyt valita **Java Application**. 

![create maven](http://saskeli.kapsi.fi/mvn_create.png)

Sivulla **Name and Location** kannattaa antaa ohjelmalle hyvä ja kuvaava nimi. Aseta **Project Location**:ksi Git-repositoriosi polku (omalle koneellesi luotu repositoriokansio, josta pushit ja commitit tehdään). Myös **Group id** täytyy vaihtaa ohjelman nimen mukaiseksi tai ainakin joksikin muuksi kuin _com.mycompany.enterprising.domain_ , ja se pitää kirjoittaa **pienillä kirjaimilla**. Tämä on tärkeää mutaatiotestauksen toiminnan kannalta. GroupId muuttaa ohjelman vakiopakkauksen nimen.

![location](http://saskeli.kapsi.fi/loc.png)

Maven ei eroa "normaalista" Java-projektista kovinkaan paljoa. Suurin ero on pom.xml-tiedosto joka kuvaa xml:nä projektin riippuvuudet eri kirjastoista. Lisäämme sinne valmiiksi muutaman testausta auttavan kirjaston.

Nyt projektisi pom.xml:n pitäisi näyttää jotakuinkin seuraavalta:
``` xml
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
    <modelVersion>4.0.0</modelVersion>
    <groupId>superohjelma</groupId>
    <artifactId>SuperOhjelma</artifactId>
    <version>0.1.0</version>
    <packaging>jar</packaging>
    <properties>
        <project.build.sourceEncoding>UTF-8</project.build.sourceEncoding>
        <maven.compiler.source>1.8</maven.compiler.source>
        <maven.compiler.target>1.8</maven.compiler.target>
    </properties>

    <!-- Lisättävä osa tähän väliin-->

</project>
```

Tämän xml:n alkuosa on jokaisella projektille yksilöllinen. Siihen emme koske. Sen sijaan haluamme lisätä muuutaman riippuvuuden ja pluginin projektiin. Lisätään `</properties>`-tagin ja `</project>`-tagin väliin osa:
``` xml
<dependencies>
    <dependency>
        <groupId>junit</groupId>
        <artifactId>junit</artifactId>
        <version>4.12</version>
        <scope>test</scope>
    </dependency>
</dependencies>

<build>
    <plugins>
        <plugin>
            <artifactId>maven-compiler-plugin</artifactId>
            <configuration>
                <source>1.8</source>
                <target>1.8</target>
            </configuration>
            <version>3.3</version>
        </plugin>
        <plugin>
            <groupId>org.pitest</groupId>
            <artifactId>pitest-maven</artifactId>
            <version>1.1.8</version>
        </plugin>
    </plugins>
</build>
```

Lisäyksen jälkeen pom.xml pitäisi näyttää jotakuinkin tältä:

``` xml
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
    <modelVersion>4.0.0</modelVersion>
    <groupId>superohjelma</groupId>
    <artifactId>SuperOhjelma</artifactId>
    <version>1.0-SNAPSHOT</version>
    <packaging>jar</packaging>
    <properties>
        <project.build.sourceEncoding>UTF-8</project.build.sourceEncoding>
        <maven.compiler.source>1.8</maven.compiler.source>
        <maven.compiler.target>1.8</maven.compiler.target>
    </properties>

    <dependencies>
        <dependency>
            <groupId>junit</groupId>
            <artifactId>junit</artifactId>
            <version>4.12</version>
            <scope>test</scope>
        </dependency>
    </dependencies>

    <build>
        <plugins>
            <plugin>
                <artifactId>maven-compiler-plugin</artifactId>
                <configuration>
                    <source>1.8</source>
                    <target>1.8</target>
                </configuration>
                <version>3.3</version>
            </plugin>
            <plugin>
                <groupId>org.pitest</groupId>
                <artifactId>pitest-maven</artifactId>
                <version>1.1.8</version>
            </plugin>
        </plugins>
    </build>

</project>
```

Tämän jälkeen projektille voi tehdä mutaatiotestausraportteja, joista käy ilmi myös rivikattavuus. Tehdään vielä näiden generoimisesta hieman helpompaa.

Lisää projektiin uusi tiedosto **New File...**-näppäimellä. Valitse **XML -> XML Document** ja anna sille nimeksi **nbactions**. Siirry seuraavan ikkunaan ja valitse **Well-formed Document**. Paina Finish. Nyt projektissa pitäisi olla uusi _nbactions.xml_-tiedosto. Jos se ei ole Project Files-kansiossa, siirrä se sinne.

Avaa tiedosto ja korvaa sen sisältö tällä:
``` xml
<?xml version="1.0" encoding="UTF-8"?>
<actions>
    <action>
        <actionName>CUSTOM-pit</actionName>
        <displayName>pit</displayName>
        <goals>
            <goal>org.pitest:pitest-maven:mutationCoverage</goal>
        </goals>
    </action>
</actions>
```

### 4. Luo dokumentaatiokansio ja puske gittiin

Dokumentaatiolle kannattaa luoda oma kansio jotta projektin juuri pysyy siistinä. Tyhjään dokumentaatiokansioon täytyy lisäksi luoda edes yksi tiedosto jotta git osaa lisätä sen versiohallintaan. Tämän voi tehdä esimerkiksi luomalla valmiiksi enimmäisen viikkoraportin. Tämän jälkeen muutokset voi puskea gittiin.

![folder](http://saskeli.kapsi.fi/doc.png)