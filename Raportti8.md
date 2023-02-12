
# Raportti 8, Say my name (Tiistai 12.02.2023)

### OS: Windows 11 Pro 22H2
### Virtualisointi: DigitalOcean Droplet, 1vCPU, 1GB RAM, 25GB SSD
### Host-tietokone: Intel i7-6700 @ 3.40GHz, 16GB DDR4, NVIDIA GTX 970

## a) Domain

### Kellonaikoja ei valitettavasti ole, kirjoittelen jälkeenpäin. Aikaa kului noin 2h.

Tein Namecheapiin käyttäjän, ja ostin domainin 'juusti.me' ilmaiseksi GitHub Educationin kautta. 

Menin domainin asetuksiin sivuston Dashboardista, valitsin 'Manage', sieltä edelleen 'Advanced DNS', ja laitoin Host Records -kohtaan vuokraamani palvelimen IP-osoitteen.

![image](https://user-images.githubusercontent.com/122888655/218339511-ae43fa65-4dbe-4d2c-80cf-9581d6e04b02.png)


![image](https://user-images.githubusercontent.com/122888655/218338890-5d51e7f1-789e-44a6-a494-c2cfa501be5d.png)

Palvelimella on Apache asennettuna, ja laitoin /etc/apache2/sites-available/etusivu.conf -tiedostoon sisältöön lisäksi rivin

      $ ServerName juusti.me
      
En nyt ollut ihan varma onko tämä täysin oikea ja paras tapa saada sivu näkymiin, mutta taisin kuitenkin onnistua koska sivu kuitenkin näkyy tietokoneella ja myös puhelimella eri verkon kautta. Tämä kaikki oli siis noin 1,5 tunnin selvittelyn, googlailun ja testailun tulos :D

![image](https://user-images.githubusercontent.com/122888655/218339210-17d2a33c-ff40-40f5-af8d-541c19f43a1a.png)


## b) Tutki tietoja



## Tiivistelmä, Valmista


## Lähteet 

https://serverfault.com/questions/470587/pointing-a-domain-name-to-a-vps

https://www.namecheap.com/support/knowledgebase/article.aspx/207/48/how-to-set-up-personal-nameservers-vps-and-dedicated-servers/

https://www.namecheap.com/support/knowledgebase/article.aspx/319/2237/how-can-i-set-up-an-a-address-record-for-my-domain/

https://askubuntu.com/questions/117931/how-do-i-set-up-hosting-a-domain-name-at-home-with-apache

https://terokarvinen.com/2023/linux-palvelimet-2023-alkukevat/#h8-say-my-name

