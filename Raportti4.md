# Raportti 4, Tukki (28.01.2023)

### OS: Windows 10 Home 21H2
### Virtualisointi: VMware Workstation 17 Player
### Host-tietokone: Ryzen 7 3700x, 32GB DDR4 RAM, NVIDIA RTX 3080
### VM: 8GB RAM, 2 prosessoriydintä, 2GB VRAM


## a) Artikkelin tiivistäminen (klo. 23.15)

Aloin selaamaan HackerNewsiä kinnostavan artikkelin perässä. Löysin artikkelin nimeltä "A personal log from the command line" jossa puhuttiin jobrog -nimisestä sovelluksesta.

- Jobrog on terminaalissa toimiva sovellus, johon voit suoraan terminaalista merkitä päivän aikana tekemiäsi asioita.
- Sovellus pitää logia asioista joita haluat, kellonajat mukaanlukien. 
- Hyvä esimerkiksi päivän aikana tehtyjen työtehtävien merkitsemiseen, näkee myöhemmin mitä on tehnyt mihin aikaan. 
- Voi myös käyttää muistiinpanoihin. 

## b) Logien analyysi (klo. 23.40)

Navigoin kansioon /var/log/ käyttäen cd- ja ls -komentoja, ja syötin komennon               

        $ sudo cat syslog
        
Ruudulle tulostuu satoja rivejä logeja. Selasin hieman, ja löysin tämän:

![kuva](https://user-images.githubusercontent.com/122888655/215292597-de4b012f-6946-4d9e-8e8b-d87dd90af10f.png)

Systemd näyttäisi tekevän taustalla jonkinlaista väliaikaisten hakemistojen siivoamista. 

Seuraavaksi katsoin auth.log -tiedostoa komennolla 

        $ sudo cat auth.log
        
![kuva](https://user-images.githubusercontent.com/122888655/215292740-925fafb7-290d-4803-b381-14a3d7ffe91c.png)

Kuten näkyy, logiin kirjautuu sudo-komennon käyttö tarkkoine kellonaikoineen sekä tieto kuka komennon antoi. (userid + käyttäjänimi)

Sitten katsoin Apachen logeja komennolla

        $ sudo cat apache2/access.log
        
![kuva](https://user-images.githubusercontent.com/122888655/215292913-44f685bf-70dd-44ae-8a03-c2519090aa38.png)

Siellä näkyy onnistunut yhteys (HTTP koodi 200) omalta tietokoneeltani (127.0.0.1) kellonaikaan 23.53 Suomen aikavyöhykkeeltä Firefox-selaimelta Linux käyttöjärjestelmältä. 

Virhelogia katsoin komennolla 

        $ sudo cat apache2/error.log
        
![kuva](https://user-images.githubusercontent.com/122888655/215293015-1cde2563-deb3-44b9-84ea-53f8a536bfc6.png)

Siellä ei mitään kummoista näkynyt, pelkästään ilmoitus siitä että Apache on konfiguroitu ja käynnissä normaalisti. Logissa näkyy samaan tapaan kellonaika, ja lisäksi myös sovelluksen prosessi-id. 

## b) Tapahtumien aiheuttaminen (klo. 00.04)

Aiheutan Apachen access -logiin käyttäjävirheen menemällä selaimella palvelimen kansioon jota ei ole olemassa.

![kuva](https://user-images.githubusercontent.com/122888655/215293186-46f590cc-f06f-4639-a0d7-37633fc73909.png)

Tämä näkyy logissa:

![kuva](https://user-images.githubusercontent.com/122888655/215293216-40c7cc51-52ee-4467-943a-4150602b1538.png)

Huomataan, että tällä kertaa tuli HTTP koodi 404, eli kohdetta ei löytynyt palvelimelta. Sama IP-osoite, eri kellonaika, sama selain. 

Aiheutin toisen tapahtuman, tällä kertaa käyttöjärjestelmän authlogiin syöttämällä kirjautumisruudulla väärän salasanan. 

![kuva](https://user-images.githubusercontent.com/122888655/215293882-4d64912a-584b-4052-9301-41d9a8fa2b47.png)

Kellonaika ja päivä kirjautuivat ylös, ja myös kirjautumista yrittänyt käyttäjä. Authentication failure kertoo sen, että kirjautuminen ei onnistunut. 


## Valmista tuli (klo. 00.26), tiivistys ja lähteet 

Tiivistin löytämäni artikkelin simppelistä sovelluksesta jolla voi seurata ja logata asioita joita päivän aikana on tehnyt. 
Selasin käyttöjärjestelmän logeja, ja aiheutin niihin hieman tapahtumia. 

- https://github.com/dfhoughton/jobrog
 
- https://news.ycombinator.com/item?id=22281815
