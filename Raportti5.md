# Raportti 3, Hello Web (Tiistai 31.01.2023)

### OS: Windows 11 Pro 22H2
### Virtualisointi: VMware Workstation 17 Player
### Host-tietokone: Intel i7-6700 @ 3.40GHz, 16GB DDR4, NVIDIA GTX 970
### VM: 4GB RAM, 2 prosessoriydintä

## x) Indie Hackers -podcastjakson tiivistäminen (klo. )



## a) Apachen esimerkkisivu (klo 21.10)

Muokkasin Apachen oletussivua komennolla 

        $ echo 'moi' | sudo tee /var/www/html/index.html
        
Joka kirjoittaa kotisivun .html -tiedoston sisällöksi "moi". Kotisivu on siis kansiossa "/var/www/html/".

![image](https://user-images.githubusercontent.com/122888655/215859368-0421ab1b-1a32-44a3-9205-4fa5b65c28c3.png)

Komennon suorittamisen jälkeen näyttää tältä. 

## b) Käyttäjän kotisivu (klo 21.15)

Loin "mkdir" -komennolla kotikansiooni kansion "public_html", johon loin tiedoston "index.html", mihin kirjoitin hieman sisältöä.

        $ cd, mkdir public_html, cd public_html, nano index.html 
        
![image](https://user-images.githubusercontent.com/122888655/215859220-3774ec1f-1b33-44d1-99d6-d92f0d29d269.png)

Komentojen jälkeen kotikansio näyttää tältä. Sama sisältö saadaan myös, jos hakee sivun curl-komentoa käyttäen. 

![image](https://user-images.githubusercontent.com/122888655/215862092-11ea54df-a795-4a2b-ac0f-affc63b42519.png)

## c) Uusi käyttäjä (klo. 21.24)

Suoritin komennon 

      $ sudo adduser laurintesti1
      
Joka lisää käyttäjän "laurintesti1" järjestelmään. 

![image](https://user-images.githubusercontent.com/122888655/215862790-e0d31426-65ab-4ea7-b028-bdcccc78c40f.png)

Kuvankaappaus koko käyttäjän lisäämisprosessista. Uuden käyttäjän userid on 1001, eli yksi isompi kuin oman käyttäjäni. Kysyy tietenkin salasanan käyttäjälle, sekä hieman muita satunnaisia tietoja. Piti Googlata että minkä takia komento kysyy huoneen numeroa, vaikuttaisi olevan joku jäännös Unix-järjestelmien alkuajoilta :D

## d) Validi HTML5 (21.32)

Muokkasin public_html -kansion sisällä olevaa tiedostoa "index.html", ja lisäsin sinne hieman HTMLää.

![image](https://user-images.githubusercontent.com/122888655/215865711-ec13174f-f0b6-4752-8a00-528c45c37610.png)


![image](https://user-images.githubusercontent.com/122888655/215865153-afe066a4-241c-4665-b6b9-5c62600c8b5d.png)

Tarkistin sen vielä W3Schools:n HTML-validaattorilla, ja läpi meni.

## Tiivistelmä, Valmista (klo. )


## Lähteet 

https://terokarvinen.com/2023/linux-palvelimet-2023-alkukevat/#h5-hello-web

https://www.geeksforgeeks.org/tee-command-linux-example/

https://www.quora.com/What-does-room-number-stands-for-when-setting-up-a-new-account-on-Ubuntu
