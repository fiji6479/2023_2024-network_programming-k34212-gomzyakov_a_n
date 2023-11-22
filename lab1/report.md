University: [ITMO University](https://itmo.ru/ru/)

Faculty: [FICT](https://fict.itmo.ru)

Course: [Network programming](https://github.com/itmo-ict-faculty/network-programming)

Year: 2023/2024

Group: K34212

Author: Gomzyakov Alexander Nikolaevich

Lab: Lab1

Date of create: 18.11.2023

Date of finished: 22.11.2023

# Отчет по лабораторной работе №1 "Установка CHR и Ansible, настройка VPN" #

## Цель работы: ##
Развертывание виртуальной машины на базе Cloud.Yandex c установленной системой контроля конфигураций Ansible. Установка CHR в virtualbox.

## Ход работы: ##

### Создание виртуальной машины Ubuntu в Yandex.cloud ###
Первым делом создадим виртуальную машину со следующими параметрами:
![изображение](https://github.com/fiji6479/2023_2024-network_programming-k34212-gomzyakov_a_n/assets/71012423/c69f88e4-e54e-4ee9-abfd-949d8b6533f7)

![изображение](https://github.com/fiji6479/2023_2024-network_programming-k34212-gomzyakov_a_n/assets/71012423/afeae0d4-ad06-444f-886a-71449c86b2ea)

Для того чтобы создать и скопировать ssh-ключ воспользуемся двумя командами:
ssh-keygen -t ed25519 


type C:\Users\skist\.ssh\id_ed25519.pub | clip

![изображение](https://github.com/fiji6479/2023_2024-network_programming-k34212-gomzyakov_a_n/assets/71012423/9c24f515-bf49-42ec-aa78-beeaca2e72a9)


