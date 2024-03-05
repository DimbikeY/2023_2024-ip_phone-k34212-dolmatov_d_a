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

Перейдем к установке MicroSIP
![Добавление](https://github.com/DimbikeY/2023_2024-ip_telephony-k34212-dolmatov_d_a/blob/main/lab3/pictures/%D0%A1%D0%BD%D0%B8%D0%BC%D0%BE%D0%BA%20%D1%8D%D0%BA%D1%80%D0%B0%D0%BD%D0%B0%202024-03-05%20105400.png)  

Проверим, что аккаунт 1002 подключился к порту
![Добавление](https://github.com/DimbikeY/2023_2024-ip_telephony-k34212-dolmatov_d_a/blob/main/lab3/pictures/%D0%A1%D0%BD%D0%B8%D0%BC%D0%BE%D0%BA%20%D1%8D%D0%BA%D1%80%D0%B0%D0%BD%D0%B0%202024-03-05%20105412.png)  

Совершим звонок, чтобы проверить связность  
![Связность](https://github.com/DimbikeY/2023_2024-ip_telephony-k34212-dolmatov_d_a/blob/main/lab3/pictures/%D0%A1%D0%BD%D0%B8%D0%BC%D0%BE%D0%BA%20%D1%8D%D0%BA%D1%80%D0%B0%D0%BD%D0%B0%202024-03-05%20105418.png)  

Связность работает!
### Вывод
В результате выполнения данной лабораторной работы были изучены основы подключения ip-телефонов в Asterisk с помощью ZoiPer5, MicroSIP. Локальную связность обеспечила Asterisk для софт-телефонов.
