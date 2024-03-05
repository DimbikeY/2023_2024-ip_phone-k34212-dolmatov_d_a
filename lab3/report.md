University: [ITMO University](https://itmo.ru/ru/)  
Faculty: [FICT](https://fict.itmo.ru)  
Course: [IP-telephony](https://itmo-ict-faculty.github.io/ip-telephony/)   
Year: 2023/2024  
Group: K34212  
Author: Dolmatov Dmitrii Alexeevich  
Lab: Lab3  
Date of create: 04.03.2023  
Date of finished: --.03.2023  

# Лабораторная работ №3 "Конфигурация voip в среде Сisco packet trace"  
## Описание  
Для выполнения данной лабораторной работы необходимо выполнить настройку Asterisk.  
## Цель работы  
Изучить программный комплекс Asterisk. Настройка Asterisk для локальных звонков.  
### Ход работы  
#### SIP 
Был установлен Asterisk, который используется для локальных звонков  
![Установка](https://github.com/DimbikeY/2023_2024-ip_telephony-k34212-dolmatov_d_a/blob/main/lab3/pictures/%D0%A1%D0%BD%D0%B8%D0%BC%D0%BE%D0%BA%20%D1%8D%D0%BA%D1%80%D0%B0%D0%BD%D0%B0%202024-03-05%20103103.png)  

Далее были настроены sip.conf и extensions.conf для добавления SIP-аккаунта и связи между ними  
![Связи](https://github.com/DimbikeY/2023_2024-ip_telephony-k34212-dolmatov_d_a/blob/main/lab3/pictures/%D0%A1%D0%BD%D0%B8%D0%BC%D0%BE%D0%BA%20%D1%8D%D0%BA%D1%80%D0%B0%D0%BD%D0%B0%202024-03-05%20103805.png)  

![Связи](https://github.com/DimbikeY/2023_2024-ip_telephony-k34212-dolmatov_d_a/blob/main/lab3/pictures/%D0%A1%D0%BD%D0%B8%D0%BC%D0%BE%D0%BA%20%D1%8D%D0%BA%D1%80%D0%B0%D0%BD%D0%B0%202024-03-05%20103819.png)  

После этого выполним перезагрузку Asterisk для применения настроек изменений  
![Перезагрузка](https://github.com/DimbikeY/2023_2024-ip_telephony-k34212-dolmatov_d_a/blob/main/lab3/pictures/%D0%A1%D0%BD%D0%B8%D0%BC%D0%BE%D0%BA%20%D1%8D%D0%BA%D1%80%D0%B0%D0%BD%D0%B0%202024-03-05%20103900.png)  

Далее, установим ZoiPer для добавления софт-телефона  
![Сайт](https://github.com/DimbikeY/2023_2024-ip_telephony-k34212-dolmatov_d_a/blob/main/lab3/pictures/%D0%A1%D0%BD%D0%B8%D0%BC%D0%BE%D0%BA%20%D1%8D%D0%BA%D1%80%D0%B0%D0%BD%D0%B0%202024-03-05%20104310.png)  

![Сайт](https://github.com/DimbikeY/2023_2024-ip_telephony-k34212-dolmatov_d_a/blob/main/lab3/pictures/%D0%A1%D0%BD%D0%B8%D0%BC%D0%BE%D0%BA%20%D1%8D%D0%BA%D1%80%D0%B0%D0%BD%D0%B0%202024-03-05%20105336.png)  

В качестве hostname укажем адрес localhost: 127.0.0.1  

Проверка того, что порт 1001 добавлен для ZoiPer

Стоит напомнить, что в DHCP интерфейс и сабинтерфейсы выключены по умолчанию  
Скрипт для настройки DHCP сервера  

> ip dhcp excluded-address 192.168.20.1 192.168.20.10  
> ip dhcp pool VOICE_POOL  
> network 192.168.20.0 255.255.255.0  
> default-router 192.168.20.10  
> option 150 ip 192.168.20.10  

Команда option 150 ip 192.168.20.10 используется в сетях VoIP (Voice over IP) для настройки DHCP-сервера на предоставление клиентам информации о том, где они могут найти серверы TFTP (Trivial File Transfer Protocol), которые используются для загрузки конфигурационных файлов для IP-телефонов 
То же самое сделаем и для 10-влана  

Далее перейдем к настрйоке ip-телефоном на роутере 

> telephony-services
> max-dn 3 (кол-во номеров макс)
> max-ephones (кол-во телефонов макс)
> ip source-address 192.168.20.10 port 2000 (тот же, что и сабинтерфейс роутера)

Далее настраиваем телефоны по очереди:  

> ephone-dn 1  
> number 1010  
> exit  
> ephone 1  
> type 7960 (всегда так)  
> button 1:1 (заранее должно быть DHCP соединение с оконечными устройствами)  
> и так делаем с каждым телефоном, меняя button 1:N, где N - номер устройства

В результате выполнения данной лабораторной работы были изучены основы подключения ip-телефоном (не забываем команду switchport voice vlan NN), а также изучен материал по использованию роутера с DHCP сервером, который одновременно является сервером TFTP для корректной связности IP-телефонов.  

Отключение поиска по DNS: ![Поиск](https://github.com/DimbikeY/2023_2024-ip_telephony-k34212-dolmatov_d_a/blob/main/lab2/screens/Снимок%20экрана%202024-02-19%20234904.png)  

Установка пароля на сетевые устройства: ![Пароль](https://github.com/DimbikeY/2023_2024-ip_telephony-k34212-dolmatov_d_a/blob/main/lab2/screens/Снимок%20экрана%202024-02-19%20235152.png)  

Проверка связности: ![Связность](https://github.com/DimbikeY/2023_2024-ip_telephony-k34212-dolmatov_d_a/blob/main/lab2/screens/Снимок%20экрана%202024-02-19%20235847.png)  

### 2-ая часть
В принципе, часть этой работы схожа с прошлой. Только вместо этого у нас добавляется ещё один VLAN: это компьютеры  
Сама конфигурация особо не отличилась: на коммутаторе добавим 
> switchport mode access
> switchport access vlan 10 (PC)
> switchport voice vlan 20 (Voice)
Также установим DHCP Pool как для ПК, так и для телефонов
Остальная конфигурация не изменяется
Проверка работы DHCP: ![DHCP](https://github.com/DimbikeY/2023_2024-ip_telephony-k34212-dolmatov_d_a/blob/main/lab2/screens/Снимок%20экрана%202024-02-20%20004046.png)

Проверка связности: ![Связность](https://github.com/DimbikeY/2023_2024-ip_telephony-k34212-dolmatov_d_a/blob/main/lab2/screens/Снимок%20экрана%202024-02-19%20235847.png)  

Схема: ![Схема](https://github.com/DimbikeY/2023_2024-ip_telephony-k34212-dolmatov_d_a/blob/main/lab2/screens/Снимок%20экрана%202024-02-20%20003238.png)  

## Вывод  
В результате выполнения данной лабораторной работы были изучены основы подключения ip-телефоном (не забываем команду switchport voice vlan NN), а также изучен материал по использованию роутера с DHCP сервером, который одновременно является сервером TFTP для корректной связности IP-телефонов.

