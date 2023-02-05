# Raportti 4, Based (5.2.2023)

### OS: Windows 10 Home 21H2
### Virtualisointi: VMware Workstation 17 Player
### Host-tietokone: Ryzen 7 3700x, 32GB DDR4 RAM, NVIDIA RTX 3080
### VM: 8GB RAM, 2 prosessoriydintä, 2GB VRAM


## a) Getting Started ja Name-based Virtual Host Support -Artikkelien tiivistäminen (klo. 18.47)

### Getting Started

  - Clientit pyytävät requesteja serveriltä, ja serveri antaa vastauksen (response) takaisin. 
  - Apachea konfiguroidaan simppelien tekstitiedostojen kautta.
  - Sivujen sisältö voi olla staattista tai dynaamista. Staattinen sisältö pysyy samana, mutta dynaaminen sisältö riippuu esim. pyynnöstä. 
  - Lokit ovat tärkeitä!
 
### Name-based Virtual Host Support

  - Apache-palvelin voi tarjota eri sisältöä riippuen yhdistävän clientin IP-osoitteesta.
  - Eri sisällölle pitää aina tehdä uusi VirtualHost

## a) Etusivu (klo. 21.14)

Loin apachen "/etc/apache2/sites-available" -kansioon tiedoston frontpage.conf, jossa on seuraava sisältö.

![image](https://user-images.githubusercontent.com/122888655/216840095-57ab53a9-0e91-41d5-a382-1b568625ccaf.png)

Tämä kertoo Apachelle, että etusivu löytyy kansiosta "/home/lauri/public_site/". Siellä on tiedosto, jonka nimi on index.html, jossa on kotisivun sisältö.
Sitten suoritin komennot 

      $ sudo a2ensite frontpage.conf
      $ sudo a2dissite 000-default.conf
      $ sudo systemctl restart apache2
      
Nämä komennot ottavat uuden etusivun käyttöön, poistavat vanhan käytöstä ja käynnistää apachen uudelleen. 

Nyt voin käydä muokkaamassa kotisivua:

![image](https://user-images.githubusercontent.com/122888655/216841081-a3c11ce7-9e2b-415f-84d3-14a920ed73f7.png)

![image](https://user-images.githubusercontent.com/122888655/216841232-cd511209-2f8e-4072-ac17-016099b39d36.png)

Lopputulos: 

![image](https://user-images.githubusercontent.com/122888655/216839934-e0e1963a-dacd-4e21-8f38-64afad9e048a.png)



## b) Kirjoitusvirhe (klo. 21.55)

Laitoin frontpage.confiin kirjoitusvirheen kansioon, jolloin kotisivua ei enää löydy. 

![image](https://user-images.githubusercontent.com/122888655/216841786-bf9a56c3-99d0-4b94-aa27-e64b4a7847a9.png)

![image](https://user-images.githubusercontent.com/122888655/216841801-eb229da5-b5fb-43ea-8460-cc558f19f8ab.png)

Error.logissa ei näy mitään tähän liittyen, mutta apache2ctl huomaa virheen ja kertoo että kansiota ei ole olemassa.

![image](https://user-images.githubusercontent.com/122888655/216841931-eabd1775-a1ed-4f16-b957-f3c6a90a369a.png)

![image](https://user-images.githubusercontent.com/122888655/216842077-82f41b0d-4d21-4699-8958-f4eb97e6b65a.png)


## Valmista tuli (klo. 22.06), tiivistys ja lähteet 

Raportissa vaihdoin apachen kotisivun, ja katsoin hieman virhelokeja. 

https://terokarvinen.com/2023/linux-palvelimet-2023-alkukevat/#h6-based
