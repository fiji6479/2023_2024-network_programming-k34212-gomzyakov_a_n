University: [ITMO University](https://itmo.ru/ru/)

Faculty: [FICT](https://fict.itmo.ru)

Course: [Network programming](https://github.com/itmo-ict-faculty/network-programming)

Year: 2023/2024

Group: K34212

Author: Gomzyakov Alexander Nikolaevich

Lab: Lab4

Date of create: 06.12.2023

Date of finished: 07.12.2023

# Отчет по лабораторной работе №4 "Базовая 'коммутация' и туннелирование используя язык программирования P4" #

## Цель работы: ##
Изучить синтаксис языка программирования P4 и выполнить 2 задания обучающих задания от Open network foundation для ознакомления на практике с P4.

## Ход работы: ##

### Подготовка среды ###

Первым делом проверим что установлен vagrant и Virtualbox

![изображение](https://github.com/fiji6479/2023_2024-network_programming-k34212-gomzyakov_a_n/assets/71012423/1a6554c0-db19-4e4d-8d65-330066e0bb4f)

Далее склонируем репозиторий p4lang/tutorials

![изображение](https://github.com/fiji6479/2023_2024-network_programming-k34212-gomzyakov_a_n/assets/71012423/a3c21538-b21b-4850-af63-361353fa1ac0)

Запустим vagrant с помощью команды vagrant up

![изображение](https://github.com/fiji6479/2023_2024-network_programming-k34212-gomzyakov_a_n/assets/71012423/a4c48178-93b6-426d-9159-a12428a7ab58)

![изображение](https://github.com/fiji6479/2023_2024-network_programming-k34212-gomzyakov_a_n/assets/71012423/959210a3-d3c9-4465-8862-539948169e1c)

### Implementing Basic Forwarding ###
В первой части работы нужно было дополнить скрипт на P4, который реализует базовую переадресацию с использованием следующей топологии:

![изображение](https://github.com/fiji6479/2023_2024-network_programming-k34212-gomzyakov_a_n/assets/71012423/d2750c20-ea40-4569-9013-adac11c22cb9)

Первым делом запустим mininet в папке заданий с помощью команды make run

![изображение](https://github.com/fiji6479/2023_2024-network_programming-k34212-gomzyakov_a_n/assets/71012423/77ca764f-8345-4330-8290-c79966a6464a)

С помощью команды pingall проверим связь устройств

![изображение](https://github.com/fiji6479/2023_2024-network_programming-k34212-gomzyakov_a_n/assets/71012423/b4b9a817-7fb6-4409-baed-9e972c37f6cb)

Как можем заметить ни один пинг не проходит

![изображение](https://github.com/fiji6479/2023_2024-network_programming-k34212-gomzyakov_a_n/assets/71012423/2b5bf92f-a77f-432d-9c28-ef2570235545)

Чтобы исправить это ошибку нужно впервую очередь почистить логи с помощью следующих команд чтобы не возникло ошибок в будущем

exit 

make stop

make clean

Теперь нужно исправить код basic.p4. Для того чтобы код заработал нужно добавить логику парсера:

![изображение (142)](https://github.com/fiji6479/2023_2024-network_programming-k34212-gomzyakov_a_n/assets/71012423/26ca0cd3-591c-4da1-925e-b4c5563acb28)
![изображение (144)](https://github.com/fiji6479/2023_2024-network_programming-k34212-gomzyakov_a_n/assets/71012423/b97c7e6e-bc78-48e9-ba7b-b04669848f8d)

Далее было необходимо дописать логику для входящих пакетов и объединения их в пакет. Для этого добавим код в action и apply

Дополнение кода action для установления порта выхода для следующего узла, обновления MAC-адреса назначения Ethernet, обновления MAC-адрес источника ethernet на адрес коммутатора и уменьшения TTL. 

![изображение (145)](https://github.com/fiji6479/2023_2024-network_programming-k34212-gomzyakov_a_n/assets/71012423/79e7b320-4925-4b53-89ab-2735a5fd2d3f)

Теперь добавим логику проверки правильности ipv4 заголовка

![изображение](https://github.com/fiji6479/2023_2024-network_programming-k34212-gomzyakov_a_n/assets/71012423/850bf36f-b80f-41d5-8621-cf07aeda57de)

Осталось только дописать deparser который будет сформировывать пакет из заголовка

![изображение](https://github.com/fiji6479/2023_2024-network_programming-k34212-gomzyakov_a_n/assets/71012423/e91c6a45-4937-4524-b5d7-5585bae96ddf)

Проверим правильно ли мы все сделали с помощью команды pingall в mininet

![изображение](https://github.com/fiji6479/2023_2024-network_programming-k34212-gomzyakov_a_n/assets/71012423/19394939-5b9f-4f33-a99f-eddfde7e7310)

Как можем заметить все пинги проходят успешно, следовательно мы сделали все правильно

### Implementing Basic Tunneling ###
