# Raportti 3, Vapaus (Tiistai 24.01.2023)

### OS: Windows 11 Pro 22H2
### Virtualisointi: VMware Workstation 17 Player
### Host-tietokone: Intel i7-6700 @ 3.40GHz, 16GB DDR4, NVIDIA GTX 970
### VM: 4GB RAM, 2 prosessoriydintä



## x) Rise of Open Source ja FSF Free Software Definition -artikkelien tiivistäminen (klo. 17.55)

- Vapaan ohjelmiston käyttäjillä on oikeus mm. muokata, jakaa, opiskella, käyttää ja kopioida ohjelmistoa haluamallaan tavalla. 
- Vapaan ohjelmiston kulmakivenä toimii neljä vapautta. Vapaus käyttää ohjelmistoa, vapaus jakaa ohjelmistoa (myös mahdolliset itse muokkaamat kopiot) sekä mahdollisuus lukea ja opiskella ohjelmiston toimivuutta sekä lähdekoodia. 
- Vapaa ohjelmisto voi olla kaupallista, mutta sen ei tarvitse olla. 



## a) Kolmen ohjelman lisenssit (klo 18.10)

### Neofetch: MIT-Lisenssi
Lisenssi löytyy projektin GitHub -sivulta. MIT-Lisenssi on vapaa, ja se antaa oikeuden muokata ja käyttää koodia vapaasti kunhan lisenssiteksti säilytetään.

![image](https://user-images.githubusercontent.com/122888655/214345837-0dedbd4e-dfde-4c1e-a3e3-b3c33af662df.png)


### CMatrix: GPL 3.0 -Lisenssi
Lisenssi löytyy projektin GitHub -sivulta. GPL 3.0 on vapaa, ja se antaa oikeuden muokata ja käyttää koodia vapaasti, kunhan mahdolliset johdannaiset lisensoidaan samalla tavalla. 

![image](https://user-images.githubusercontent.com/122888655/214345773-a43b39db-d904-456b-bb84-3d9c8a0410b6.png)


### Htop: GPL 2.0 -Lisenssi
Lisenssi löytyy projektin GitHub -sivulta. GPL 2.0 on vapaa, ja se antaa oikeuden muokata ja käyttää koodia vapaasti, kunhan mahdolliset johdannaiset lisensoidaan samalla tavalla. 

![image](https://user-images.githubusercontent.com/122888655/214345712-9f654642-509b-4823-8a46-fb65fb1a1b88.png)

## b) Säännöllistä (klo 14.00 Torstai 26.1)

Loin tekstitiedoston, johon kirjoitin pienen määrän sisältöä.

![image](https://user-images.githubusercontent.com/122888655/214832027-775fcdda-97a4-4758-aa36-67121b7e01a6.png)

Komennolla    

    $ grep -P ^lau lauri.md

saadaan palautettua vain sanat, jotka alkavat kirjamilla "lau". "-P" -lippu komennossa tarkoittaa että käytössä on Perlin säännölliset lausekkeet.

![image](https://user-images.githubusercontent.com/122888655/214832742-23717241-d421-4ff2-9817-b620ddc613e0.png)

Komento 

      $ grep -P lauri[0-9] lauri.md 
      
palauttaa ne merkkijonot, joissa on "lauri" ja myös numero 0-9 perässä.

![image](https://user-images.githubusercontent.com/122888655/214833797-1fcbc5b6-bc01-49dc-9fac-ba8ef63f25aa.png)





## c) Pipe (klo. 14.28)

Putkien käyttö Linuxissa tarkoittaa sitä, että putken seuraava komento ottaa syötteekseen edellisen komennon tulosteen.

Putkella                        
            
    $ cat lauri.md | grep -P "k...." | wc -l
    
Tulostuu tiedoston sisältö, joka menee edelleen grep:lla säännöllisten lausekkeiden vertailun kautta "wc -l" -komennolle, joka tulostaa kuinka monta riviä komennosta tuli ulos. 

![image](https://user-images.githubusercontent.com/122888655/214839226-3750dae2-b127-4b7f-9b5e-e269ab2c1d08.png)

## Tiivistelmä, Valmista (klo. 14.48)

Raportissa katsoin edellisen tehtävän ohjelmien lisenssejä, kokeilin hieman grep-komentoa regexin kanssa sekä näytin hieman pipejä.

## Lähteet 

https://snyk.io/learn/what-is-gpl-license-gplv3-explained/

https://www.gnu.org/philosophy/free-sw.html

http://lib.tkk.fi/Diss/2005/isbn9529187793/isbn9529187793.pdf

https://www.cyberciti.biz/faq/grep-regular-expressions/

https://www.geeksforgeeks.org/perl-regex-cheat-sheet/
