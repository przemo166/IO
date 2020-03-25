# Kurs IO LAB , rok akademicki 2019/20 .

|  Temat projektu : | Stacja pogodowa  |
| :------------: | :------------: |
|  Autorzy :  |  Przemys�aw Widz , Oskar Wi�ckowicz   |
| Prowadz�cy :  | Mgr inz. Wojciech Tarnawski  |
|  Data oddania :  | 14.01.2020r.  |
|  Termin zaj�� :   |  PIATEK/TP 14:30 - 17:30 | 

![Zdj�cie projektu ](projekt.png "fig:") [fig:my~l~abel]

Za�o�enia projektowe
====================

Celem projektu by�o stworzenie prostej stacji pogodowej, powiadamiaj�cej
u�ytkownika o nast�puj�cych informacjach :

1.  bie��cy czas i data

2.  temperatura powietrza pochodz�ca z dw�ch osobnych czujnik�w

3.  ci�nienie atmosferyczne

4.  wilgotno�� powietrza

Do stacji pomiarowej dodano r�wnie� modu� Bluetooth umo�liwiaj�cy zdalne
wysy�anie bie��cych danych z czujnik�w na komputer lub smartfon.

U�yte elementy
==============

![Zdj�cia element�w u�ytych do projektu ](elementy.png "fig:")
[fig:my~l~abel]

**Do przygotowania stacji pogodowej u�yto nast�puj�cych element�w :**

-   **Klon Arduino Uno** (do wst�pnego projektu na p�ytce stykowej)

    Arduino Uno to popularna p�ytka z mikrokontrolerem ATmega328 z
    rodziny AVR wyposa�ony w 14 cyfrowych wej��/wyj�� z czego 6 mo�na
    wykorzysta� jako wyj�cia PWM oraz 6 analogowych wej��.

-   **Klon Arduino Nano** (do projektu ko�cowego)

    Arduino Nano to popularna wersja Uno w mniejszym rozmiarze: 45 x 18
    mm. P�ytka zawiera mikrokontroler ATmega328 wyposa�ony w 22 cyfrowe
    wej�cia/wyj�cia z czego 6 mo�na wykorzysta� jako wyj�cia PWM oraz 8
    jako wej�cia analogowe.

-   **Wy�wietlacz LCD 2x20**

    Popularny wy�wietlacz 2 x 20 znak�w pod�wietlany w kolorze
    niebieskim.

-   **Czujnik temperatury i wilgoci DHT22**

    Czujnik temperatury i wilgotno�ci powietrza z interfejsem cyfrowym,
    jednoprzewodowym. Zakres pomiarowy: temperatura -40 do 80 �C,
    wilgotno�� 0-100 %RH.

-   **Modu� bluetooth HC-05**

    Modu� Blootooth v2.0 + EDR klasa 2. Pracuje z napi�ciem 3,3 V,
    komunikuje si� poprzez interfejs szeregowy UART (piny RX, TX),
    wspiera komendy AT. Maksymalna moc nadajnika wynosi + 4 dBm, czu�o��
    odbiornika to - 85 dBm. Modu� Bluetooth pozwala na po��czenie
    dowolnego urz�dzenia z telefonem, smartfonem, tabletem lub innym
    urz�dzeniem bezprzewodowo.

-   **Czujnik ci�nienia atmosferycznego i temperatury BMP280**

    Modu� z cyfrowym barometrem firmy Bosch BMP180. Zakres pomiarowy
    wynosi od 200 do 1100 hPa z dokonano�ci� 0,02 hPa. Zasilany jest
    napi�ciem z zakresu 1,8 - 3,6 V.

-   **Zegar czasu rzeczywsitego RTC DS1307**

    Modu� z zegarem czasu rzeczywistego i rezerwowym zasilaniem
    bateryjnym, kt�re ma na zadanie podtrzymanie pracy zegara po zaniku
    g��wnego zasilania uk�adu. Pozwala na odczyt czasu w postaci
    godziny, minuty i sekundy oraz daty: miesi�c, dzie�, rok.
    Interfejsem komunikacyjnym jest magistrala I2C.

-   **Potencjometr 10k**

    Rezystor nastawny, kt�ry dzia�a na zasadzie klasycznego dzielnika
    napi�cia. Typowym zastosowaniem potencjometr�w jest regulacja pr�du
    lub napi�cia w urz�dzeniach elektrycznych. W tym przypadku zosta�
    u�yty do regulacji kontrastu w wy�wietlaczu LCD.

-   **Bateria 9V**

    Bateria u�yta do samodzielnego zasilania stacji pogodowej.

Dzia�anie stacji pogodowej
==========================

Stacja pogodowa dokonuje pomiar�w wilgotno�ci, temperatury, ci�nienia
atmosferycznego oraz czasu. Nast�pnie wyniki pomiar�w pokazywane s� na
wy�wietlaczu LCD oraz przesy�ane przez bluetooth na telefon lub komputer
i wy�wietlane na nich za pomoc� aplikacji Bluetooth Terminal.

Wy�wietlanie danych na wy�wietlaczu odbywa si� co dwie sekundy, w
kolejno�ci zgodnej z p�tl� g��wn� programu :

-   temperatury (z obu czujnik�w)

-   ci�nienie i wilgotno��

-   data i czas

Zatem czas trwania p�tli to 6 sekund (3 x 2 sekundy), zako�czone
wys�aniem danych na komputer lub smartfon.

![Przyk�adowy cykl pracy wy�wietlacza ](cykl.PNG "fig:") [fig:my~l~abel]

![Przesy� danych na komputer (z lewej) oraz telefon (z prawej)
](lol.PNG "fig:") [fig:my~l~abel]

Przebieg realizacji projektu
============================

Prototyp stacji pogodowej by� realizowany na p�ytce stykowej przy pomocy
Arduino Uno. Budowe stacji pogodowej zacz�to od pod�aczenia czujnik�w do
Arduino oraz stworzenia programu obs�uguj�cego je. Nastepnie dodany
zosta� wy�wietlacz LCD, na kt�rym zosta�y wy�wietlone dane pomiarowe.
Kolejnym etapem by�a realizacja komunikacji bezprzewodowej przy pomocy
modu�u bluetooth oraz zasilanie z baterii. Nast�pnie, gdy prototypowa
stacja pogodowa dzia�a�a poprawnie, zamieniono Ardunino Uno na Arduino
Nano w celu zaoszcz�dzenia miejsca na uniwersalnej p�ytce PCB, do kt�rej
przylutowane zosta�y wszystkie elementy.

Podczas realizacji projektu napotkano kilka problem�w. Jednym z nich by�
niedzia�aj�cy wy�wietlacz LCD, na kt�rym mia�y by� wy�wietlane dane
pomiarowe. Okaza�o si�, �e z��cza m�skie dzi�ki, kt�rym mozna umie�ci�
wy�wietlacz na p�ytce stykowej nie by�y do niego przylutowane przez co
jaki� element nie styka�. W pierwotnym projekcie bezprzewodowa
komunikacja stacji pogodowej mia�a by� realizawana za pomoc� wifi.
Zakupiono wi�c modu� ESP8266, jednak napotkano problemy, kt�rych nie
uda�o si� rozwi�za�. W efekcie bezprzewodow� komunikacj� zrealizowano
przy pomocy modu�u bluetooth HC-05, kt�ry pozwala przesy�a� dane na
telefon. Dane odebrane ze stacji pogodowej wy�wietlane s� w aplikacji
Bluetooth Terminal.

Arduino zapewnia gotowe biblioteki przez co programowanie
mikrokontrolera jest programowaniem wysokopoziomowym, a co za tym idzie
du�o przyjemniejszym i prostszym. Ka�dy modu� u�yty w projekcie mia�
swoje dedykowane biblioteki, dzi�ki czemu w kodzie �r�d�owym pos�ugiwano
si� obiektami gotowych klas.

Schemat po��cze�
================

![Schemat po��cze� element�w stacji pogodowej ](schemat.jpg "fig:")
[fig:my~l~abel]

Kosztorys projektu
==================

1.  Arduino Nano klon - **21.00 z�**

2.  P�ytka uniwersalna �U-11� - **element z laboratorium**

3.  Czujnik DHT22 - **22.00 z�**

4.  Wy�wietlacz LCD - **17.50 z�**

5.  Czujnik BMP280 - **12.00 z�**

6.  Rezystor 10k - **0.05 z�**

7.  Zegar czasu rzeczywistego RTC DS1307 - **11.60 z�**

8.  Bateria 9V - **5.00 z�**

9.  Modu� bluetooth HC-05 - **22.30 z�**

10. Potencjometr - **3.00 z�**

**Ca�kowity koszt stacji pogodowej - 114.45 z�**\

Wnioski
=======

-   Budowa stacji pogodowej jest czasoch�onnym zaj�ciem. Ma�y b��d mo�e
    kosztowa� nawet kilka godzin pracy. Jednak podczas realizacji tego
    projektu mo�na si� nauczy� wiele praktycznych rzeczy z dziedziny
    elektroniki i programowania.

-   Najtrudniejszym etapem okaza�a si� realizacja odpowiednich po��cze�
    elektrycznych pomiedzy poszczeg�lnymi elementami stacji pogodowej.
    Natomiast najprostszym etapem by�o programowanie.

-   Por�wnuj�c koszt zbudowania stacji pogodowej z cen� takiego
    urz�dzenia zakupionego w sklepie elektronicznym mo�na doj�� do
    wniosku, �e czasami warto jest zrealizowa� jaki� projekt samemu i
    zaoszcz�dzi� pieni�dze. Koszt stacji wyni�s� 114,45z�, gdzie w
    sklepie elektronicznym trzeba zap�aci� �rednio 150z�. Zamawiaj�c
    elementy do budowy stacji z Chin, a nie od Polskich po�rednik�w,
    mo�na by by�o zaoszcz�dzi� jeszcze wi�cej.


