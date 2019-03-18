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
|   ``addr``    |                                | informacje o adresacji i własnościach interfejsów |
|               |   ``ip addr``                  | informacja o wszystkich interfejsach              |
|               |   ``ip addr show dev enp0s3``  | informacja o konkretnym interfejsie               |
|               |    ``ip addr add/del <address> dev <maszyna>``| dodwanie/usunięcie adresu IP do maszyny |
|   ``link``    |                                | konfigurowanie włączanie i zarządzanie urządzeniami sieciowymi|                     |
|               |    ``ip link show dev enp0s3`` | wyświetlenie informacji o link maszyny |
|               |    ``ip link set enp0s3 down/up``| reset ip maszyny (WYKONAĆ)         |
|   ``chat``    |                                |                                                   |
|               |    ``cd http-chat/server/`` - pierwsza maszyna | ścieżka do serwera python         |
|               |    ``python httpchat.py`` - pierwsza maszyna   | połączenie z serwerem chatu       |
|               |    ``curl -X POST -d '{"text": "<treść wiadomości>"}' http://172.16.100.10:8888/chat`` - druga maszyna| przesyłanie wiadomości na pierwszą maszynę|
|   ``route``   | ``ip route show`` | |
|               | ``ip route get 172.16.100.50`` | podać jakiś adres i podaje, do którego go odwołuje np. 172.16.100.50 bd należeć do 172.16.100.10 |
|               |   `ip route add/del (default) via <address>  np. via 172.16.100.1      | dodanie i usunięcie adresu i przez default można ustawić domyślny adres, przez który zostają przekierowane wszystkie inne ip|
|   ``maddr``   |           |
|   ``neigh``   |  | |
|   ``help``    |  | |

Zadanie
------------

![zadanie 3](cwiczenia3.svg)

1.
   * Przygotuj konfigurację sieci zgodnie z powyższym diagramem, 
   * Przetestuj połączenie poleceniem ping
2.
   * Zainstaluj na komputerze ``PC1`` serwer programu ``HTTP CHAT`` dostępnego pod adresem ``https://github.com/jkanclerz/http-chat``
   * Przetestuj komunikację wysyłając wiadomość z komputera ``PC2``, upewnij się czy jest widoczna w konsoli serwera
3. // pamiętać o utworzeniu i ustawieniu sieci globalnej (bez fajeczek) w oraclu na obu maszynach
   * Dodaj do istniejącej sieci komputer ``PC3`` pod kontroloą systemu windows
   * Skonfiguruj ``PC3`` zgodnie z poniższym diagramem
   * Zweryfkuj połączenie kożystając z przeglądarki, odwiedzając graficzny interfejs ``HTTP CHAT`` pod adresem ``http://172.16.100.10:8888``
   * Przygotuj dokumentację pisemno obrazkową z wykonania zadania w formacie ``markdown`` zamieść ją w serwisie ``github.com`` obok obocnego tematu ``cwiczenia-3``

![zadanie 3.1](cwiczenia3.1.svg) 

https://tlk.io/sk-2019

https://s3.eu-central-1.amazonaws.com/jkan.pl/PC1.7z


