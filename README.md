# H1




## x) darknet diaries






## a) webgoat asennus ja testaus

asensin webgoatin olemassa olevaan debian virtuaalikonelle, asennuksessa seurasin opettajamme [Teron ohjeita](https://terokarvinen.com/2020/install-webgoat-web-pentest-practice-target/).

Aloitettiin päivittämällä paketit `sudo apt-get update`. Päivityksien jälkeen asennettiin java ja ufw.

Ennen kun ruvettiin lataamaan itse webgoat niin katsottiin palomuuren asetukset `sudo ufw status verbose`, kuten kuvassa näkyy palomuuri on aktiivinen, se estää tulevan liikeneet ja sallii ulospäin menevän liikenteen.

![image](https://user-images.githubusercontent.com/93308960/198050912-417c5c9d-170f-473d-811f-9933b11866a6.png)

Sitten itse asennukseen, webgoat saatiin ladattua komennolla `wget https://terokarvinen.com/2020/install-webgoat-web-pentest-practice-target/webgoat-server-8.0.0.M26.jar`

![image](https://user-images.githubusercontent.com/93308960/198555854-38851ac1-dbbf-424b-816c-f3f682b7bd30.png)



Testasin että asennus onnistui kirjoittamalla selaimeen `http://localhost:8080/WebGoat/` ja pääsin kirajutumaan sivulle.

![image](https://user-images.githubusercontent.com/93308960/198053058-38b47ac0-81ee-4383-a970-f9b2f641aa29.png)








## b) Tehtävät "HTTP Basics" ja "Developer tools"

Tein ensiksi tehtävän HTTP Basics. Tässä oli tarkoitus tutustua 


![image](https://user-images.githubusercontent.com/93308960/198056370-92420114-f4a3-4f4b-b031-df105b660ccb.png)



![image](https://user-images.githubusercontent.com/93308960/198058501-cfab93f9-75a2-4703-9fa8-94eaff9eb68c.png)


![image](https://user-images.githubusercontent.com/93308960/198060597-2d434e3e-9478-40c8-85b1-0638aa764bbf.png)


![image](https://user-images.githubusercontent.com/93308960/198060919-db064a89-1f97-4b60-811d-91046ecbffce.png)


![image](https://user-images.githubusercontent.com/93308960/198058394-fc4c21c4-6749-4900-9dde-0d81a86073d6.png)


## c) Over The Wire: Bandit (0-2)

Tehtävissä piti ottaa ssh yhetys käyttäjään ja saada sieltä tiedostosta salasana, jonka jälken otettiin uus yhteys toiseen käyttäjään.


Avasin terminaalin johon kirjoitin komennon `ssh bandit@bandit.labsoverthewire.org -p 2220`

![image](https://user-images.githubusercontent.com/93308960/198089117-ecd3e6d7-aadb-4c2e-9442-f63140468f0c.png)

Yhteyden saatua katsoin readme teidoston sisällön `cat readme`, joka sisälsi toisen käyttäjän salasanan. 

![image](https://user-images.githubusercontent.com/93308960/198090384-c690224d-b76c-4b0f-adb6-2a380eae29d7.png)

Otin muistiin salasanan ja lopetin yheyden `exit` komenolla. Otin uuden ssh yhteyden toiselle käyttäjälle `ssh bandit1@bandit.labsoverthewire.org -p 2220` ja salasanana toimi muistiin otettu salasana. 

![image](https://user-images.githubusercontent.com/93308960/198090455-b49b54f0-a927-4261-bc4a-4b017ccf0656.png)


Yhteyden muodostuksen jälkeen piti avata erikoismerkillä nimetty tiedosto, sain avattua sen komennolla `cat ./-`


![image](https://user-images.githubusercontent.com/93308960/198092907-c225faca-5120-468a-ad7f-19727ea029ed.png)


## d) Kali linux asennus

Koneesta löytyi jo virtualbox joten mentiin suoraan asentamaan itse kali linux konetta. Asennus tapahtui netistä osoitteesta [kali](https://www.kali.org/get-kali/#kali-virtual-machines), sieltä ladattiin 7z teidosto.

![image](https://user-images.githubusercontent.com/93308960/198114507-3425b53d-cf08-458a-8416-35330dd3d48f.png)

Koska tiedosto oli 7z muodossa se piti purkaa (extract) käyttämällä 7-zip file manageria.

![image](https://user-images.githubusercontent.com/93308960/198703286-3dd173a5-b201-43e3-b5da-8312a32db019.png)


Puratun tiedoston sisältä löytyy valmis image jota klikkaamalla avautuu virtuaaliboxiin valmis kali virtuaali kone.

![image](https://user-images.githubusercontent.com/93308960/198704437-d3fdf09a-b1f8-4855-bca4-6838a92de253.png)



![image](https://user-images.githubusercontent.com/93308960/198114452-f5c4ac68-29ed-4d91-90ab-f691751026c8.png)

## e) Where was this picture taken? 2/4 (2021 Challenge.fi) 


![image](https://user-images.githubusercontent.com/93308960/198120197-67191197-bf8a-4722-9457-6307868050a6.png)



![image](https://user-images.githubusercontent.com/93308960/198696888-2a51d11f-aae2-4e63-993d-5ba7d05a889e.png)


![image](https://user-images.githubusercontent.com/93308960/198697037-36994299-8c09-4681-a655-496aa540ce05.png)



![image](https://user-images.githubusercontent.com/93308960/198121367-44c42ee5-b2f8-4577-a627-2b9d3962ac21.png)

Blackpool Tower, Englanti


