University: [ITMO University](https://itmo.ru/ru/)

Faculty: [FICT](https://fict.itmo.ru)

Course: [Network programming](https://github.com/itmo-ict-faculty/network-programming)

Year: 2023/2024

Group: K34212

Author: Gomzyakov Alexander Nikolaevich

Lab: Lab3

Date of create: 04.12.2023

Date of finished: 05.12.2023

# Отчет по лабораторной работе №3 "Развертывание Netbox, сеть связи как источник правды в системе технического учета Netbox" #

## Цель работы: ##
С помощью Ansible и Netbox собрать всю возможную информацию об устройствах и сохранить их в отдельном файле.

## Ход работы: ##

### Поднять Netbox на дополнительной VM ###
Для того чтобы поднять Netbox нужно первым делом установить postgreSQL

sudo apt install postgresql libpq-dev -y
sudo systemctl start postgresql
sudo systemctl enable postgresql

После этого создадим пользователя и базу данных для Netbox.

![изображение](https://github.com/fiji6479/2023_2024-network_programming-k34212-gomzyakov_a_n/assets/71012423/16bc8a52-cfc7-4a30-974b-7811772196b8)

Следующим шагом установим Redis 

![изображение](https://github.com/fiji6479/2023_2024-network_programming-k34212-gomzyakov_a_n/assets/71012423/3c34f9f8-8597-48d8-a8e3-38dda638e363)

Далее установим python.
![изображение](https://github.com/fiji6479/2023_2024-network_programming-k34212-gomzyakov_a_n/assets/71012423/117d6622-0481-48fa-916b-25e3247f6bda)

Проверим работу PostgreSQL с помощью следующий команды 

![изображение](https://github.com/fiji6479/2023_2024-network_programming-k34212-gomzyakov_a_n/assets/71012423/02ad354a-662c-4c10-8ef0-0c1f758d61c5)

Клонируем репозиторий с github netbox

![изображение](https://github.com/fiji6479/2023_2024-network_programming-k34212-gomzyakov_a_n/assets/71012423/501bd505-e379-4136-aaec-618665ccf6fa)


После этого перейдем в каталог netbox скопируем файл в котором будут находится натсрйоки конфигурации.

![изображение](https://github.com/fiji6479/2023_2024-network_programming-k34212-gomzyakov_a_n/assets/71012423/ee0201c4-b651-45d4-bfa2-6304e5047aeb)

Сгенерируем ключ кторый позже укажем в конфигурации.

![изображение](https://github.com/fiji6479/2023_2024-network_programming-k34212-gomzyakov_a_n/assets/71012423/4b094eb9-52ff-4cef-a02b-852c7d1e6b42)

Отредактируем файл configuration.py следующим образом

![изображение](https://github.com/fiji6479/2023_2024-network_programming-k34212-gomzyakov_a_n/assets/71012423/4d6053f7-16a3-4a75-a65d-82584a524c26)

После этого запустим сценарий обновления:

![изображение](https://github.com/fiji6479/2023_2024-network_programming-k34212-gomzyakov_a_n/assets/71012423/03b698a5-aa3c-4d02-b7f8-c93219d7f7c1)

Далее создадим супер пользователя с помощью следующих команд

![изображение](https://github.com/fiji6479/2023_2024-network_programming-k34212-gomzyakov_a_n/assets/71012423/2070c228-1842-4a88-af2d-20e57526303e)

Запустим netbox

![изображение](https://github.com/fiji6479/2023_2024-network_programming-k34212-gomzyakov_a_n/assets/71012423/07dd8e09-575e-459e-9a17-b0102e8762f3)

Зайдем в браузер по орпеделнной ссылке

![изображение](https://github.com/fiji6479/2023_2024-network_programming-k34212-gomzyakov_a_n/assets/71012423/d649148d-52ae-44d5-8dd6-eaae5952cb08)

Теперь авторизируемся в netbox

![изображение](https://github.com/fiji6479/2023_2024-network_programming-k34212-gomzyakov_a_n/assets/71012423/94957c27-918b-4b93-bfc3-31251d89855a)

### Заполнение информации о CHR в Netbox ###

