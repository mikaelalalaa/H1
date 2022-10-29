# H1




## x) darknet diaries ep: 53 Shadow Brokers

[Linkki jaksoon löytyy tästä!](https://darknetdiaries.com/episode/53/)

* NSA ANT catalogue vuodettiin twitteriin, tämä sisälsi listan hakkereista, exploiteista ja kybervalvonta laitteista. Esimerkiksi; 
  *   COTTONMOUTH; USB plug joka kaappaa kaikki sen läpi kulkevan datan ja lähettää tämän langattomasti.
  *   DROPOUTJEEP; Iphone puhelimeen ladattava ohjelma joka paljastaa kaikki viestit, yhteystiedot, maantieteellisen sijainnin ja pystyy avata kameran ja mikin
  *   DEITYBOUNCE; antaa takaoven pääsyn dell palvelimiin 
* Vierailijana oli Jake Williams joka on töissä Rendition Security.
* Jaksossa kerrottiin hakkeriryhmästä Shadow Brokerss, he olivat varastaneet kyber aseita NAS:alta ja olivat julkaisi joitan tiedostoja.   
  * Paljastaisivta lisää jos heille maksettaisiin. 
  * Hakkeriryhmä myös julkaisi IP-osoitteita ja lista palvelimista joita NASa on saastuttanut
  * He myös paljastivat että Jake (vierailija) on ollut töissä NAS:alla 



## a) webgoat asennus ja testaus

asensin webgoatin olemassa olevaan debian virtuaalikonelle, asennuksessa seurasin opettajamme [Teron ohjeita](https://terokarvinen.com/2020/install-webgoat-web-pentest-practice-target/).

Aloitettiin päivittämällä paketit `sudo apt-get update`. Päivityksien jälkeen asennettiin java ja ufw.

Ennen kun ruvettiin lataamaan itse webgoat niin katsottiin palomuuren asetukset `sudo ufw status verbose`, kuten kuvassa näkyy palomuuri on aktiivinen, se estää tulevan liikeneet ja sallii ulospäin menevän liikenteen.

![image](https://user-images.githubusercontent.com/93308960/198050912-417c5c9d-170f-473d-811f-9933b11866a6.png)

Sitten itse asennukseen, webgoat saatiin ladattua komennolla 
`wget https://terokarvinen.com/2020/install-webgoat-web-pentest-practice-target/webgoat-server-8.0.0.M26.jar`. Asennuksen jälkeen palvelin käynnistettiin `java -jar webgoat-server-8.0.0.M26.jar` 


![image](https://user-images.githubusercontent.com/93308960/198833486-1436b4ce-ec0a-4002-a98c-041c782175e2.png)


Testasin että asennus ja palvelimen käynnistäminen onnistui kirjoittamalla selaimeen `http://localhost:8080/WebGoat/`. Sivu näkyi ja pääsin luomaa käyttäjän.

![image](https://user-images.githubusercontent.com/93308960/198053058-38b47ac0-81ee-4383-a970-f9b2f641aa29.png)



## b) Tehtävät "HTTP Basics" ja "Developer tools"

### HTTP Basics. 

Painettiin F12 nappia jolloin avautuu selaimen Developer tool, siinä mennään network välilehdelle.
Painamalla GO näppäintä ilmestyi tiedosto `attack2`, jonka jälkeen avasin viereisessä ikkunassa `Request` välilehden josta löytyi magic number.

eli tehtävän vastaukset olivat

```
HTTP komento : POST

Magic number : 38
```
![image](https://user-images.githubusercontent.com/93308960/198056370-92420114-f4a3-4f4b-b031-df105b660ccb.png)

### Developer tools

Ensimmäinen tehtävä oli suorittaa Consolessa javasripct koodi jonka jälkeen tämä tulostaa numerosarjan `-449513090`. 

![image](https://user-images.githubusercontent.com/93308960/198060919-db064a89-1f97-4b60-811d-91046ecbffce.png)

Viimeisenä tehtävänä oli HTTP pyynnöstä randomoitu numero. Aloitettiin painamalla Go näppäintä jolloin tuli semmoinen tiedosto kun `network`. Tässä taas vastaus löytyi `Request` välilehdeltä

![image](https://user-images.githubusercontent.com/93308960/198060597-2d434e3e-9478-40c8-85b1-0638aa764bbf.png)



## c) Over The Wire: Bandit (0-2)

Tehtävissä piti ottaa ssh yhetys käyttäjään ja saada sieltä tiedostosta salasana, jonka jälken otettiin uus yhteys toiseen käyttäjään käyttämällä saatua salasanaa.


Avasin terminaalin johon kirjoitin komennon 
`ssh bandit0@bandit.labsoverthewire.org -p 2220`

![image](https://user-images.githubusercontent.com/93308960/198089117-ecd3e6d7-aadb-4c2e-9442-f63140468f0c.png)

Yhteyden saatua katsoin readme teidoston sisällön `cat readme`, joka sisälsi salasanan. 

![image](https://user-images.githubusercontent.com/93308960/198090384-c690224d-b76c-4b0f-adb6-2a380eae29d7.png)

Otin sen muistiin ja lopetin yheyden `exit` komenolla. Otin uuden ssh yhteyden toiselle käyttäjälle `ssh bandit1@bandit.labsoverthewire.org -p 2220`.  *käytettiin muistiin otettua salasanaa*

![image](https://user-images.githubusercontent.com/93308960/198833423-475e7035-7b0d-4c4a-b991-bcdae9a0704f.png)


Yhteyden muodostuksen jälkeen piti avata erikoismerkillä nimetty tiedosto, sain avattua sen komennolla `cat ./-`  
*tehtävään sain apua [stackoverflow sivustolta](https://stackoverflow.com/questions/42187323/how-to-open-a-dashed-filename-using-terminal)*


![image](https://user-images.githubusercontent.com/93308960/198092907-c225faca-5120-468a-ad7f-19727ea029ed.png)


## d) Kali linux asennus

Koneesta löytyi jo virtualbox joten mentiin suoraan asentamaan itse kali linux konetta. Asennus tapahtui netistä osoitteesta [kali](https://www.kali.org/get-kali/#kali-virtual-machines), sieltä ladattiin 7z teidosto.

![image](https://user-images.githubusercontent.com/93308960/198114507-3425b53d-cf08-458a-8416-35330dd3d48f.png)

Koska tiedosto oli 7z muodossa se piti purkaa (extract) käyttämällä 7-zip file manageria.

![image](https://user-images.githubusercontent.com/93308960/198703286-3dd173a5-b201-43e3-b5da-8312a32db019.png)


Puratun tiedoston sisältä löytyy valmis image jota klikkaamalla avautuu virtuaaliboxiin valmis kali virtuaali kone.

![image](https://user-images.githubusercontent.com/93308960/198704437-d3fdf09a-b1f8-4855-bca4-6838a92de253.png)

Sitten vaan startattiin kone, salasana ja käyttäjä löytyi netistä. Tässä vaan päivittelin paketit ja testailin että toimii.

![image](https://user-images.githubusercontent.com/93308960/198114452-f5c4ac68-29ed-4d91-90ab-f691751026c8.png)


## e) Where was this picture taken? 2/4 (2021 Challenge.fi) 

Valitsin tehtävän *Where was this picture taken? 2/4* 

Tehtävänä oli löytää mistä kyseinen kuva on otettu.

![image](https://user-images.githubusercontent.com/93308960/198121367-44c42ee5-b2f8-4577-a627-2b9d3962ac21.png)

Aloitettiin katsomalla kuvan metadataa, avaamalla kuvan `Properties -> Details välilehti`. GPS kohdasta löytyi koordinaatit jossa kuva on otettu, laitoin  koordinaatiti google mapsiin. Sain apua [Googlen](https://support.google.com/maps/answer/18539?hl=en&co=GENIE.Platform%3DDesktop) omalta sivulta miten koodrinaatit kirjotetaa.


![image](https://user-images.githubusercontent.com/93308960/198696888-2a51d11f-aae2-4e63-993d-5ba7d05a889e.png)

Varmistin vielä että osasin laittaa koordinaatit oikein avaamalla kuvan ja painamalla `alt + enter` yhdistelmää. Tarkistin että osoitteet sopivat yhteen.

![image](https://user-images.githubusercontent.com/93308960/198697037-36994299-8c09-4681-a655-496aa540ce05.png)


## lähteet

https://terokarvinen.com/2020/install-webgoat-web-pentest-practice-target/

https://stackoverflow.com/questions/42187323/how-to-open-a-dashed-filename-using-terminal

https://darknetdiaries.com/episode/53/

https://overthewire.org/wargames/

https://2021.challenge.fi/

https://support.google.com/maps/answer/18539?hl=en&co=GENIE.Platform%3DDesktop
