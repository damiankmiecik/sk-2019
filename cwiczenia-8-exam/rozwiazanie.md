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

całość została przetestowana komendą ``ping google.pl`` wyegzekwowaną na PC1 i PC2
