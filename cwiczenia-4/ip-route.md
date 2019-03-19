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
|               |   ``ip route add/del``             | dodaj do tablicy routingu/usun |
|               |   ``ip route show``             | pokaz tablice routingu |
|               |   ``ip route get``             | pokaz gdzie leci pakiet|


Zadanie
------------

![zadanie 4](cwiczenia4.svg)

1.
   * Przygotuj konfigurację sieci zgodnie z powyższym diagramem,
   
   ```
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
   
   cat /etc/sysctl.conf
   
   cat /proc/sys/net/ipv4/ip_forward
   
   echo 1 > cat /proc/sys/net/ipv4/ip_forward
   ```
   
   
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
  
   Konfiguracja debiana i centosa:
   * Utworzenie dwóch sieci NAT o odpowiednich adresach - ``172.168.10.0/24`` oraz ``10.0.10.0/24``
   * ``ip addr add 172.16.100.10/24 dev enp0s3``-> centos
   * ``ip addr add 10.0.10.10/24 dev enp0s3`` -> debian
   * ``ip addr add 172.16.100.1/24 dev enp0s3`` + ``ip addr add 10.0.10.1/24 dev enp0s8``-> router debian
   ![konfiguracja adresów IP](https://i.imgur.com/YiN5JJJ.png)
   * ``ip link set enp0s8 up`` -> podniesienie drugiego interfejsu w routerze
   * ``echo 1 > /proc/sys/net/ipv4/ip_forward`` - > włączenie port forwardingu w kernelu debiana
   * ![ip route show](https://i.imgur.com/wEYsprN.png)
   * ``ip route add default via 10.0.10.1 dev enp0s8``
   ![jw](https://i.imgur.com/b0ZXZMw.png)
   * ``ping 172.16.100.10 + ping 10.0.10.10``
   * ![ping](https://i.imgur.com/R4d1FYf.png)
   * ``cd http-chat/server`` -> ``python httpchat.py`` -> uruchomienie czatu
   * `` curl -X post -d '{"text" : "elo"}' http://{172.16.100.1}:8888/chat`` + `` curl -X post -d '{"text" : "elo debian here"}' http://{172.16.100.1}:8888/chat`` - komunikacja dwóch komputerów przy pomocy routera
   ![komunikacja dwoch komputerow przy pomocy routera](https://i.imgur.com/UkpMmeE.png)
   
   
  
  Obraz - > tlk.io/sk-2019
  root; 123qwe

