# Занятие 2: Команды IOS. Базовая конфигурация устройств
## Задачи
#### Часть 1. Проверка конфигурации коммутатора по умолчанию
#### Часть 2. Создание сети и настройка основных параметров устройства
Настройте базовые параметры коммутатора.

Настройте IP-адрес для ПК.
#### Часть 3. Проверка сетевых подключений
Отобразите конфигурацию устройства.

Протестируйте сквозное соединение, отправив эхо-запрос.

Протестируйте возможности удаленного управления с помощью Telnet.


### Часть 1 Проверка конфигурации коммутатора по умолчанию

##### Топология 1:
![](Top1.jpg)
#### [1 Настройки коммутатора по умолчанию](def1)
**24 порта FastEthernet**

**2 порта GigabitEthernet**

**Диапазоны vty: 0-4 и 5-15**

**Т.к. еще не сохранен running config:**

Switch# sh startup-config 

startup-config is not present

**SVI для VLAN1 не настроен:**

interface Vlan1

no ip address

shutdown

version 15.0 – Версия ОС
##### Топология 2:
![](Top2.jpg)

#### [Подключение к инт. fa06](Podcfa06)

**Интерфейс в работе, протокол канального уровня в работе, согласован Full-duplex, 100Mb/s**

**Содержимое флеш-каталога:**

Switch#sh flash

Directory of flash:/

1 -rw- 4670455 <no date> 2960-lanbasek9-mz.150-2.SE4.bin

64016384 bytes total (59345929 bytes free)

**Имя образа:**
  2960-lanbasek9-mz.150-2.SE4.bin


### Часть 2 Настройка базовых параметров сетевых устройств

#### [Подкдючение по Telnet и конфиг](ConfTelnet)


### Часть 3. Проверка сетевых подключений
**Настройки на PC-A:**

C:\>ipconfig

FastEthernet0 Connection:(default port)

   Connection-specific DNS Suffix..:
   
   Link-local IPv6 Address.........: FE80::20C:85FF:FE57:A145
   
   IPv6 Address....................: ::
   
   IPv4 Address....................: 192.168.1.10
   
   Subnet Mask.....................: 255.255.255.0
   
   Default Gateway.................: ::
   
                                     0.0.0.0

Bluetooth Connection:

   Connection-specific DNS Suffix..: 
   
   Link-local IPv6 Address.........: ::
   
   IPv6 Address....................: ::
   
   IPv4 Address....................: 0.0.0.0
   
   Subnet Mask.....................: 0.0.0.0
   
   Default Gateway.................: ::
   
                                     0.0.0.0

**Проверка сетевой связанности на коммутаторе S1:**

S1#ping 192.168.1.10

Type escape sequence to abort.

Sending 5, 100-byte ICMP Echos to 192.168.1.10, timeout is 2 seconds:

!!!!!

Success rate is 100 percent (5/5), round-trip min/avg/max = 0/0/1 ms
