# Raportti 3, Hello Web (Tiistai 31.01.2023)

### OS: Windows 11 Pro 22H2
### Virtualisointi: VMware Workstation 17 Player
### Host-tietokone: Intel i7-6700 @ 3.40GHz, 16GB DDR4, NVIDIA GTX 970
### VM: 4GB RAM, 2 prosessoriydintä



## x) Rise of Open Source ja FSF Free Software Definition -artikkelien tiivistäminen (klo. 17.55)

- Vapaan ohjelmiston käyttäjillä on oikeus mm. muokata, jakaa, opiskella, käyttää ja kopioida ohjelmistoa haluamallaan tavalla. 
- Vapaan ohjelmiston kulmakivenä toimii neljä vapautta. Vapaus käyttää ohjelmistoa, vapaus jakaa ohjelmistoa (myös mahdolliset itse muokkaamat kopiot) sekä mahdollisuus lukea ja opiskella ohjelmiston toimivuutta sekä lähdekoodia. 
- Vapaa ohjelmisto voi olla kaupallista, mutta sen ei tarvitse olla. 



## a) Apachen esimerkkisivu (klo 21.10)

Muokkasin apachen oletussivua komennolla 

        $ echo 'moi' | sudo tee /var/www/html/index.html
        
Joka kirjoittaa kotisivun .html -tiedoston sisällöksi "moi". Kotisivu on siis kansiossa "/var/www/html/".

![image](https://user-images.githubusercontent.com/122888655/215859368-0421ab1b-1a32-44a3-9205-4fa5b65c28c3.png)

Komennon suorittamisen jälkeen näyttää tältä. 

## b) Käyttäjän kotisivu (klo 21.15)

Loin "mkdir" -komennolla kotikansiooni kansion "public_html", johon loin tiedoston "index.html", mihin kirjoitin hieman sisältöä.

        $ cd, mkdir public_html, nano index.html 
        
![image](https://user-images.githubusercontent.com/122888655/215859220-3774ec1f-1b33-44d1-99d6-d92f0d29d269.png)

Komentojen jälkeen kotikansio näyttää tältä. Sama sisältö saadaan myös, jos hakee sivun curl-komentoa käyttäen. 

![image](https://user-images.githubusercontent.com/122888655/215862092-11ea54df-a795-4a2b-ac0f-affc63b42519.png)

## c) Uusi käyttäjä (klo. 21.24)

Suoritin komennon 

      $ sudo adduser laurintesti1
      
Joka lisää käyttäjän "laurintesti1" järjestelmään. 

![image](https://user-images.githubusercontent.com/122888655/215862790-e0d31426-65ab-4ea7-b028-bdcccc78c40f.png)

Kuvankaappaus koko käyttäjän lisäämisprosessista. Uuden käyttäjän userid on 1001, eli yksi isompi kuin oman käyttäjäni. Kysyy tietenkin salasanan käyttäjälle, sekä hieman muita satunnaisia tietoja. Piti oikein googlata että minkä takia komento kysyy huoneen numeroa, vaikuttaisi olevan joku jäännös UNIX-järjestelmien alkuajoilta :D.

## d) Validi HTML5 (21.32)


![image](https://user-images.githubusercontent.com/122888655/215865153-afe066a4-241c-4665-b6b9-5c62600c8b5d.png)

Tarkistin vielä W3Schools:n HTML-validaattorilla, ja läpi meni.

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>HTML5 Sivutesti</title>

    <style>
        body {background-color: bisque;}

        h2 {font-family: 'Gill Sans', 'Gill Sans MT', 'Trebuchet MS', sans-serif;}
        p {font-family: 'Gill Sans', 'Gill Sans MT', 'Trebuchet MS', sans-serif;}        
    </style>

</head>
<body>
    
    <h2>Laurin hieno kotisivu</h2>
    <p>Esimerkkitekstiä</p>
    <p>Hieno CSS, eikö?</p>

</body>
</html>
## Tiivistelmä, Valmista (klo. 14.48)


## Lähteet 

https://terokarvinen.com/2023/linux-palvelimet-2023-alkukevat/#h5-hello-web

https://www.geeksforgeeks.org/tee-command-linux-example/
