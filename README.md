# ****Построение сети с помощью Cisco Packet Traiser****

## Настройка IP адресации компьютеров и подключение к коммутатору

Такая схема используется когда необходимо произвести подключение нескольких PC между собой с помощью коммутатора в локальной сети.

Для настройки сети и ее демонстрации необходима  программа Cisco Packet Traicer.

Для начала необходимо выбрать нужное количество ПК и Switch 2960

![ufw](https://github.com/PopChop88/PopChop88-Networking-with-Cisco-Packet-Tracer/blob/main/pic/1.png?raw=true)


Подключение производится с помощью кабеля Copper-Straight-Through от порта FastEthernet0 на ПК до порта FastEthernet0/..на коммутаторе.

![ufw](https://github.com/PopChop88/PopChop88-Networking-with-Cisco-Packet-Tracer/blob/main/pic/2.png?raw=true)

В итоге должно получится такое соединение PC со Switch

![ufw](https://github.com/PopChop88/PopChop88-Networking-with-Cisco-Packet-Tracer/blob/main/pic/3.png?raw=true)

**Настройка IP адрессации**

На PC заходим во вкладку `Desktop`, далее `IP configuration`
![ufw](https://github.com/PopChop88/PopChop88-Networking-with-Cisco-Packet-Tracer/blob/main/pic/4.png?raw=true)
![ufw](https://github.com/PopChop88/PopChop88-Networking-with-Cisco-Packet-Tracer/blob/main/pic/5.png?raw=true)

Далее необходимо вписать IPv4, Subnet Mask, Default Gateway.
![ufw](https://github.com/PopChop88/PopChop88-Networking-with-Cisco-Packet-Tracer/blob/main/pic/6.png?raw=true)

В этом примере должно получится так
![ufw](https://github.com/PopChop88/PopChop88-Networking-with-Cisco-Packet-Tracer/blob/main/pic/7.png?raw=true)

Теперь добавляем еще один Switch и 2 сервера. Каждому серверу, по аналогии с PC, присваивается IP адрес.

![ufw](https://github.com/PopChop88/PopChop88-Networking-with-Cisco-Packet-Tracer/blob/main/pic/8.png?raw=true)

После настройки необходимо отправить `ping` на каждый хост

****Настройка динамической ip-адресации, DHCP, DNS, WEB серверов****

Для настройки DCHP необходимо:

* Добавить сервер
* Дать ему имя "Serv-DCHP"
* Открыть вкладку `Service`
* В графе `DCHP` ввести следующие данные:
```
Default Geteway: 192.168.99.1
DNS Server: 192.168.33.61
Start IP Address: 192.168.33.2
Subnet Mask: 255.255.255.0
Maximum Number of User: 20
```
Далее сохраняем настройки и включаем сервер.

![ufw](https://github.com/PopChop88/PopChop88-Networking-with-Cisco-Packet-Tracer/blob/main/pic/10.png?raw=true)

Следующий шаг это настройка динамического адреса на PC. Для это открываем вкладку `ip configuration` и меняем `static` на `DHСP`
![ufw](https://github.com/PopChop88/PopChop88-Networking-with-Cisco-Packet-Tracer/blob/main/pic/12.png?raw=true)
Необходимо немного подождать пока сервер распределит IP адресс на PC, после чего появится сообщение `DHCP request successful`.

Для настройки DNS необходимо:
* Добавить сервер
* Изменить имя сервера на `Serv-DNS`
* Открыть вкладку `Service`
* В графе `DNS` ввести следующие данные:
```
Name: cisco.com
Address: 192.168.33.60
```
* Сохранить настройки и включить сервер

![ufw](https://github.com/PopChop88/PopChop88-Networking-with-Cisco-Packet-Tracer/blob/main/pic/13.png?raw=true)

![ufw](https://github.com/PopChop88/PopChop88-Networking-with-Cisco-Packet-Tracer/blob/main/pic/14.png?raw=true)

**Настройка WEB сервера**

Для настройки WEB необходимо:
* Добавить сервер
* Изменить имя сервера на `Serv-WEB`
* Открыть вкладку `Service`
* В графе `HTTP` проверить данные
![ufw](https://github.com/PopChop88/PopChop88-Networking-with-Cisco-Packet-Tracer/blob/main/pic/15.png?raw=true)

В итоге у нас получается такая схема в которой необходимо проверить все хосты командой `ping` и зайти с помощью встроенного браузера на PC на web-ресурс
![ufw](https://github.com/PopChop88/PopChop88-Networking-with-Cisco-Packet-Tracer/blob/main/pic/16.png?raw=true)
![ufw](https://github.com/PopChop88/PopChop88-Networking-with-Cisco-Packet-Tracer/blob/main/pic/17.png?raw=true)
