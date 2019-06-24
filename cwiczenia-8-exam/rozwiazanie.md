Zadanie 1
---------

1. Zaprojektuj oraz przygotuj prototyp rozwiązania z wykorzystaniem oprogramowania ``VirtualBox`` lub podobnego. 
Zaproponuj rozwiązanie spełniające poniższe wymagania:
   * Usługodawca zapewnia domunikację z siecią internet poprzez interfejs ``eth0`` ``PC0``
   * Zapewnij komunikację z siecią internet na poziomie ``LAN1`` oraz ``LAN2``
   * Dokonaj takiego podziału sieci o adresie ``172.22.128.0/17`` aby w ``LAN1`` można było zaadresować ``500`` adresów natomiast w LAN2 ``5000`` adresów    
   * Przygotuj dokumentację powyższej architektury w formie graficznej w programie ``DIA``
 
Rozwiązanie
-----------

PC0  
-------------------
|  interfejs   | adres  |
|:-------------| :------| 
| eth3 | internet od usługodawcy  |
| eth8 | 172.22.128.1/23  |
| eth9 | 172.22.160.1/19  |

PC1  
----------------
|  interfejs   | adres  |
|:-------------| :------| 
| eth3 | 172.22.128.2/23 |


PC2  
------------------
|  interfejs   | adres  |
|:-------------| :------| 
| eth3 | 172.22.160.2/19 |


użyte komendy: </br>
``ip addr add *** dev ***`` - PC0, PC1, PC2 </br> 
``ip link set *** up`` - PC0 </br>
``ip route add default via *** dev ***`` </br>
``echo 1 > /proc/sys/net/ipv4/ip_forward`` / ``sysctl -w net.ipv4.ip_forward=1``</br>
``iptables -t nat -A POSTROUTING -s *** -o *** -j MASQUERADE`` </br>

*** - ip/nazwa

Całość została przetestowana komendą ``ping google.pl``na wszystkich PC.

Podział sieci: </br></br>
172.22.128.0/17 </br></br>
Aby otrzymać 500 podsieci, należy pożyczyć z części hosta 2n >= 500, n = 9, czyli 17+9 = 26 </br>
255.255.11111111.10000000 </br>
255.255.255.128 </br>
2^7-2 hostów, czyli 126 hostów </br>

|Nr podsieci    |     Adres podsieci    |          Zakres hostów                     |           Broadcast         |
|---------------|-----------------------|--------------------------------------------|-----------------------------|
|     1         |   172.22.128.0/26     |   172.22.128.1 - 172.22.128.126            |          172.22.128.127     |
|     2         |   172.22.128.128/26   |   172.22.128.129 - 172.22.128.254          |          172.22.128.255     |
|     3         |   172.22.129.0/26     |   172.22.129.1 - 172.22.129.126            |          172.22.129.127     |




