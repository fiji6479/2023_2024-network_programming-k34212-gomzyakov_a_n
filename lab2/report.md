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
![изображение](https://github.com/fiji6479/2023_2024-network_programming-k34212-gomzyakov_a_n/assets/71012423/b00fc165-f971-4be7-8caa-244aa6c57471)
