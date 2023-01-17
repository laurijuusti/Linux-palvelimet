# Raportti 1, Debianin asennus virtuaalikoneelle (17.01.2023)

## Asennusympäristö: Käyttöjärjestelmänä toimii Windows 11 Pro, virtualisointiohjelmana toimii VMware Workstation 17 Player.


## a) Raportin kirjoittaminen -artikkelin tiivistäminen
 - Selkeät, helppolukuiset ja tarkat ohjeet siitä mitä on tehty
 - Kellonajat on hyvä olla mukana, jotta saa kuvan käytetystä ajasta
 - Kuvat ovat hyviä visualisoimaan tekemistä

## b) Asennus
Klo 19.39, latasin Debian 11.6 .iso-tiedoston AMD64 prosessoriarkkitehtuuria varten KDE-työpöydällä Debianin nettisivuilta osoitteesta https://cdimage.debian.org/images/unofficial/non-free/images-including-firmware/current-live/amd64/iso-hybrid/

Klo 19.47, latauksen valmistuttua aloitin virtuaalikoneen luomisen, valitsin oikean .iso -tiedoston:

![image](https://user-images.githubusercontent.com/122888655/212973646-9b1e3185-42d6-47db-8de2-881c457998eb.png)

Tässä näkyy virtuaalikoneen asetukset, annoin sille 4GB RAM-muistia, 60GB dynaamisen kovalevyn ja 2 prosessoriydintä. Muut asetukset ovat vakioita, jotka VMware laittoi:

![image](https://user-images.githubusercontent.com/122888655/212973831-cdaea1a4-bf54-484c-a94c-c28978fc9e7e.png)

Klo 19.50, käynnistin koneen ja pääsin käyttöjärjestelmän live-ympäristöön.

Klo 19.52, pääsin työpöydälle, etsin ja käynnistin asennusohjelman: 
Kieleksi valitsin Amerikan Englanti, sijainniksi Suomi, näppäimistöksi Suomi sekä valitsin virtuaalilevyn jolle käyttöjärjestelmä asentuu.

![image](https://user-images.githubusercontent.com/122888655/212974834-b722b1a5-f32e-4aaf-a575-2c9a246aac03.png)


Seuraavaksi laitoin käyttäjän tiedot, joita asennusohjelma kysyi: 
![image](https://user-images.githubusercontent.com/122888655/212975509-f600bb2b-fac4-431a-b735-fa13a36e55f3.png)



Yhteenveto asetuksista: 

![image](https://user-images.githubusercontent.com/122888655/212975960-e4f69578-719f-4188-95e1-0a3e6d7ee5a3.png)

Klo 19.59, asennus alkoi.

Klo 20.06, asennus oli valmis. 

![image](https://user-images.githubusercontent.com/122888655/212977474-57649311-2e97-448a-b1ec-d21cb1aeee37.png)

## Asennuksen jälkeiset toimenpiteet

Klo 20.12, avasin selaimen, testasin hiiren/näppäimistön ja internetyhteyden toimimista. 

![image](https://user-images.githubusercontent.com/122888655/212978587-b97a438a-3ab3-41af-ad9d-77d18ae350d9.png)

Klo 20.15, kokeilin pakettien päivittämistä ja ne olivat jo valmiiksi ajan tasalla.

![image](https://user-images.githubusercontent.com/122888655/212979036-be8ec4e8-bc62-4743-8db5-f72714115d6c.png)

Samalla asensin palomuurin ja käynnistin virtuaalikoneen uudelleen:

![image](https://user-images.githubusercontent.com/122888655/212979559-7e37cb5a-cbcf-4feb-b2e1-8daa8479c888.png)


## VMware Tools-paketin asennus (VMwaren VirtualBox Guest Additionsia vastaava paketti)

Klo 20.23, virtuaalikoneen asetuksista valitsin Player --> Manage --> Install VMware Tools...

![image](https://user-images.githubusercontent.com/122888655/212980502-249dc4b3-ca24-4870-98b4-45c4a80380b4.png)

Tämä näkymä tuli ruudulle:

![image](https://user-images.githubusercontent.com/122888655/212980628-e87afd2c-077b-45dc-89ed-f42ab1eda5e5.png)

Mounttasin levyn painamalla "Mount", etsin levyn, siirsin levyn sisällön työpöydälle sekä purin tar-paketin käyttöjärjestelmän mukana tullutta Dolphin -File Exploreria käyttäen. (Työpöydällä hiiren oikean painikkeen painaminen tar-paketin päällä --> Extract --> Extract archive here)

Tämä loi kansion "vmware-tools-distrib", joka on kuvassa.

![image](https://user-images.githubusercontent.com/122888655/212992174-60719fe6-d508-46ff-945f-df7dfd2ea07d.png)


Navigoin terminaalissa oikeaan kansioon "ls" ja "cd" -komentoja käyttäen ja käynnistin asennuksen komennolla

    $ sudo ./vmware-install.pl

![image](https://user-images.githubusercontent.com/122888655/212986215-f0dd5ec9-b32d-45bc-b9ce-5f5587b7d1f2.png)

Asennusohjelma käynnistyi, annoin sen tehdä kaiken oletuskansioihin painamalla Enter tai syöttämällä Yes (riippuen kysymyksestä):


![image](https://user-images.githubusercontent.com/122888655/212986345-7b5a46fa-cfbd-4280-8a83-037ee8adc012.png)

![image](https://user-images.githubusercontent.com/122888655/212986754-d60acf10-7ff6-43dc-a3db-b6f9dace8e95.png)

![image](https://user-images.githubusercontent.com/122888655/212987670-c65a2736-a6c3-4378-a8cf-9967fdcfb164.png)


### Klo 21.05, Asennus valmistui. Nyt voi vaihtaa virtuaalikoneen resoluutiota, sekä leikata + liittää pääkoneesta:

![image](https://user-images.githubusercontent.com/122888655/212987373-fd6ff959-284a-42fb-91ae-c29b45174edc.png)

### Kaikki valmista!
