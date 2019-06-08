# firewall

  * https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/6/html/security_guide/sect-security_guide-iptables
  * https://linux.die.net/man/8/iptables
  * https://websistent.com/how-to-save-iptables-rules-in-debian/

## iptables

### tabele / tables (-t)

| tabela    |  przeznaczenie   | 
| ------------- |:-------------| 
|   ``nat``    |   NAT / przekierowania          |
|   ``filter``    |  filtrowanie                 |
|   ``mangle``    |  modyfikacje, (ex. TTL       |

### łańcuchy / chains iptab

![input](input.svg)

![output](output.svg)

![forward](forward.svg)


| łańcuch    |  przeznaczenie   | 
| ------------- |:-------------| 
|   ``INPUT``    | kontroluje zachowanie połączeń, które przychodzą |
|   ``OUTPUT``    | do połączenia wychodzącego  |
|   ``FORWARD``    | używany do połączeń przychodzących, które nie są dostarczane lokalnie, przekierowywanie |
|   ``PREROUTING``    | zmiana miejsca dostarczania pakietów przed wysłaniem pakietów |
|   ``POSTROUTING``    | jw. po wysłaniu                        |

### co zrobić / target (-j)

|     |  przeznaczenie   | 
| ------------- |:-------------| 
|   ``ACCEPT``    |umożliwienie połączenia|
|   ``DROP``    | zerwanie połączenia |
|   ``REJECT``    | odrzucenie połączenia i odesłanie błędu |
|   ``LOG``    | szczegółowe informacje o pakietach|


### Użycie

```bash
iptables -A -i <interface> -p <protocol (tcp/udp) -s <source> --dport <port> -j <target>
```

### Przydatne informacje

```
ruch TCP
iptables -A INPUT -p tcp --dport 80 -j ACCEPT
```

```
przekierowanie jakiegokolwiek ruchu z portu 80 na port 8080:
iptables -t nat -A PREROUTING -i eth0 -p tcp --dport 80 -j REDIRECT --to-port 8080
```

```
zapis zasad do pliku
iptables-save > /etc/iptables.rules
```

```
po restarcie maszyny:
iptables-restore < /etc/iptables.up.rules
nano /etc/network/if-pre-up.d/firewall -> /sbin/iptables-restore < /etc/iptables.rules
chmod +x /etc/network/if-pre-up.d/firewall
reboot
Kolejne reguły zawsze trzeba zapisywać ręcznie używając komendy - iptables-save > /etc/iptables.rules
```


### iptables 
* -A - append - dodawanie nowych zasad
* -D - delete - usuwanie zasad
* -I - insert - wstawianie zasad do łancucha
* -R - replace - zamienienie jakiejś zasady w łańcuchu 
* -L - list - wyświetlenie wszystkich zasad w wybranym łancuchu, np nat rules iptables -t nat -n -L
* -F - flush - to sam oco usuwanie wszystkich zasad po kolei


### wykorzystanie

* Lista obecnych reguł 
  * format tabeli
  * format listy
* Czyszczenie obecnych reguł aka flush
* Domyślne zachowanie ACCEPT / DROP
* Zezwolenie na połączenie dla konkretnego portu
* NAT
  * Przekierowanie portów ip:port -> ip2:port
  * Przekierowanie portów ip:port1 -> ip2:port2

### Zadanie 
```
Notki z zajęć:
1. PC0 trzy karty - Sieć NAT, NAT, Host Only, PC1 jako udostępnianie usług
2. Podniesienie interfejsów - ip link set nazwa up 
3. iptables -S - wyświetlenie inp, outp, forw, musi być accept na inpucie. SSH musi być włączone. 
4. iptables -P INPUT DROP, iptables -A INPUT -p tcp --dport 22 -s adres -j ACCEPT
5. Zapis reguły jw. 
```

1.
   * Przygotuj konfigurację sieci gdzie ``PC0`` pełni rolę bramy NAT
   * Przygotuj konfigurację sieci gdzie ``PC1`` udostępnia usługi
   
2. * Rozbuduj konfigurację sieci dla ``PC0`` o kolejny interfejs umożliwiający komunikację z hostem ``host-only`` 
  Zabezpiecz ``PC1`` konfigurując firewall z wykorzystanie ``iptables`` tak aby zezwolicz na połącznia przychodzace
 z portem 22 (SSH) włącznie z lokalnej sieci (komputera hosta)
   * Ustaw domyślne polityki dla INPUT, OUTPUT, FORWARD kolejno, DROP, ACCEPT, ACCEPT
   * Zapisz konfigurację firewall, tak aby została odtworzona po konownym uruchomieniu maszyny
   * Zweryfikuj możliwość połączenia wykorzystując program putty (klient SSH)

3. * Skonfiguruj ``NAT`` dla PC0
   * Zweryfikuj poprawność konfiguracji dla ``PC1`` pingując dowolny adres publiczny
   * Zainstaluj serwer http ``apache`` lub ``nginx``
   * dokonaj przekierowania portów tak aby odwiedzając w przeglądarce adres w sieci ``host-only `` dla ``PC0``
     wyświetlona została strona startowa serwera zainstaloanego dla ``PC1`` 

4. * Zainstaluj program ``udp-echo-serwer`` dla ``PC1`` oraz ``udp-echo-client`` dla ``PC0``
   * skonfiguruj firewall dla ``PC1`` tak aby umożliwiał połączenia przychodzące wyłącznie dla następujacych portów
    * 80
    * 65433
   * zapewnij aby konfiguracja została załadowana po każdym uruchomieniu systemu
   * sprawdź konfigurację wykonując testowe polączenie na wskazanych wyżej portach
   * zweryfikuj brak możliwości ustanowienia połączenia na porcie 22 (SSH)
