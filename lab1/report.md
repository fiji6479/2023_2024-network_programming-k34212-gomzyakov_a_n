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

Как можем заметить на рисунке ниже, виртуальная машина запущена

![изображение](https://github.com/fiji6479/2023_2024-network_programming-k34212-gomzyakov_a_n/assets/71012423/6f3cacdf-5dbd-48cd-bb92-07884fd71a01)


Попробуем к ней подключиться с помощью команды ssh admin@158.160.58.60

![изображение](https://github.com/fiji6479/2023_2024-network_programming-k34212-gomzyakov_a_n/assets/71012423/cc6a61e7-80f8-4552-8564-2db148846d40)

### Создание виртуальной машины RouterOS и подключение к ней через winbox ###
Первым делом скачем образ RouterOS с официального сайта MikroTik и установим его с помощью virtualbox

![изображение](https://github.com/fiji6479/2023_2024-network_programming-k34212-gomzyakov_a_n/assets/71012423/42ab814c-cf6d-4a2f-a3db-4a8b96d066fd)

Далее настроим сетевой мост

![изображение](https://github.com/fiji6479/2023_2024-network_programming-k34212-gomzyakov_a_n/assets/71012423/9cada01c-2e45-401e-82de-e54f4ce7435c)

После этого запустим нашу виртуальную машину 

![изображение](https://github.com/fiji6479/2023_2024-network_programming-k34212-gomzyakov_a_n/assets/71012423/29824f76-b969-4331-a64e-1cd9fcd65130)

Теперь с помощью winbox подключимся к CHR (используя логин, пароль, MAC-адрес)

![изображение](https://github.com/fiji6479/2023_2024-network_programming-k34212-gomzyakov_a_n/assets/71012423/0fa80880-d35c-4554-8c91-d831b3370b54)

Подключение произошло успешно 

![изображение](https://github.com/fiji6479/2023_2024-network_programming-k34212-gomzyakov_a_n/assets/71012423/407182e5-1d46-40c4-b10c-72387cf5dcda)

### Настройка VPN сервера ###
