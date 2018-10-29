# Suorituskykytestaus

Voit suorituskykytestauksessa laskea ohjelmasi suoritukseen kuluvan ajan esimerkiksi seuraavasti:
```java
long aikaAlussa = System.currentTimeMillis();
< kutsu tässä testattavaa operaatiota >
long aikaLopussa = System.currentTimeMillis();
System.out.println("Operaatioon kului aikaa: " + (aikaLopussa - aikaAlussa) + "ms.");
```

Myös ```System.nanoTime()``` on hyödyllinen jos ohjelma on niin nopea että ```currentTimeMillis``` ei anna järjellisiä tuloksia.

Ohjelma kannattaa ajaa kullakin syötekoolla/testiaineistolla useita kertoja (esim. 10 kpl) ja ottaa keskiarvo (tai mediaani) kuluneesta ajasta. Myös rakenteeltaan erilaisia syötteitä on hyvä testata, esimerkiksi tiedon pakkauksessa: kirja vs. satunnaisesti generoitu tekstisyöte.

Tehdessäsi dokumentaatiota suorituskykytestauksesta kerro mitä testasit ja muutenkin avaa tuloksia, älä siis vain copypastea lukuja.
