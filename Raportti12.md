# Raportti 12, Vianselvitys (Maanantai 6.3.2023)

### OS: MacOS 12.1 Monterey
### Virtualisointi: UTM 4.1.6 (https://mac.getutm.app)
### Host-tietokone: M1 MacBook Pro 13"
### VM: 2GB RAM


## a) Toimiva asennus (klo 18.38)

Tein viime tehtävän ongelmitta, joten asennuksen pitäisi olla täysin toimiva.

<img width="796" alt="image" src="https://user-images.githubusercontent.com/122888655/223174409-99acc72c-b8fb-4c15-9faf-c7af4cc76d69.png">

## b) Kirjoitusvirhe python -tiedostossa (klo 18.40)

Poistin settings.py -tiedostosta kohdan "ROOT_URLCONF = 'projekti.urls'". Tämän jälkeen suoritin komennot        

    $ touch wsgi.py & sudo systemctl restart apache2
    
Sitten sain seuraavan virheilmoituksen:

<img width="791" alt="image" src="https://user-images.githubusercontent.com/122888655/223177599-281acf87-5207-4fb0-9c8e-c9a065dac960.png">

Tämä kertoo, että palvelimen konfigurointi on tietenkin väärin, ja että lokista löytyy lisätietoja. Menin lokiin, ja tämä rivi oli alimmaisena:

<img width="723" alt="image" src="https://user-images.githubusercontent.com/122888655/223178402-23f0ba7f-52ff-471b-af57-b23fe25a40ac.png">

Tiedämme tämän perusteella, että asetuksissa ei ole poistamaani "ROOT_URLCONF" -attribuutia.

Korjasin ongelman lisäämällä kohdan takaisin tiedostoon, ja sivu toimi taas tämän jälkeen.

<img width="435" alt="image" src="https://user-images.githubusercontent.com/122888655/223179191-7b8da30d-8550-47a7-b335-6e3f58c102a8.png">

## c) Django-kansio väärässä paikassa (19.29)

Tällä hetkellä projektin kansio on sijainnissa /home/lauri/publicwsgi. Siirrän sen kansioon Desktop komennolla 

      $ mv projekti/ /home/lauri/Desktop/
      
<img width="586" alt="image" src="https://user-images.githubusercontent.com/122888655/223186442-d5a38224-2c5d-4fc3-a963-be1194fa352c.png">

Kuten kuvasta näkyy, kansio ei ole enää äskeisessä sijainnissa. Suoritin komennon

    $ sudo systemctl restart apache2
    
Joidenka jälkeen sain sivulta virheilmoitukseksi 403 Forbidden:

<img width="438" alt="image" src="https://user-images.githubusercontent.com/122888655/223187126-5bc0c04b-6f0c-4e7e-98f2-b2424650e5f6.png">

Lokitiedoston viimeinen rivi näyttää tältä: 

<img width="721" alt="image" src="https://user-images.githubusercontent.com/122888655/223187438-a575cb3c-ae0c-4954-b42e-fea82a0c6d7b.png">

En kyllä täysin ymmärrä miksi tulee 403 eikä 404 not found, mutta olkoon. 

Siirsin kansion takaisin komennoilla 

    $ cd, cd Desktop, mv projekti/ /home/lauri/publicwsgi
    
Jonka jälkeen sivu toimii taas.

<img width="429" alt="image" src="https://user-images.githubusercontent.com/122888655/223190607-f04e82e3-ad48-4596-8b7a-89eb681f2d02.png">

## d) Väärät oikeudet (klo. 20.00)

Suoritin komennot 

    $ chmod ugo-rwx projekti/ & chmod u+rx projekti/ & sudo systemctl restart apache2
    
Sain tämän jälkeen taas 403 Forbidden. 

Lokit näyttävät seuraavaa: 

<img width="721" alt="image" src="https://user-images.githubusercontent.com/122888655/223193986-1985569a-9bd9-495d-a46e-09a9e538b397.png">

Kansiolta (tai joltain sen polun osalta, tässä tapauksessa kansio) näyttäisi puuttuvan hakuoikeudet. 

Palautin oikeudet komennolla, joka antaa tiedostoon kaikille käyttäjille kaikki oikeudet. (ei kovin turvallista, käytän vain koska testivirtuaalikone) 

    $ chmod 777 projekti/ 
    
Tämän jälkeen sivu toimi taas normaalisti. 

<img width="797" alt="image" src="https://user-images.githubusercontent.com/122888655/223195887-78353ff0-9d8f-43f2-861e-9f153770e3c2.png">

## e) Kirjoitusvirhe apachessa (klo 20.16)

Laitoin sivun asetuksista kofiguraation osoittamaan kansioon jota ei ole olemassa. 

<img width="582" alt="image" src="https://user-images.githubusercontent.com/122888655/223196931-fd2c298f-e32e-4aa5-9a3b-b41f5658c9f4.png">

Käynnistin apachen uudelleen, ja sain taas 403 forbiddenin:

<img width="427" alt="image" src="https://user-images.githubusercontent.com/122888655/223197391-43bb6391-d56d-42a4-a05c-3d0d8902229d.png">

Lokit näyttävät näin:

<img width="722" alt="image" src="https://user-images.githubusercontent.com/122888655/223197675-8f6b1cc5-0565-4953-b69d-9d836d02ce90.png">

Veikkaan että client yrittää pyytää tiettyä kansiota, mutta koska polku on määritetty asetuksissa väärin, se ei onnistu. 

Korjasin ongelman määrittämällä polun taas oikeaksi, ja sivu toimii taas. 

## f) Puuttuva WSGI-moduuli (klo. 20.27)

Poistin wsgi-moduulin komennolla 

    $ sudo apt purge libapache2-mod-wsgi-py3
    
Apachen käynnistäminen ei enää onnistu. 

<img width="749" alt="image" src="https://user-images.githubusercontent.com/122888655/223199091-b035862e-8a77-4237-8b8c-5126fe3b43da.png">

Apache yrittää etsiä käynnistymisen yhteydessä WSGI:n Daemonia, mutta ei löydä sitä ja ei täten käynnisty. 

Asensin paketin uudestaan, ja apachen käynnistäminen toimii ja sivu näkyy taas. 

## g) Väärä domain (klo. 20.34)

Muutin settings.py -tiedostossa ALLOWED_HOSTS kohdan tyhjäksi, jolloin minkään palvelimeen yhdistämisyrityksen ei pitäisi toimia. 

Nyt saan vastaukseksi 400 Bad Request. Serveri ei siis aio suorittaa pyyntöä, koska host (localhost) ei ole sallittu. 

Errorlokissa ei näy tähän liittyen mitään erikoista. 

Laitoin localhostin taas sallituksi hostiksi, ja sivu toimii. 

## Tiivistelmä, lähteet (klo. 20.40)

Raportissa leikin hieman apachella ja djangolla, aiheutin ja korjasin tahalleen eri vikoja. 

Lähteet:

https://linuxhandbook.com/chmod-command/

https://terokarvinen.com/2023/linux-palvelimet-2023-alkukevat/#h12-vianselvitys

https://developer.mozilla.org/en-US/docs/Web/HTTP/Status/400
