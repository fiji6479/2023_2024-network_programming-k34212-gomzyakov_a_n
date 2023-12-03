University: [ITMO University](https://itmo.ru/ru/)

Faculty: [FICT](https://fict.itmo.ru)

Course: [Network programming](https://github.com/itmo-ict-faculty/network-programming)

Year: 2023/2024

Group: K34212

Author: Gomzyakov Alexander Nikolaevich

Lab: Lab1

Date of create: 02.12.2023

Date of finished: 03.12.2023

# Отчет по лабораторной работе №2 "Развертывание дополнительного CHR, первый сценарий Ansible" #

## Цель работы: ##
С помощью Ansible настроить несколько сетевых устройств и собрать информацию о них. Правильно собрать файл Inventory.

## Ход работы: ##

### Установка второго CHR на компьютере ###
Первым делом скаем тот же самый образ RouterOS и поменяем UUID на новом образес помощью консольной команды

C:\>"C:\Program Files\Oracle\VirtualBox\VBoxManage.exe" internalcommands sethduuid "C:\Users\skist\Downloads\chr-7.12.1.vdi(1)\chr-7.12.1.vdi" 

### OVPN Client на втором CHR ###
После этого проедлаем те же действия как и в первой лабораторной работе и получим следующий результат

![изображение](https://github.com/fiji6479/2023_2024-network_programming-k34212-gomzyakov_a_n/assets/71012423/0187f297-5470-4558-9085-f2165977b3af)

### Используя ansible настроим CHR на двух ВМ ###
Первым делом установим библиотеку для работы ansible-ssh c помощью следующий команды:

![изображение](https://github.com/fiji6479/2023_2024-network_programming-k34212-gomzyakov_a_n/assets/71012423/790e0653-1079-47dd-926b-8adde6e0d34b)

После этого узнаем IP CHR и проверим подключения с помощью ssh.
![изображение](https://github.com/fiji6479/2023_2024-network_programming-k34212-gomzyakov_a_n/assets/71012423/bd5f08fe-f907-46c5-a0e3-0c0c0c41750f)

Следующим дейтсвием создадим файл hosts.ini 

![изображение](https://github.com/fiji6479/2023_2024-network_programming-k34212-gomzyakov_a_n/assets/71012423/5b78ea21-1245-4537-bb86-5784d8aea6a4)

Далее проверим работу этого файла

![изображение](https://github.com/fiji6479/2023_2024-network_programming-k34212-gomzyakov_a_n/assets/71012423/7b82ebe2-3cc0-4fe7-ba7a-4f9b79e4f424)

Теперь создадим ansible-playbook файл с командами для настройки конфигураций.
![изображение](https://github.com/fiji6479/2023_2024-network_programming-k34212-gomzyakov_a_n/assets/71012423/496a58c0-52ee-4e21-8d22-5a4933546ee6)

Проверим работу с помощью следующей команды: 

![изображение](https://github.com/fiji6479/2023_2024-network_programming-k34212-gomzyakov_a_n/assets/71012423/47668831-fc23-4bf4-ad8f-d741d87391b4)
![изображение](https://github.com/fiji6479/2023_2024-network_programming-k34212-gomzyakov_a_n/assets/71012423/d4a9f499-0232-4970-9715-e169d4cb847e)

### Проверка работы на CHR ###
Результаты пингов проверки локальной связности:

![изображение](https://github.com/fiji6479/2023_2024-network_programming-k34212-gomzyakov_a_n/assets/71012423/f3f14bf8-4113-4a55-89e2-5f5cf29b43d0)

Созданные на машинах пользователи и NTP Clients

ВМ1:

![изображение](https://github.com/fiji6479/2023_2024-network_programming-k34212-gomzyakov_a_n/assets/71012423/b2a03992-47ba-4928-bfe9-8b41e8506d4d)

ВМ2:

![изображение](https://github.com/fiji6479/2023_2024-network_programming-k34212-gomzyakov_a_n/assets/71012423/116e1c7e-a5cc-443b-8dc1-047f39a95b74)

проверка OSPF

ВМ1:

![изображение](https://github.com/fiji6479/2023_2024-network_programming-k34212-gomzyakov_a_n/assets/71012423/df102484-4abd-434d-8a3a-300009befc94)

ВМ2:

![изображение](https://github.com/fiji6479/2023_2024-network_programming-k34212-gomzyakov_a_n/assets/71012423/cd263caa-5c76-466d-ada6-84d8f2313551)
