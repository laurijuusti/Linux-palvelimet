# Raportti 2, Komentaja Pingviini (21.01.2023)

### OS: Windows 10 Home 21H2
### Virtualisointi: VMware Workstation 17 Player
### Host-tietokone: Ryzen 7 3700x, 32GB DDR4 RAM, NVIDIA RTX 3080
### VM: 8GB RAM, 2 prosessoriydintä, 2GB VRAM


## a) Command Line Basics -artikkelin tiivistäminen (klo. 22.49)
 - Tärkeimpiä komentoja on esim. 
 
        $ cd, ls, pwd, mkdir, mv, cp, rm, rmdir, history
        
 - Komennoista voi saada lisätietoa kirjoittamalla "man" + komento, esim

        $ man mkdir
        
 - Kun komennon eteen laitetaan "sudo", tulee komento suoriutumaan kaikilla oikeuksilla.
 - Tabilla on helppo täydentää komentoja nopeasti.
 - Tärkeitä kansioita ovat esim. root, home/*käyttäjänimi*/, media ja var/log/

## a) Asenna Micro (klo 22.58)
 Suorittamalla komennot 
 
      $ sudo apt-get update
      $ sudo apt-get install micro
      
 Saa Micron asennettua.

![kuva](https://user-images.githubusercontent.com/122888655/213886863-b69c70dd-5f1b-48a3-98d1-83ddc25f3960.png)

Minulla oli jo Micro valmiiksi asennettuna, mutta näillä komennoilla sen olisi saanut asennettua. 


## b) Komponenttien listaus (23.02)

Suorittamalla komennon 
 
      $ sudo apt-get install lshw
      
Asennan ensiksi lshw -ohjelman. 

![kuva](https://user-images.githubusercontent.com/122888655/213886984-d951b669-33fa-4878-a90b-857a3d8bea2a.png)

Tämän jälkeen suoritan komennon 
    
      $ sudo lshw -short -sanitize
      
Ja tulostuu (pitkä) lista. Komento näyttää koneessa kiinni olevat osat kuten prosessorin, muistit ja kovalevyn sekä esim. USB-laitteet ja nettikortin. Piti rajata kuvankaappauksia hieman, komento listasi esim. jokaisen prosessorisäikeen omalle rivilleen. 

Komennon lipuista "-sanitize" poistaa hieman tietoja listasta, kuten IP-osoitteen ja sarjanumeroita. "-short" taas tulostaa vasemmalla reunalla näkyvät Hardware pathit treemaiseen kompaktiin muotoon.

![kuva](https://user-images.githubusercontent.com/122888655/213887048-9945d974-1945-4d36-81e6-1ccc956e4832.png)
![kuva](https://user-images.githubusercontent.com/122888655/213887129-7930f6c7-765f-4870-9a32-f7a0e841ec27.png)


## c) Apt:n käyttö (klo. 23.14)

Aiemmin päivitin jo saatavilla olevien pakettien listan komennolla

      $ sudo apt-get update
      
Kolme haluamaani ohjelmaa ovat Neofetch, Htop sekä Cmatrix.

näiden asennus onnistuu komennolla 

      $ sudo apt-get install neofetch htop cmatrix -y
      
![kuva](https://user-images.githubusercontent.com/122888655/213887973-3401b2f0-2346-4128-86c2-e23cadbaf3b1.png)


Neofetch on pieni ohjelma, joka tulostaa hieman tietoja koneesta, sekä ASCII-kuvan distron logosta. 

    $ neofetch

![kuva](https://user-images.githubusercontent.com/122888655/213887692-1c9854c4-6ae6-4c88-845b-55b0e956db4c.png)

Htop on ohjelma, joka näyttää käynnissä olevia prosesseja sekä esim. käytetyn muistin, käynnissäoloajan ja prosessorin käytön.

    $ htop
    
![kuva](https://user-images.githubusercontent.com/122888655/213888004-91d48125-f23a-4185-aed6-d3586c49adda.png)

Cmatrix on pieni ohjelma, joka tulostaa terminaaliin Matrix -tyylistä vihreää animoitua "tippuvaa" tekstiä.

    $ cmatrix

![kuva](https://user-images.githubusercontent.com/122888655/213888037-1c18c229-6fd5-46e5-9505-586ad48d03f2.png)

## d) Tärkeät kansiot (klo. 23.40)

Root -kansio. Ylin kansio koko järjestelmässä, sisältää kaiken, esim. jokaisen käyttäjän kotikansion. 

![kuva](https://user-images.githubusercontent.com/122888655/213888184-027b50a0-9a86-467d-a7e4-fe2f4e4b4de3.png)

Home -kansio. Sisältää kaikkien käyttäjien omat kansiot. 

![kuva](https://user-images.githubusercontent.com/122888655/213888197-9fc8b01f-0d45-4527-9ed0-0481c2d09a89.png)

Käyttäjän oma kansio. Sisältää käyttäjän kansiot, esim. työpöydän, ja vain sinne voi käyttäjä tallentaa pysyvästi tietoa. 

![kuva](https://user-images.githubusercontent.com/122888655/213888267-a964f596-0c04-4f08-974f-e1329c3492a3.png)

Media -kansio. Siellä näkyvät esim. ulkoiset kovalevyt.

![kuva](https://user-images.githubusercontent.com/122888655/213888298-ca763059-422c-4a0b-81af-e8994620a29e.png)

Etc -kansio. Järjestelmän asetukset löytyvät sieltä. 

![kuva](https://user-images.githubusercontent.com/122888655/213888362-47596963-c5ca-4f9a-a2f1-b1e65087cccc.png)

Etc:stä löytyvä "debian_version" -tiedosto. Sisältää käyttöjärjestelmän version. 

![kuva](https://user-images.githubusercontent.com/122888655/213888392-ff5d15e9-67df-4cb2-84ec-a3fd6a70ae8b.png)

Var/log/. Sisältää lokeja järjestelmästä, hyödyllistä!

![kuva](https://user-images.githubusercontent.com/122888655/213888433-c60514aa-eda1-478a-9e1d-d1016b2e0b47.png)

Kansiossa oleva "user.log". Sisältä löytyy loki käyttäjän toimista.

![kuva](https://user-images.githubusercontent.com/122888655/213888502-d1ef9e4c-1012-46e7-8e83-56655dc9dff6.png)


## e) Grep (klo. 23.59)

Grep on komento, jolla voi etsiä tiedostoista sanoja tai merkkijonoja. 

Loin työpöydälle tiedoston "lauri.md", johon kirjoitin tekstiä. 
Komennolla 

      $ grep "lauri" lauri.md
      
Se etsii sisällöstä kaiken joka sisältää termin "lauri". 

![kuva](https://user-images.githubusercontent.com/122888655/213888891-d4df6403-ee87-44b2-b35d-42d83dbf3138.png)

Lipulla "-c" komento tulostaa kuinka monta kertaa jokin termi esiintyy tiedostossa.

      $ grep -c "lauritesti" lauri.md

![kuva](https://user-images.githubusercontent.com/122888655/213888872-502bdb28-b2b8-478c-bc28-495789d9cbe1.png)

## Tiivistelmä, Valmista (klo. 00.10)

Tässä raportissa kävin läpi terminaalissa grep- komennon käyttöä, paketinhallintaa, tärkeitä kansioita, ja terminaalissa pyöriviä ohjelmia sekä tiivistin artikkelin muutamaan riviin . 
      
## Lähteet 

 - https://terokarvinen.com/2020/command-line-basics-revisited/ (Tero Karvinen, 2020)
 - https://linux.die.net/man/1/lshw (linux.die.net)
 - https://www.cyberciti.biz/faq/howto-use-grep-command-in-linux-unix/ (Vivek Gite, 2023)
