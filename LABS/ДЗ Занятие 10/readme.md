# Занятие 10 Лабораторная работа. Настройка IPv6-адресов на сетевых устройствах. 

### Топология:

![](T1.png)

### Таблица адресации

![](Tab1.png)

## Задачи
* Часть 1. Настройка топологии и конфигурация основных параметров маршрутизатора и коммутатора
* Часть 2. Ручная настройка IPv6-адресов
* Часть 3. Проверка сквозного соединения
## Часть 1 Настройка топологии и конфигурация основных параметров маршрутизатора и коммутатора.
### Шаг 1. Настройка маршрутизатора.
#### Назначить имя хоста и настройте основные параметры устройства.
#### Выполнение команд на маршрутизаторе:
* Router(config)#hos
* Router(config)#hostname R1
* R1(config)#no ip domain-lookup
* R1(config)#do wr
* Building configuration...
* [OK]
* R1(config)#
#### Выполнение команды R1#sh run
#### [Конфигурация маршрутизатора R1](ConfR1)
### Шаг 2. Настройка коммутатора.
#### Назначение имени хоста и настройка основных параметров устройства.
#### Выполнение команд на коммутаторе:
* Switch(config)#hostname S1
* S1(config)#
* S1(config)#no ip domain-lookup
* S1(config)#do wr
* Building configuration...
* [OK]
* S1(config)#
#### Выполнение команды S1#sh run
#### [Конфигурация коммутатора S1](ConfS1)
## Часть 2. Ручная настройка IPv6-адресов.
### Шаг 1. Назначьте IPv6-адреса интерфейсам Ethernet на R1.
#### a.	Назначьте глобальные индивидуальные IPv6-адреса, указанные в таблице адресации обоим интерфейсам Ethernet на R1.
#### Выполнение команд на R1:
* R1(config)#int gi0/0/0
* R1(config-if)#ipv6 add 2001:db8:acad:a::1/64
* R1(config-if)#int gi0/0/1
* R1(config-if)#ipv6 add 2001:db8:acad:1::1/64
#### b.	Введите команду show ipv6 interface brief, чтобы проверить, назначен ли каждому интерфейсу корректный индивидуальный IPv6-адрес.
#### Выполнение команды R1(config-if)#do sh ipv6 int br на R1:
* GigabitEthernet0/0/0       [administratively down/down]
*    FE80::201:C7FF:FE54:3A01
*    2001:DB8:ACAD:A::1
* GigabitEthernet0/0/1       [administratively down/down]
*    FE80::201:C7FF:FE54:3A02
*    2001:DB8:ACAD:1::1
* GigabitEthernet0/0/2       [administratively down/down]
*    unassigned
* Vlan1                      [administratively down/down]
*    unassigned
#### Выполнение команды R1(config-if)#do sh int gi0/0/0 на R1:
* GigabitEthernet0/0/0 is administratively down, line protocol is down (disabled)
* Hardware is ISR4331-3x1GE, address is 0001.c754.3a01 (bia 0001.c754.3a01)
#### Выполнение команды R1(config-if)#do sh int gi0/0/1 на R1:
* GigabitEthernet0/0/1 is administratively down, line protocol is down (disabled)
* Hardware is ISR4331-3x1GE, address is 0001.c754.3a02 (bia 0001.c754.3a02)
#### Отображаемые локальные адреса канала основаны на адресации EUI-64, которая автоматически использует MAC-адрес интерфейса для создания 128-битного локального IPv6-адреса канала.
#### c.	Чтобы обеспечить соответствие локальных адресов канала индивидуальному адресу, вручную введите локальные адреса канала на каждом интерфейсе Ethernet на R1.
#### Выполнение команд на R1:
* R1(config)#int gi0/0/1
* R1(config-if)#ipv6 add fe80::1 link-local

* R1(config-if)#int gi0/0/0
* R1(config-if)#ipv6 add fe80::1 link-local
