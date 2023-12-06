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
В веб-интерфейсе был создан сайт, мануфактура, тип устройства, функция устройства и само устройство – chr1 и chr2. Для указания IP-адресов устройств необходимо было создать интерфейсы

![изображение](https://github.com/fiji6479/2023_2024-network_programming-k34212-gomzyakov_a_n/assets/71012423/1d0ec8c1-e5d8-4f7f-947a-97e3e176a3ec)

### Сохранение всех данных из Netbox в отдельный файл ###

Установим insible модули для Netbox

![изображение](https://github.com/fiji6479/2023_2024-network_programming-k34212-gomzyakov_a_n/assets/71012423/9ff23193-904b-4ed2-bfb2-0a5399f64ea8)

Далее создадим токен который нам понадобися в будущем.

![изображение](https://github.com/fiji6479/2023_2024-network_programming-k34212-gomzyakov_a_n/assets/71012423/488e3cf0-2b0b-40e7-9b73-a0a61d7d3afa)

Теперь заполним файл netbox_conf.yml следующими данными (Здесь нам пригодится токен который мы зарнее создали)

![изображение](https://github.com/fiji6479/2023_2024-network_programming-k34212-gomzyakov_a_n/assets/71012423/82e3ef44-d57e-4792-b0b2-5ca99729dd92)

Сохраним всю информацию в файл netbox_inventory.yml с помощью команды:

![изображение](https://github.com/fiji6479/2023_2024-network_programming-k34212-gomzyakov_a_n/assets/71012423/f4551793-8492-42b0-9260-350792305986)

Проверим содержимое файла

![изображение](https://github.com/fiji6479/2023_2024-network_programming-k34212-gomzyakov_a_n/assets/71012423/392e17d5-edc6-4102-b247-3695e57dbf94)

Отредактируем файл который только что создали и перенес переменные для подключения к роутерам.

![изображение](https://github.com/fiji6479/2023_2024-network_programming-k34212-gomzyakov_a_n/assets/71012423/53564f2a-45ea-4c29-bb64-b27b06a29f55)

### Сценарий для изменения имени и IP ###
Теперь напишем playbook для изменения имени устройства и IP.

![изображение](https://github.com/fiji6479/2023_2024-network_programming-k34212-gomzyakov_a_n/assets/71012423/cdfe399c-f6dd-47d3-9a3c-24ff3458210a)

Запустим playbook с помощью следующей команды 

![изображение](https://github.com/fiji6479/2023_2024-network_programming-k34212-gomzyakov_a_n/assets/71012423/352e7e99-2b49-4771-a14b-fca54aeda147)

Как можем заметить изменения вступили в силу

CHR1:

![изображение](https://github.com/fiji6479/2023_2024-network_programming-k34212-gomzyakov_a_n/assets/71012423/771f43b1-a687-4389-9476-ba439d0b6d2c)

CHR2:

![изображение](https://github.com/fiji6479/2023_2024-network_programming-k34212-gomzyakov_a_n/assets/71012423/c65968d1-4093-411b-b397-4b4969d839ff)

### Сценарий для внесения серийного номера ###

Создадим сценарий playybook который собирает серийный номер и вносит его в netbox

![изображение](https://github.com/fiji6479/2023_2024-network_programming-k34212-gomzyakov_a_n/assets/71012423/b4d5a5f1-d221-4099-b1b9-07a929e0d946)

Запустим этот сценарий с помощью этой команды:

ansible-playbook -i inventory serial_num-playbook.yml

Проверим добавленные серийные номера

CHR1:

![изображение](https://github.com/fiji6479/2023_2024-network_programming-k34212-gomzyakov_a_n/assets/71012423/7dc4e599-0e59-4e5c-b29f-5c72d35627d3)

CHR2:

![изображение](https://github.com/fiji6479/2023_2024-network_programming-k34212-gomzyakov_a_n/assets/71012423/2d42a851-dde6-4564-8223-0ed14871eacc)

### Сеть ###

![изображение](https://github.com/fiji6479/2023_2024-network_programming-k34212-gomzyakov_a_n/assets/71012423/c47b7b8a-4d42-4b54-afd1-904a9f152c76)

## Вывод ##

В ходе выполнения лабораторной работы был настроен Netbox. В свою очередь с помощью Netbox и Ansible получилось собрать всю неоюходимую информацию, а также добавить некоторую информацию.
