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
Проведём в этом задании возможность связи по ip-телефонии.  
Для этого нам необходим Router, на котором будет настроен DHCP сервер, необходимый для того, чтобы к IP-телефонам передался ip-адрес и номер телефона  

Стоит напомнить, что в DHCP интерфейс и сабинтерфейсы выключены по умолчанию
Скрипт для настройки DHCP сервера
> ip dhcp excluded-address 192.168.1.1 192.168.1.10
> ip dhcp pool VOICE_POOL
> network 192.168.10.0 255.255.255.0
> default-router 192.168.10.10
> option 150 ip 192.168.10.10

Команда option 150 ip 192.168.10.10 используется в сетях VoIP (Voice over IP) для настройки DHCP-сервера на предоставление клиентам информации о том, где они могут найти серверы TFTP (Trivial File Transfer Protocol), которые используются для загрузки конфигурационных файлов для IP-телефонов  

Далее перейдем к настрйоке ip-телефоном на роутере  
> telephony-services
> max-dn 2 (кол-во номеров макс)
> max-ephones (кол-во телефонов макс)
> ip source-address 192.168.10.10 port 2000 (тот же, что и сабинтерфейс роутера)

Далее настраиваем телефоны по очереди:  
> ephone-dn 1
> number 1010
> exit
> ephone 1
> type 7960 (всегда так)
> button 1:1 (заранее должно быть DHCP соединение с оконечными устройствами)
> и так делаем с каждым телефоном, меняя button 1:N, где N - номер устройства

В итоге, имеем работающую телефонную связь в пределах одного VLAN (для удобства, с учётом размера сети):  
![Scheme](https://github.com/DimbikeY/2023_2024-ip_telephony-k34212-dolmatov_d_a/blob/main/lab1/screens/%D0%A1%D0%BD%D0%B8%D0%BC%D0%BE%D0%BA%20%D1%8D%D0%BA%D1%80%D0%B0%D0%BD%D0%B0%202024-02-12%20225150.png)  
![Связность](https://github.com/DimbikeY/2023_2024-ip_telephony-k34212-dolmatov_d_a/blob/main/lab1/screens/%D0%A1%D0%BD%D0%B8%D0%BC%D0%BE%D0%BA%20%D1%8D%D0%BA%D1%80%D0%B0%D0%BD%D0%B0%202024-02-12%20225221.png)  

### Вывод:  
В результате выполнения данной лабораторной работы были изучены основы подключения ip-телефоном (не забываем команду switchport voice vlan NN), а также изучен материал по использованию роутера с DHCP сервером, который одновременно является сервером TFTP для корректной связности IP-телефонов.  

