University: [ITMO University](https://itmo.ru/ru/)  
Faculty: [FICT](https://fict.itmo.ru)  
Course: [IP-telephony](https://itmo-ict-faculty.github.io/ip-telephony/)   
Year: 2023/2024  
Group: K34212  
Author: Dolmatov Dmitrii Alexeevich  
Lab: Lab1  
Date of create: 06.02.2023  
Date of finished: --.02.2023  

# Лабораторная работ №1 "Базовая настройка ip-телефонов в среде Сisco packet trace"  
## Описание  
Для выполнения данной лабораторной работы собирается схема соединения. Необходимо проверить, правильно ли подключены и настроены все узлы устройств  
## Цель работы  
Изучить рабочую среду Cisco Packet Tracer, ознакомить- ся с интерфейсами основных устройств, типами кабелей, научиться собирать топологию. Изучить построение сети IP-телефонии с помощью маршрутизатора, коммутатора и IP телефонов Cisco 7960 в среде Packet tracer  
### Ход работы  
#### 1-ая часть  
Выполним базовую настройку L2 switch to PCs. PC -> Switch через mode access vlan NN  
Switch -> Switch через mode trunk encapsulation vlan NN,YN,ZN...  

Результаты связности представлены ниже:  
Вид схемы: ![Вид схемы](https://github.com/DimbikeY/2023_2024-ip_telephony-k34212-dolmatov_d_a/blob/main/lab1/screens/Снимок%20экрана%202024-02-06%20212229.png)  

Связность VLAN10:  ![VLAN10](https://github.com/DimbikeY/2023_2024-ip_telephony-k34212-dolmatov_d_a/blob/main/lab1/screens/Снимок%20экрана%202024-02-06%20212319.png)  
Связность VLAN20:  ![VLAN20](https://github.com/DimbikeY/2023_2024-ip_telephony-k34212-dolmatov_d_a/blob/main/lab1/screens/Снимок%20экрана%202024-02-06%20212334.png)  

##### Особенность
Нужно задавать VLAN на всех L2 switch, через которых будут пробегаться пакеты VLANов: **Switch 6 & Switch 7** имеют в show vlan и 10, и 20 метки VLAN 

#### 2-ая часть:

