# Raportti 10, DJ Ango (Maanantai 27.02.2023)

### OS: Windows 11 Pro 22H2
### Virtualisointi: VMware Workstation 17 Player
### Host-tietokone: Intel i7-6700 @ 3.40GHz, 16GB DDR4, NVIDIA GTX 970
### VM: 4GB RAM, 2 prosessoriydintä

## a) Kannattavaa (klo 14.04)

Asensin virtuaaliympäristön komennolla 

    $ sudo apt update & sudo apt install virtualenv
    
![image](https://user-images.githubusercontent.com/122888655/221559740-049ddbdd-e0ec-4728-b2a7-98d0bbf7ccfb.png)

Ajoin komennon 

    $ virtualenv --system-site-packages -p python3 env/
    
joka loi kansion 'env' omaan hakemistooni. Kansio sisältää kaiki tarvittavat python-paketit. 

![image](https://user-images.githubusercontent.com/122888655/221560174-e9365bdc-d816-4031-8b66-e9240fe60a3d.png)

Seuraavaksi menin virtuaaliympäristööni komennolla 

     $ source env/bin/activate
     
ja asensin Djangon tekemällä requirements.txt -tiedoston, jonka sisältönä on 'django'.

     $ pip install -r requirements.txt

![image](https://user-images.githubusercontent.com/122888655/221561465-c1ccff13-6555-436a-9792-f8f2d9c3e64a.png)

Tarkistin vielä että Django oli asentunut kunnolla komennolla 

    $ django-admin --version
    
![image](https://user-images.githubusercontent.com/122888655/221564629-bbdc7c0d-047d-4d7e-9090-a08930d2d71f.png)

## Tauko, jatkoin 19.30

Käynnistin djangoprojektin, navigoin projektin kansioon ja käynnistin palvelimen komennoilla

    $ django-admin startproject env & ./manage.py runserver

![image](https://user-images.githubusercontent.com/122888655/221639511-71822aad-6963-4cf3-80d4-aa19352cf687.png)

![image](https://user-images.githubusercontent.com/122888655/221639004-b7de83df-d09c-4722-a2d3-af9af90f4a0b.png)

Päivitin databasen, mutta mitään päivitettävää ei ollut. 

![image](https://user-images.githubusercontent.com/122888655/221639998-df810cf1-1084-4eb8-8399-defb945e91bf.png)

Asensin sovelluksen pwgen (luo salasanoja), ja lisäsin uuden käyttäjän admin-paneeliin. 

    $ sudo apt install pwgen
    $ pwgen -s 20 1
    $ ./manage.py createsuperuser
    
![image](https://user-images.githubusercontent.com/122888655/221641275-61153a6e-636a-405c-9f27-9d25381a2f39.png)


Pääsin sisään!

![image](https://user-images.githubusercontent.com/122888655/221641021-6426ec15-ff46-4799-8330-8f2319ad4d51.png)

## Toinen tauko, jatkoin 20.50

Tein toisen käyttäjän samalla tavalla kuin edellisen, ja katsoin että tälläkin käyttäjällä on staff- ja admin-oikeudet.

![image](https://user-images.githubusercontent.com/122888655/221655829-d5549033-e74b-425e-86a2-6c0b58657da4.png)

Käynnistin crm-applikaation, ja lisäsin kohdan 'crm' settings.py -tiedostoon 

    $ ./manage.py startapp crm

![image](https://user-images.githubusercontent.com/122888655/221656960-6231a844-dc74-49d8-87b3-5490b2229620.png)

![image](https://user-images.githubusercontent.com/122888655/221657120-1b4a332e-b629-4d13-88b2-55dad7298aa9.png)


Lisäsin sisällön models.py -tiedostoon, tein 'Customer' tietokannan.

![image](https://user-images.githubusercontent.com/122888655/221657692-1b01c691-5bad-492f-82fe-730d2681e823.png)

Tein asiakastietokannalle migraation, piti varmistaa vielä että olen oikeassa kansiossa.

![image](https://user-images.githubusercontent.com/122888655/221658181-cb064f60-05f9-488b-9113-c2b560938ded.png)

Muokkasin admin.py -tiedostoa, jotta tietokanta näkyy

![image](https://user-images.githubusercontent.com/122888655/221658779-28a7a930-6ece-49d4-9ee7-e167a0c52289.png)

Sain asiakkaita luotua!

![image](https://user-images.githubusercontent.com/122888655/221659496-c384ebd9-ad73-4330-a7ef-65abb39d421a.png)

Muokkasin vielä admin.py -tiedostoa hieman että asiakkaat saavat nimen. Toimii!

![image](https://user-images.githubusercontent.com/122888655/221659433-67a46832-b03c-4f27-bec4-adad444cd0b8.png)

![image](https://user-images.githubusercontent.com/122888655/221659798-566df8f3-3ee7-41be-a969-7e9e853c113e.png)


## Valmista, tiivistys (klo. 21.13)

Tässä raportissa asensin Djangon, loin projektin, käynnistin sen, loin käyttäjiä, loin asiakastietokannan ja tein testiasiakkaan.

## Lähteet 

https://terokarvinen.com/2022/django-instant-crm-tutorial/


