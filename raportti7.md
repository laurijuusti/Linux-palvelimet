
# Raportti 7, Real Internet (9.2.2023)

### OS: Windows 10 Home 21H2
### Virtualisointi: DigitalOcean VPS, 1 vCPU, 512MB RAM, 10GB SSD, Debian 11
### Host-tietokone: Ryzen 7 3700x, 32GB DDR4 RAM, NVIDIA RTX 3080



## a) Lue ja tiivistä (klo. x)

## a) Vuokraa oma palvelin (klo. 18.15)

Kirjauduin sisään DigitalOceaniin, aloitin uuden projektin vasemman reunan sivupalkista, annoin nimen ja painoin 'Create project' 

Serverin saan maksettua GitHub Educationista saatavilla crediteillä (200€ opiskelijoille)

![kuva](https://user-images.githubusercontent.com/122888655/217870221-d1e4de4c-9850-4d26-81ac-4ba9c525713c.png)


Tein uuden 'Dropletin', valitsin Frankfurtin sijainniksi, Debian 11 käyttöjärjestelmäksi, halvimman vaihtoehdon spekseihin, generoin host-tietokoneellani uuden ssh-avaimen komennolla

     $ ssh-keygen

Ja laitan dropletin käyttämään sitä. 

![kuva](https://user-images.githubusercontent.com/122888655/217870790-1d400705-25d2-4e0a-bb88-9328231595c0.png)

![kuva](https://user-images.githubusercontent.com/122888655/217871528-2e8e93f7-0697-4c42-91b3-882eba32c3e2.png)

![kuva](https://user-images.githubusercontent.com/122888655/217872304-7bdc52f1-aeaf-4475-b154-11de07fc33a2.png)

Annoin koneelle hostnamen, ja painoin 'Create droplet'.

Kone käynnistyi, ja pääsin sisään host-koneeltani komennolla 

      $ ssh@root[koneen ip-osoite]
      
![kuva](https://user-images.githubusercontent.com/122888655/217877621-7a1c1079-5cdf-4e33-a989-5f3bf5372ec3.png)

Sisällä ollaan!

## b) Alkutoimet (klo. 18.35)

Päivitin paketit komennolla

      $ sudo apt upgrade -y
      
jonka jälkeen asensin palomuurin, avasin portit 22 ja 80 sekä otin palomuurin käyttöön komennoilla 

      $ sudo apt install ufw, sudo ufw allow 22/tcp, sudo ufw allow 80/tcp, sudo ufw enable
      
![kuva](https://user-images.githubusercontent.com/122888655/217879179-1718685a-68f6-4335-b975-7aed8b6dd2f3.png)

Loin myös uuden käyttäjän, täytin tiedot ja lisäsin sen sudo-ryhmään komennoilla 

      $ adduser lauri, sudo adduser lauri sudo
      
Lukitsin root-käyttäjän komennolla 

      $ sudo usermod -L root
      
## c) Webserver (klo. 18.49)

Asensin Apachen, käynnistin Apachen ja vaihdoin kotisivun komennoilla

      $ sudo apt install apache2, sudo systemctl start apache2, echo 'Tehtävä 7' | sudo tee /var/www/html/index.html

Sitten kokeilin host-koneen selaimella mennä sivulle, se ei tosin vielä toiminut

![kuva](https://user-images.githubusercontent.com/122888655/217883069-2e03af5e-467a-49b3-a138-587a3037921c.png)

Sivun curlaus kuitenkin toimi. 

![kuva](https://user-images.githubusercontent.com/122888655/217883845-d5df9ae3-1ce2-448f-85ac-f752b58d764e.png)

En tiennyt mikä on vikana, joten käynnistin VPS:n uudelleen ja kokeilin lisätä palomuuriin reiän uudestaan, mutta sain vastaukseksi 'Skipping adding existing rule'.

    $ sudo reboot, sudo ufw allow 80/tcp
    
Näiden jälkeen se kuitenkin alkoi toimia, pääsin näkemään sivun host-koneeltani. (Ääkkösten näyttäminen ei onnistu jostain syystä...)
    
![kuva](https://user-images.githubusercontent.com/122888655/217884124-67327506-7c91-4d64-bd36-f312ac5a438e.png)


## d) Murtautumiset (klo. 18.59)

Tarkistin userlogin, auth.login, ja syslogin mutta niissä ei näkynyt mitään poikkeavaa.

![kuva](https://user-images.githubusercontent.com/122888655/217885530-5742cafa-da5d-4c29-8616-1a0ce89d1a2c.png)

Myöskään Apachen access- tai errorlokeissa ei näkynyt mitään erikoista (ainakaan vielä, tein tätä ennen testikoneen johon nettisivuja selaavat crawlerit yhdistivät heti)

![kuva](https://user-images.githubusercontent.com/122888655/217886546-a637950c-f976-4eee-b275-a898c616a590.png)



## Valmista tuli (klo. 19.14), tiivistys ja lähteet 

Pistin VPS:n pyörimään DigitalOceania käyttäen, pääsin koneeseen sisälle omalta koneeltani, asensin Apachen, leikin palomuurilla, ja katselin lokeja.

https://terokarvinen.com/2023/linux-palvelimet-2023-alkukevat/#h6-real-internettm

https://devconnected.com/how-to-manage-root-account-on-ubuntu-20-04/
