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

