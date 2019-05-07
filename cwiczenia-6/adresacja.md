Struktura adresu IP
-------------------

```192.168.100.192```
```255.255.255.0```

Adres sieci
-----------

1. IP + maska => BIN 
2. AND => IP, maska
3. Konwersja do DEC

Adres rozgłoszeniowy
-----------

1. Maska => NOT
2. Konwersja do DEC
3. Otrzymaną liczbę w systemie DEC dodajemy do adresu sieci. 


Podział na równą ilość podsieci
-------------------------------

```2^S >= n```

Chcemy 7 -> 2^3 >= 7

Maska -> 255.255.255.11100000 -> 255.255.255.224 -> /27


Wyznaczenie broadcastu
-------------------------------
[!img](broadcast.png)


Wprowadzenie
------------

------------------------------
| dziesiętnie |  binarnie   | 
| --------- |:-------------| 
| ``10``  | 00001010 | 
| ``92``  | 01011100 | 
| ``37``  | 00100101 | 
| ``240`` | 11110000 | 
| ``192`` | 11000000 | 
| ``255`` | 11111111 | 
| ``128`` |	10000000 | 
| ``168`` | 10101000 | 


------------------------------
| binarnie |  dziesiętnie   | 
| --------- |:-------------| 
| ``00100000``  | 32 | 
| ``11111000``  | 248 | 
| ``10100000``  | 160 | 
| ``00110000`` | 48 | 
| ``10101100`` | 172 | 
| ``01000000`` | 64 | 
| ``11111100`` | 252 | 
| ``01100010`` | 98 | 
 
Notacja CIDR
------------
 
------------------------------
| maska |  /(X) x - liczba bitów   | 
| --------- |:-------------| 
| ``255.255.255.0``   | /24 | 
| ``255.128.0.0``     | /25 | 
| ``255.255.252.0``   | /22 | 
| ``255.255.254.0``   | /23 | 
| ``255.255.255.240`` | /28 | 
| ``255.240.0.0``     | /13 | 

------------------------------
| CIDR |  Maska   | 
| --------- |:-------------| 
| ``/8``    | 255.0.0.0 | 
| ``/20``   | 255.255.240.0 | 
| ``/30``   |	255.255.255.252 | 
| ``/16``   | 255.255.0.0 | 
| ``/27``   | 255.255.255.224 | 
| ``/11``   | 255.224.0.0 | 


Liczba hostów
-------------

------------------------------
| sieć |  liczba   | 
| --------- |:-------------| 
| ``10.0.0.0/8``    |	16 777 214 | 
| ``172.16.0.0/16``   | 65 534 | 
| ``192.168.1.0/24``   | 254 | 
| ``192.168.1.0/27``   | 30 | 
| ``192.168.1.0/29``   | 6 | 
| ``192.168.1.0/31``   | 0 | 

* liczba 0 w masce?


Parametry na podstawie adresu
-----------------------------

Mając dany adres hosta i maskę znajdź:
  * adres sieci
  * początkowy adres hosta w sieci
  * liczbę hostów w zadanej podsieci ```2^(32 bity - bity maski maska) - 2 (siec i broadcast)```
  * końcowy zakres adresu hosta w sieci
  * adres rozgłoszeniowy
  
  ------------------------------
| Parametr |  wartość   | 
| --------- |:-------------| 
| ``ip``    | 192.168.1.145| 
| ``maska``   | 255.255.255.128 | 
| ``adres sieci``   |  |
| ``liczba hostów``   | |
| ``host - min``   | | 
| ``host - max``   | | 
| ``broadcast``   | | 
 
Zadanie
------------

0. Znajdz wszystkie parametry sieci dla hosta o adresie 172.16.128.64 / 16
  
------------------------------
| Parametr |  wartość   | 
| --------- |:-------------| 
| ``ip``    | | 
| ``maska``   |  | 
| ``adres sieci``   | |
| ``liczba hostów``   | |
| ``host - min``   | | 
| ``host - max``   | | 
| ``broadcast``   | | 

1.
  * Podziel sieć ```192.168.1.0``` na 16 równych podsieci
  
----------------------------------------------------------
| Adres sieci |  zakres hostów   | Adres Rozgłoszeniowy |
| --------- |:-------------|  :---------------|
| ``192.168.1.0``    | | |
| ````   | | |
| ````   | | |
| ````   | | |
| ````   | | |
| ````   | | |

2. 
  * Podziel sieć ``172.16.0.0/16`` na 6 równych podsieci.

3. 
  * Podziel sieć ``192.168.1.0/24``, tak aby każda podsieć miała 11 użytkowników.

4. 
  * Podziel sieć ``10.0.0.0/8`` na 5 podsieci. 
    * Podsieć A ma posiadać 100 000 użytkowników,
    * B – 10 000 użytkowników
    * C – 3 000 użytkowników
    * D – 500 użytkowników
    * E – 2 użytkowników.
    *
    
    
    
