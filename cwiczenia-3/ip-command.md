Ustawianie parametrów sieci ip
------------------------------

* stan interfejsu
    * interfejs up
    * interfejs down
* adresacja
    * dodaj adres
    * zmień adres
    * usuń adres
* routing
    * dodaj trasę default
    * dodaj trasę przez bramę
    * dodaj trasę przez interfejs
    * usuń trasę
    * zmień trasę
    * pobierz trasę dla adresu
* adresacja fizyczna
    * pokaż adresy interfejsów dostępnych w sieci
    * pokaż adresy dla konkretnego interfejsu
     


ip 
-------------------------
| subcommand    |  polecenie   | opis  |
| ------------- |:-------------| :---------------| 
|   ``addr``    |                               | infirmacje o adresacji i własnościach interfejsów |
|               |   ``ip addr``                 | informacja o wszystkich interfejsach              |
|               |   ``ip addr show dev enp0s3`` | informacja o konkretnym interfejsie               |
|   ``link``    |   ``ip link set enp0s3 up/down``             | Polecenie to służy do zmiany ustawień istniejących interfejsów (włącz/wyłącz) |
|   ``route``   | ``ip route add default via 192.168.0.1`` | Polecenie ip route służy do zarządzania tablicami routingu wewnątrz jądra. Pozwala na dodawanie, usuwanie i modyfikowanie tras. Składnia polecenia wyświetlana za pomocą polecenia `ip route help` |
|   ``maddr``   | ``ip maddr add/del/show``  | Zarządzanie rozsyłaniem adresów |
|   ``neigh``   | ``ip neigh add/del/change/show/replace -> ip neigh show to 192.168.0.0/24`` | Polecenie to służy do dodawania nowego wpisu w tablicy sąsiedztwa. Polecenie obok wyświetli tablicę sąsiedztwa dla hostów z podsieci 192.168.0.0/24 |
|   ``help``    | ``ip help`` | wyswietlenie informacji o poleceniu ip |


Przydatne rzeczy:
-------------------------

instalowanie pakietów na centosie:

``sudo yum install``

wyłączenie firewalla na centosie:

``sudo systemctl stop firewalld``

wysyłanie wiadomości na czacie:

``curl -X POST -d '{"text": "jd"}' http://{172.16.100.6}:8888/chat``

-------------------------


Zadanie
------------

![zadanie 3](cwiczenia3.svg)

1.
   * Przygotuj konfigurację sieci zgodnie z powyższym diagramem, 
   * Przetestuj połączenie poleceniem ping
   ping dla obu urządzeń (172.16.100.5 oraz .6 działa)
   ![ping](https://i.imgur.com/wXlTPax.png)
   ![konfiguracja hosta VB](https://i.imgur.com/s0m10hP.png)
   ![konfiguracja hosta w Windowsie](https://i.imgur.com/2DNALAc.png)
2.
   * Zainstaluj na komputerze ``PC1`` serwer programu ``HTTP CHAT`` dostępnego pod adresem ``https://github.com/jkanclerz/http-chat``
   * Przetestuj komunikację wysyłając wiadomość z komputera ``PC2``, upewnij się czy jest widoczna w konsoli serwera
   Serwer zainstalowałem w moim wypadku na PC2, jakoś tak wyszło (172.16.100.6)
   ![serwer na dwóch urządzeniach](https://i.imgur.com/CcDMnox.png)
3.
   * Dodaj do istniejącej sieci komputer ``PC3`` pod kontroloą systemu windows
   * Skonfiguruj ``PC3`` zgodnie z poniższym diagramem
   * Zweryfkuj połączenie korzystając z przeglądarki, odwiedzając graficzny interfejs ``HTTP CHAT`` pod adresem ``http://172.16.100.10:8888`` -> w moim wypadku ``http://172.16.100.6:8888``
   ![czat](https://i.imgur.com/Q8CuPzl.png) 
   * Przygotuj dokumentację pisemno obrazkową z wykonania zadania w formacie ``markdown`` zamieść ją w serwisie ``github.com`` obok obocnego tematu ``cwiczenia-3``

![zadanie 3.1](cwiczenia3.1.svg) 
