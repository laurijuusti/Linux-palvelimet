# Raportti 13, Hello world! (Tiistai 7.3.2023)

### OS: MacOS 12.6.3 Monterey
### Virtualisointi: UTM 4.1.6 (https://mac.getutm.app)
### Host-tietokone: M1 MacBook Pro 13"
### VM: 2GB RAM


## a) Käännä "Hei maailma" kolmelle kielelle (klo 20.14)

### Python

Navigoin työpöydälle, loin uuden tiedoston nimeltä heimaailma.py johon lisäsin sisällön

    $ print('Hei maailma!')
    
Tallensin tiedoston, ja suoritin sen komennolla 

    $ python3 heimaailma.py
    
Ohjelma tulosti sisällön terminaaliin onnistuneesti.

<img width="406" alt="image" src="https://user-images.githubusercontent.com/122888655/223514084-fa00d114-2cfe-4102-bbbc-29203b0b8db4.png">

### Java

Tein työpöydälle toisen tiedoston nimeltä heimaailma.java johon lisäsin sisällön

    $ public class heimaailma
    $ {
    $ public static void main(String[] args)
    $ { System.out.println("Hei maailma!");
    $ }
    $ }
    
Tämän jälkeen yritin suorittaa tiedoston javalla, mutta se ei toiminut. Java ei näköjään ollut asennettuna tietokoneelle, joten jouduin asentamaan sen komennoilla:

    $ sudo apt update & sudo apt get default-jre
    
Tämän jälkeen suorittaminen onnistui komennolla 

    $ java heimaailma.java

<img width="394" alt="image" src="https://user-images.githubusercontent.com/122888655/223517323-6dffa5ad-cd44-4e6c-9919-035732aa4f48.png">


### Golang

Asensin aluksi kielen virtuaalikoneelle komennolla:

    $ sudo apt install golang-go
    
Asennuksen jälkeen loin tiedoston heimaailma.go, johon lisäsin sisällöksi 

    $ package main
    $ import "fmt"
    $ func main () {
    $ fmt.Println("Hei maailma!")
    $ }
    
Tämän jälkeen suoritin sovelluksen komennolla:

    $ go run heimaailma.go
   
Sain terminaaliin seuraavan vastauksen:

<img width="394" alt="image" src="https://user-images.githubusercontent.com/122888655/223519938-990a1ae4-2944-43d8-b413-ffcc8cd203a7.png">

### Greetme (klo. 14.00 torstaina 9.3)

Loin python -tiedoston 'greetme.py', johon lisäsin koodin

    $ import sys
    $ print (f"Hello, {sys.argv[1]}")
    
Kokeilin koodin suorittamista, ja se toimii.

<img width="425" alt="image" src="https://user-images.githubusercontent.com/122888655/224018571-936ac38f-4917-4304-8d25-5beb1c2fae93.png">

<img width="289" alt="image" src="https://user-images.githubusercontent.com/122888655/224018637-42231bfa-7b9e-4d16-8373-72ff23f3a1aa.png">


## Tiivistelmä, lähteet (klo. 14.08, torstaina 9.3)

Raportissa tein kolmella ohjelmointikielellä 'Hei maailma' -sovellukset, sekä Pythonilla greetme -sovelluksen.

Lähteet:

https://terokarvinen.com/2018/hello-python3-bash-c-c-go-lua-ruby-java-programming-languages-on-ubuntu-18-04/ (Pääartikkeli)

https://www.digitalocean.com/community/tutorials/how-to-install-java-with-apt-on-debian-11 (Javan asennus)

https://www.geeksforgeeks.org/command-line-arguments-in-python/ (Command line parametrit Pythonissa)
