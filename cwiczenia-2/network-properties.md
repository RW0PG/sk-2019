Ustawianie parametrów sieci
---------------------------

![alt text][network]

[network]: ./network.png "Logo Title Text 2"

1. na 1 z komputerów zainstaluj oprogramowanie ``http-chat`` dostępne pod adresem ``https://github.com/jkanclerz/http-chat``

Wejściowe parametry sieci
-------------------------
| Parametr | wartość | komentarz(opcionalny) |
| ------------- |:-------------:| -----:|
| PC 1  | centOS  | |
| IP - address  | 192.168.56.102 | |
| MASKA  |	/24 | |
|   |  | |
| PC 2  | Debian  | |
| IP - address  | 192.168.56.103| |
| MASKA  | /24 | |

Weryfikacja połączenia

Polecenie
nmcli; ifup/down eno0s3; ip a, systemctl stop firewalld
```

Efekt
Karta sieciowa jest aktywna, nastąpiło połączenie. 
```

Statyczna konfiguracja parametrów połączenia
Wejściowe parametry sieci
-------------------------
| Parametr | wartość | komentarz(opcionalny) |
| ------------- |:-------------:| -----:|
|   PC 1 |  
| IP - address  | 192.168.10.10 | |
| MASKA  | 255.255.255.0 | |
|   |  | |
| PC 2  |  | |
| IP - address  | 172.16.100.100 | |
| MASKA  | 255.255.0.0 | |


Weryfikacja połączenia

Polecenie
```
```

Efekt
```
```

Nowa statyczna konfiguracja 

-------------------------
| Parametr | wartość | komentarz(opcionalny) |
| ------------- |:-------------:| -----:|
|   PC 1 |  
| IP - address  | | |
| MASKA  | | |
|   |  | |
| PC 2  || |
| IP - address  |  | |
| MASKA  |  | |

Weryfikacja połączenia

Polecenie
```
```

Efekt
```
```

Warto wiedzieć
--------------

su - > apt update -> apt install git
git clone https://github.com/jkanclerz/http-chat
cd /http-chat/server
python httpchat.py

-------------------------
| Parametr | wartość | komentarz(opcionalny) |
| ------------- |:-------------:| -----:|
| Lokalizacja pliku z konfiguracją sieci| cat /etc/resolv.conf  | |
| UP -> Włączenie interfejsu sieciowego|ifup enp0s3 | |
| DOWN -> Wyłączenie interfejsu sieciowego|ifdown enp0s3 | |
| Sprawdzenie obecnych parametrów |nmcli device show | |
| lista wszystkich interfejsów |ip a | |
| Które interfejsy jakie porty słuchają | netstats | |

przydatne polecenia: 
