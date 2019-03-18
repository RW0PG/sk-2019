Konfiguracja route
------------------

* routing
    * dodaj trasę default
    * dodaj trasę przez bramę
    * dodaj trasę przez interfejs
    * usuń trasę
    * zmień trasę
    * pobierz trasę dla adresu
     
ip 
-------------------------
| subcommand    |  polecenie   | opis  |
| ------------- |:-------------| :---------------| 
|   ``route``    |                               | |
|               |   ``ip route add``             | |


Zadanie
------------

![zadanie 4](cwiczenia4.svg)

1.
   * Przygotuj konfigurację sieci zgodnie z powyższym diagramem,
   
   tutorial step by step:
   
   
   ip addr add 172.16.100.10/24 dev enp0s3
   
   ip addr add 10.0.10.10/24 dev enp0s3
   
   3 maszyna na obu NATach - lan1 i lan2
   
   ip addr 172.168.100.1/24 dev enp0s3
   
   ping 172.16.100.10
   
   ip addr 10.0.10.1/24 dev enp0s8
   
   ip link set enp0s8 up
   
   PC3 -> ping 172.16.100.10
   
   ip route show
   
   ip route add default via 10.0.10.1 dev enp0s3
   
   ip route get 10.0.10.15 / 8.8.8.8
   
   * Przetestuj połączenie pomiędzy wszystkimi elementami sieci
   * Dlaczego połączenie może nie działać
2. Przygotuj konfigurację tak aby została załadowana poprawnie po ponownym uruchomieniu systemu
   * Patrz ``utrwalanie statycznej konfiguracji cwiczenia 2``
   * zwróć uwagę na różnice pomiędzy dydtrybucjami systemu
3. Zainstaluj, uruchom i przetestuj działanie aplikacji ``HTTP_CHAT``
   * aplikacja dostępna w serwisie github ``https://github.com/jkanclerz/http-chat``

Zadanie do domu
---------------

1. Przygotuj konfigurację z zadania 1 wykorzystując inny system operacyjny na komputerze pełniącym rolę routera.
  * debian -> centos lub centos -> debian
  * zapewnij poprawną komunikację pomiędzy PC3 -> PC1
  
  Obraz - > tlk.io/sk-2019
  root; 123qwe
