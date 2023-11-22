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

![изображение](https://github.com/fiji6479/2023_2024-network_programming-k34212-gomzyakov_a_n/assets/71012423/51d2f00a-350b-4cac-89a5-5c287ed79e0a)

Попробуем к ней подключиться с помощью команды ssh admin@62.84.114.36

![изображение](https://github.com/fiji6479/2023_2024-network_programming-k34212-gomzyakov_a_n/assets/71012423/6f91674f-3317-4557-9a43-0401984a0dca)

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

Первым делом установим pyhton и ansible для виртуальной машины ubuntu
Для этого пропишем команды:

sudo apt-get update \
sudo apt install python3-pip \
ls -la /usr/bin/python3.6 \
sudo pip3 install ansible

![изображение](https://github.com/fiji6479/2023_2024-network_programming-k34212-gomzyakov_a_n/assets/71012423/2fd04302-0392-4330-8a90-d418772cd598)

Далее для создания VPN сервера воспользуемся набором инструментов OpenVPN Access Server.
Для этого выполним следующие команды: 

sudo apt update && apt -y install ca-certificates wget net-tools gnupg \

wget https://as-repository.openvpn.net/as-repo-public.asc -qO /etc/apt/trusted.gpg.d/as-repository.asc \
echo "deb [arch=amd64 signed-by=/etc/apt/trusted.gpg.d/as-repository.asc] http://as-repository.openvpn.net/as/debian jammy main">/etc/apt/sources.list.d/openvpn-as-repo.list \
apt update && apt -y install openvpn-as

![изображение](https://github.com/fiji6479/2023_2024-network_programming-k34212-gomzyakov_a_n/assets/71012423/e7662b97-2881-49d4-bb7b-6be9f32b4caf)

Мы получили сообщение с логином и паролем, теперь зайдем по ссылке https://62.84.114.36:943/admin

![изображение](https://github.com/fiji6479/2023_2024-network_programming-k34212-gomzyakov_a_n/assets/71012423/c47fb662-7358-4bc5-b037-cd0f344dea9d)

Укажем в настройках TCP

![изображение](https://github.com/fiji6479/2023_2024-network_programming-k34212-gomzyakov_a_n/assets/71012423/31f0e8ec-96f0-4c26-ac4d-ad71392c4b25)

Отключим TLS

![изображение](https://github.com/fiji6479/2023_2024-network_programming-k34212-gomzyakov_a_n/assets/71012423/7a53bc85-2de8-4eee-bab0-146adfe69562)

Теперь в User Permission создадим нового пользователя и разрешим атоматический вход

![изображение](https://github.com/fiji6479/2023_2024-network_programming-k34212-gomzyakov_a_n/assets/71012423/1c375314-1d8c-432d-99d0-252d44255e2d)

Далее в User Profile создадим новый профайл и скачиваем его.

![изображение](https://github.com/fiji6479/2023_2024-network_programming-k34212-gomzyakov_a_n/assets/71012423/1a1ebf6a-603d-4263-9683-1a57fef78cf7)

### Донастройка CHR ###

Откроем установленное приложение WinBox и добавим ранее загруженный файл.

![изображение](https://github.com/fiji6479/2023_2024-network_programming-k34212-gomzyakov_a_n/assets/71012423/b71eb9ff-e78b-4621-80a4-a34e1ac5a30d)

Теперь с помощью терминала импортируем сертификат из файла

![изображение](https://github.com/fiji6479/2023_2024-network_programming-k34212-gomzyakov_a_n/assets/71012423/aca7290a-33bf-4a83-a3b1-3dc60bea3dac)

После этого создадим interface со следующими натсройками

![изображение](https://github.com/fiji6479/2023_2024-network_programming-k34212-gomzyakov_a_n/assets/71012423/773ed1a9-b681-43d2-869e-1276dab29658)

Теперь проверим работу сервера используя команду ping со внутренним ip-адресом (10.128.0.24)

![изображение](https://github.com/fiji6479/2023_2024-network_programming-k34212-gomzyakov_a_n/assets/71012423/8a306378-ec00-4395-91e8-8a7823111279)

## Вывод ##

В результате выполнения лабораторной работы были получены навыки по развертыванию виртуальной машины на платформе Yandex Cloud. Также был установлен CHR в VirtualBox и настроен VPN туннель между сервером и клиентом.
