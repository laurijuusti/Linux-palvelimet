# Raportti 11, Deploy Django 4 - Production Install (Torstai 2.03.2023)

### OS: MacOS 12.1 Monterey
### Virtualisointi: UTM 4.1.6
### Host-tietokone: M1 MacBook Pro 13"
### VM: 2GB RAM, 2 prosessoriydintä

## a) Apache (klo 19.30)

Päivitin paketit ja asensin Apachen.   

    $ sudo apt update & sudo apt install apache2 -y
    
Vaihdoin defaultsivun sisällön.

<img width="669" alt="image" src="https://user-images.githubusercontent.com/122888655/222513759-66a7fd88-df97-4df9-831a-628ed138fb2b.png">

Loin kansiot uudelle sivulle.

<img width="725" alt="image" src="https://user-images.githubusercontent.com/122888655/222515279-c1a43f29-f2a3-4f49-823d-3ee28c86aba5.png">

Muutin VirtualHostia:

    $ sudoedit /etc/apache2/sites-available/000-default.conf 

<img width="547" alt="image" src="https://user-images.githubusercontent.com/122888655/222516519-a639af86-e00c-4099-9883-12993dddc432.png">

Testasin että konfiguraatio toimii, ja käynnistin apachen uudelleen.

<img width="413" alt="image" src="https://user-images.githubusercontent.com/122888655/222517105-af4b33e1-e9df-4e79-b0f8-9f06cc8e4708.png">

Toimii!

<img width="403" alt="image" src="https://user-images.githubusercontent.com/122888655/222517809-86bc9518-4cc8-4818-ab6f-7a180a015316.png">

 ### Django
 
 Asensin virtualenvin ja sitten Djangon virtualenvin sisälle.
 
    $ sudo apt-get -y install virtualenv
    $ cd publicwsgi/
    $ virtualenv -p python3 --system-site-packages env
    $ source env/bin/activate
    $ which pip

<img width="448" alt="image" src="https://user-images.githubusercontent.com/122888655/222518672-c8457c22-76d6-42a8-b9b3-28bef9331274.png">

Tein requirements.txt -tiedoston, jonka sisällä oli teksti "django".

<img width="585" alt="image" src="https://user-images.githubusercontent.com/122888655/222519179-0f6203bb-b9cf-453b-b86d-62f6e1b1be91.png">

Django asentui onnistuneesti.

Loin uuden projektin

    $ django-admin startproject projekti

Kopioin artikkelissa olevan Virtualhost -tiedoston, ja muokkasin sitä omien kansioiden mukaan.

<img width="654" alt="image" src="https://user-images.githubusercontent.com/122888655/222521009-09e3d7a5-0a30-4782-8c2e-bcf0c988a9b2.png">

Asensin Apachen WSGI-moduulin, tarkistin syntaksin ja käynnistin Apachen uudelleen. Tämän jälkeen tarkistin, että Djangon asennus toimii. Seuraavaksi tarkistin Djangon pyörivän Apachella komennolla

    $ curl -sI localhost

<img width="655" alt="image" src="https://user-images.githubusercontent.com/122888655/222522862-d7701bca-719e-457e-9274-a0ab0d62d146.png">


Muokkasin settings.py -tiedostoa.
 
 <img width="585" alt="image" src="https://user-images.githubusercontent.com/122888655/222524921-6ab5a1f5-40c3-4438-9847-76fd56fb4546.png">

Minulla ei ole sivua jota haluan käyttää tällä hetkellä, joten laitan ALLOWED_HOSTS -kohtaan vain "localhost".

Tallensin ja käynnistin Apachen taas uudelleen.

<img width="723" alt="image" src="https://user-images.githubusercontent.com/122888655/222525791-1cac74ec-278c-462f-a0df-969920a20bb0.png">

Kuten artikkelissa, sivua ei enää löydy. 

<img width="448" alt="image" src="https://user-images.githubusercontent.com/122888655/222526005-ed8d1dd8-cd0b-43bd-9652-0834b4f56910.png">

localhost/admin löytyy, ja Djangon kirjautumissivu näkyy. Kuten viime kotitehtävässä, loin superuser-käyttäjän Djangoon komennoilla

    $ ./manage.py makemigrations
    $ ./manage.py migrate
    $ ./manage.py createsuperuser
    
Pääsin sisään!

<img width="424" alt="image" src="https://user-images.githubusercontent.com/122888655/222527584-feb9ce9b-8430-4232-9418-d9245abde610.png">

Seuraavaksi muokkasin taas settings.py -tiedostoa artikkelin mukaan, jotta CSS toimisi. 

<img width="474" alt="image" src="https://user-images.githubusercontent.com/122888655/222528110-4c2b19ee-3988-44e0-8774-926c6250d490.png">

Seuraavaksi suoritin komennon

    $ ./manage.py collectstatic
    
<img width="680" alt="image" src="https://user-images.githubusercontent.com/122888655/222528309-db702f78-f58b-4b84-adac-aa77d534f13f.png">

Toimii!

<img width="776" alt="image" src="https://user-images.githubusercontent.com/122888655/222528417-ebf95be7-27b6-4513-a04d-14a167eb0ade.png">









