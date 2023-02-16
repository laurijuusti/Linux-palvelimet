# Raportti 9, Sequel (Torstai 16.02.2023)

### OS: Windows 11 Pro 22H2
### Virtualisointi: VMware Workstation 17 Player
### Host-tietokone: Intel i7-6700 @ 3.40GHz, 16GB DDR4, NVIDIA GTX 970
### VM: 4GB RAM, 2 prosessoriydintä

## a) Yrityssoftaa (klo 19.10)

 - Amazonin EC2 Cloud computing -palvelu
 - Nettisivut joissa on login -toiminto, kuten vaikkapa GitHub


## b) Postgren asennus (19.20)

![image](https://user-images.githubusercontent.com/122888655/219441693-2db28247-8132-4332-be79-c63de8969e88.png)

Asensin ja käynnistin Postgren komennoilla 

    $ sudo apt upgrade, sudo apt install postgresql, sudo systemctl start postgresql
    
Tämän jälkeen loin uuden tietokannan ja käyttäjän komennoilla 


    $ sudo -u postgres createuser lauri1, sudo -u postgres createdb lauri1
    

![image](https://user-images.githubusercontent.com/122888655/219443911-8f2f73f2-2f3e-4350-a627-37a64699f410.png)

Toimii!

## c) CRUD (19.35)

Avasin Postgren komennolla 'psql', ja loin uuden tablen nimeltä 'students' komennolla

     $  CREATE TABLE students (id SERIAL PRIMARY KEY, name VARCHAR(200));
     
Katsoin taulua komennolla '\d students'

![image](https://user-images.githubusercontent.com/122888655/219445876-ae399f14-2596-406c-b204-b90580122592.png)

En saanut tauluun merkkijonoja jostain syystä, se hyväksyi vain lukuja mutta lisäsin tauluun hieman dataa.


![image](https://user-images.githubusercontent.com/122888655/219447646-cbf1f0b2-0950-466a-bf5e-c530f8c1c950.png)

Data on taulussa!

![image](https://user-images.githubusercontent.com/122888655/219447853-32bc3d2b-aa5c-4158-9ad9-5d77e16328d7.png)

Datan päivittäminenkin toimi!

![image](https://user-images.githubusercontent.com/122888655/219449456-ece8812e-a2a5-4b68-bd19-0d176e29cc4a.png)

Myös datan poistaminen toimii!

![image](https://user-images.githubusercontent.com/122888655/219450190-78428852-042c-4c51-b6c9-cfcab300da82.png)

## Tiivistelmä, Valmista (klo 20.05)

Kerroin kaksi esimerkkiä palveluista jotka toimivat selaimessa, joissa on tietokanta ja koodi pyörii palvelimella. Asensin Postgren ja kokeilin CRUD-toimintoja (Create, Read, Update, Delete)

## Lähteet 

https://terokarvinen.com/2023/linux-palvelimet-2023-alkukevat/#h9-sequel

https://terokarvinen.com/2016/03/03/install-postgresql-on-ubuntu-new-user-and-database-in-3-commands/

https://terokarvinen.com/2016/03/05/postgresql-install-and-one-table-database-sql-crud-tutorial-for-ubuntu/

https://blog.knoldus.com/lets-have-a-look-at-the-postgresql-crud-operation/
