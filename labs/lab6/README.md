### Лабораторная работа 6. Внедрение маршрутизации между виртуальными локальными сетями 

### Топология
![alt text](https://github.com/elborisova3009/otus-networks/blob/master/labs/lab6/%D0%A1%D0%BA%D1%80%D0%B8%D0%BD%D1%88%D0%BE%D1%82%2012-10-2022%20102253.jpg)

### Таблица адресации
![alt text](https://github.com/elborisova3009/otus-networks/blob/master/labs/lab6/%D0%A1%D0%BA%D1%80%D0%B8%D0%BD%D1%88%D0%BE%D1%82%2012-10-2022%20102449.jpg)

### Таблица VLAN
![alt text](https://github.com/elborisova3009/otus-networks/blob/master/labs/lab6/%D0%A1%D0%BA%D1%80%D0%B8%D0%BD%D1%88%D0%BE%D1%82%2012-10-2022%20102459-3.jpg)

### Задачи
Часть 1. Создание сети и настройка основных параметров устройства  
Часть 2. Создание сетей VLAN и назначение портов коммутатора  
Часть 3. Настройка транка 802.1Q между коммутаторами  
Часть 4. Настройка маршрутизации между сетями VLAN  
Часть 5. Проверка, что маршрутизация между VLAN работает  

### Часть 1. Создание сети и настройка основных параметров устройства

Шаг 1. В CPT cоздаю сеть согласно топологии.  
![alt text](https://github.com/elborisova3009/otus-networks/blob/master/labs/lab6/%D0%A1%D0%BA%D1%80%D0%B8%D0%BD%D1%88%D0%BE%D1%82%2013-10-2022%20125218.jpg)  

Шаг 2. Настрою базовые параметры для маршрутизатора R1:

![alt text](https://github.com/elborisova3009/otus-networks/blob/master/labs/lab6/%D0%A1%D0%BA%D1%80%D0%B8%D0%BD%D1%88%D0%BE%D1%82%2012-10-2022%20112704.jpg)

Show Run:

![alt text](https://github.com/elborisova3009/otus-networks/blob/master/labs/lab6/%D0%A1%D0%BA%D1%80%D0%B8%D0%BD%D1%88%D0%BE%D1%82%2012-10-2022%20112857.jpg)

Шаг 3. Настрою базовые параметры каждого коммутатора (на примере S1):

![alt text](https://github.com/elborisova3009/otus-networks/blob/master/labs/lab6/%D0%A1%D0%BA%D1%80%D0%B8%D0%BD%D1%88%D0%BE%D1%82%2012-10-2022%20114144.jpg)

Show Run:

![alt text](https://github.com/elborisova3009/otus-networks/blob/master/labs/lab6/%D0%A1%D0%BA%D1%80%D0%B8%D0%BD%D1%88%D0%BE%D1%82%2012-10-2022%20114317.jpg)

Шаг 4. Настрою узлы ПК (согласно таблице адресации).

![alt text](https://github.com/elborisova3009/otus-networks/blob/master/labs/lab6/%D0%A1%D0%BA%D1%80%D0%B8%D0%BD%D1%88%D0%BE%D1%82%2012-10-2022%20115717.jpg)

![alt text](https://github.com/elborisova3009/otus-networks/blob/master/labs/lab6/%D0%A1%D0%BA%D1%80%D0%B8%D0%BD%D1%88%D0%BE%D1%82%2012-10-2022%20115754.jpg)

### Часть 2. Создание сетей VLAN и назначение портов коммутатора

Шаг 1. Создам сети VLAN на коммутаторах.

a.	Создам и назову необходимые VLAN на каждом коммутаторе из таблицы выше. 

Vlan 10 для S1: 

![alt text](https://github.com/elborisova3009/otus-networks/blob/master/labs/lab6/%D0%A1%D0%BA%D1%80%D0%B8%D0%BD%D1%88%D0%BE%D1%82%2012-10-2022%20125154.jpg)

Vlan 20 для S1: 

![alt text](https://github.com/elborisova3009/otus-networks/blob/master/labs/lab6/%D0%A1%D0%BA%D1%80%D0%B8%D0%BD%D1%88%D0%BE%D1%82%2012-10-2022%20130607.jpg)  
![alt text](https://github.com/elborisova3009/otus-networks/blob/master/labs/lab6/%D0%A1%D0%BA%D1%80%D0%B8%D0%BD%D1%88%D0%BE%D1%82%2012-10-2022%20130622.jpg)

И оставшиеся vlan для S1:

![alt text](https://github.com/elborisova3009/otus-networks/blob/master/labs/lab6/%D0%A1%D0%BA%D1%80%D0%B8%D0%BD%D1%88%D0%BE%D1%82%2012-10-2022%20132158.jpg)

Аналогично проведу работу для S2, проиллюстрирую выводом команды show vlan:

![alt text](https://github.com/elborisova3009/otus-networks/blob/master/labs/lab6/%D0%A1%D0%BA%D1%80%D0%B8%D0%BD%D1%88%D0%BE%D1%82%2012-10-2022%20133122.jpg)

b.	Настрою интерфейс управления и шлюз по умолчанию на каждом коммутаторе, используя информацию об IP-адресе в таблице адресации. 

S1:  

![alt text](https://github.com/elborisova3009/otus-networks/blob/master/labs/lab6/%D0%A1%D0%BA%D1%80%D0%B8%D0%BD%D1%88%D0%BE%D1%82%2012-10-2022%20134412.jpg)

S2:

![alt text](https://github.com/elborisova3009/otus-networks/blob/master/labs/lab6/%D0%A1%D0%BA%D1%80%D0%B8%D0%BD%D1%88%D0%BE%D1%82%2012-10-2022%20155036.jpg)  
![alt text](https://github.com/elborisova3009/otus-networks/blob/master/labs/lab6/%D0%A1%D0%BA%D1%80%D0%B8%D0%BD%D1%88%D0%BE%D1%82%2012-10-2022%20155048.jpg)

c.	Все неиспользуемые порты коммутаторов уже назначены во VLAN Parking_Lot, также они уже настроены для статического режима доступа.  
Теперь административно деактивирую их.

S1:

![alt text](https://github.com/elborisova3009/otus-networks/blob/master/labs/lab6/%D0%A1%D0%BA%D1%80%D0%B8%D0%BD%D1%88%D0%BE%D1%82%2012-10-2022%20160116.jpg)  
![alt text](https://github.com/elborisova3009/otus-networks/blob/master/labs/lab6/%D0%A1%D0%BA%D1%80%D0%B8%D0%BD%D1%88%D0%BE%D1%82%2012-10-2022%20160153.jpg)

S2:

![alt text](https://github.com/elborisova3009/otus-networks/blob/master/labs/lab6/%D0%A1%D0%BA%D1%80%D0%B8%D0%BD%D1%88%D0%BE%D1%82%2012-10-2022%20160529.jpg)  
![alt text](https://github.com/elborisova3009/otus-networks/blob/master/labs/lab6/%D0%A1%D0%BA%D1%80%D0%B8%D0%BD%D1%88%D0%BE%D1%82%2012-10-2022%20160644.jpg)

Шаг 2. Сети VLAN соответствующим интерфейсам коммутаторов были назначены выше.

### Часть 3. Конфигурация магистрального канала стандарта 802.1Q между коммутаторами

Шаг 1. Вручную настрою магистральный интерфейс F0/1 на коммутаторах S1 и S2.

a.	Настрою статический транкинг на интерфейсе F0/1 для обоих коммутаторов.  
b.	Установлю native VLAN 1000 на обоих коммутаторах.  
c.	Укажу, что VLAN 10, 20, 30 и 1000 могут проходить по транку.  
d.	Проверю транки, native VLAN и разрешенные VLAN через транк.

Синтаксис следующий.  
S1:  
![alt text](https://github.com/elborisova3009/otus-networks/blob/master/labs/lab6/%D0%A1%D0%BA%D1%80%D0%B8%D0%BD%D1%88%D0%BE%D1%82%2012-10-2022%20171533.jpg)  
![alt text](https://github.com/elborisova3009/otus-networks/blob/master/labs/lab6/%D0%A1%D0%BA%D1%80%D0%B8%D0%BD%D1%88%D0%BE%D1%82%2012-10-2022%20171202.jpg)

S2:   
![alt text](https://github.com/elborisova3009/otus-networks/blob/master/labs/lab6/%D0%A1%D0%BA%D1%80%D0%B8%D0%BD%D1%88%D0%BE%D1%82%2012-10-2022%20175352.jpg) 

Шаг 2. Вручную настрою магистральный интерфейс F0/5 на коммутаторе S1.

a.	Настрою интерфейс S1 F0/5 с теми же параметрами транка, что и F0/1. Это транк до маршрутизатора.  
b.	Сохраню текущую конфигурацию в файл загрузочной конфигурации.  
c.	Проверю транкинг.  

![alt text](https://github.com/elborisova3009/otus-networks/blob/master/labs/lab6/%D0%A1%D0%BA%D1%80%D0%B8%D0%BD%D1%88%D0%BE%D1%82%2012-10-2022%20180211.jpg)  
![alt text](https://github.com/elborisova3009/otus-networks/blob/master/labs/lab6/%D0%A1%D0%BA%D1%80%D0%B8%D0%BD%D1%88%D0%BE%D1%82%2012-10-2022%20180538.jpg)  
![alt text](https://github.com/elborisova3009/otus-networks/blob/master/labs/lab6/%D0%A1%D0%BA%D1%80%D0%B8%D0%BD%D1%88%D0%BE%D1%82%2012-10-2022%20180223.jpg)  

### Вопрос:
Что произойдет, если G0/0/1 на R1 будет отключен?  
*Магистральный канал позволяет передавать трафик нескольких VLAN через один канал. Без магистрального порта для каждой VLAN требуется отдельное соединение между коммутаторами. Если отключить G0/0/1 на R1, трафик межу VLAN не будет роутится.*

### Часть 4. Настройка маршрутизации между сетями VLAN

Шаг 1. Настрою маршрутизатор R1.

a.	Активирую интерфейс G0/0/1 на маршрутизаторе.  
![alt text](https://github.com/elborisova3009/otus-networks/blob/master/labs/lab6/%D0%A1%D0%BA%D1%80%D0%B8%D0%BD%D1%88%D0%BE%D1%82%2013-10-2022%20110931.jpg)

b.	Настрою подинтерфейсы для каждой VLAN согласно таблице IP-адресации (не забыв про инкапсуляцию 802.1Q).  
Подинтерфейсу для native VLAN не назначаю IP-адрес.  
Включаю описание для каждого подинтерфейса.  
Интерфейсы работают.     
![alt text](https://github.com/elborisova3009/otus-networks/blob/master/labs/lab6/%D0%A1%D0%BA%D1%80%D0%B8%D0%BD%D1%88%D0%BE%D1%82%2013-10-2022%20110616.jpg)

Show run:  
![alt text](https://github.com/elborisova3009/otus-networks/blob/master/labs/lab6/%D0%A1%D0%BA%D1%80%D0%B8%D0%BD%D1%88%D0%BE%D1%82%2013-10-2022%20110645.jpg)

Show ip interface brief:  
![alt text](https://github.com/elborisova3009/otus-networks/blob/master/labs/lab6/%D0%A1%D0%BA%D1%80%D0%B8%D0%BD%D1%88%D0%BE%D1%82%2013-10-2022%20110702.jpg)

### Часть 5. Проверка маршрутизация между VLAN

Шаг 1. Выполню следующие тесты с PC-A.   
a.	Эхо-запрос с PC-A на шлюз по умолчанию.    
![alt text](https://github.com/elborisova3009/otus-networks/blob/master/labs/lab6/%D0%A1%D0%BA%D1%80%D0%B8%D0%BD%D1%88%D0%BE%D1%82%2013-10-2022%20125406.jpg)  

b.	Отправьте эхо-запрос с PC-A на PC-B.
Пинг не проходит. 

### По итогам проведенной работы над ошибками, в конфигурации устройст были внесены следующие изменения. 

1. На обоих коммутаторах были прописаны все VLANы. 

![alt text](https://github.com/elborisova3009/otus-networks/blob/master/labs/lab6/%D0%A1%D0%BA%D1%80%D0%B8%D0%BD%D1%88%D0%BE%D1%82%2014-10-2022%20124011.jpg)  
![alt text](https://github.com/elborisova3009/otus-networks/blob/master/labs/lab6/%D0%A1%D0%BA%D1%80%D0%B8%D0%BD%D1%88%D0%BE%D1%82%2014-10-2022%20124047.jpg)  

2. На trunkе между коммутаторами изменена фильтрация VLAN - теперь там прописаны все VLANы.

![alt text](https://github.com/elborisova3009/otus-networks/blob/master/labs/lab6/%D0%A1%D0%BA%D1%80%D0%B8%D0%BD%D1%88%D0%BE%D1%82%2014-10-2022%20125638.jpg)

![alt text](https://github.com/elborisova3009/otus-networks/blob/master/labs/lab6/%D0%A1%D0%BA%D1%80%D0%B8%D0%BD%D1%88%D0%BE%D1%82%2014-10-2022%20125459.jpg)

![alt text](https://github.com/elborisova3009/otus-networks/blob/master/labs/lab6/%D0%A1%D0%BA%D1%80%D0%B8%D0%BD%D1%88%D0%BE%D1%82%2014-10-2022%20125521.jpg)

![alt text](https://github.com/elborisova3009/otus-networks/blob/master/labs/lab6/%D0%A1%D0%BA%D1%80%D0%B8%D0%BD%D1%88%D0%BE%D1%82%2014-10-2022%20124922.jpg)

![alt text](https://github.com/elborisova3009/otus-networks/blob/master/labs/lab6/%D0%A1%D0%BA%D1%80%D0%B8%D0%BD%D1%88%D0%BE%D1%82%2014-10-2022%20125555.jpg)

### Вернусь на этап b. Части 5.

b.	Отправьте эхо-запрос с PC-A на PC-B.

![alt text](https://github.com/elborisova3009/otus-networks/blob/master/labs/lab6/%D0%A1%D0%BA%D1%80%D0%B8%D0%BD%D1%88%D0%BE%D1%82%2014-10-2022%20132323.jpg)

c.	Отправьте команду ping с компьютера PC-A на коммутатор S2.

![alt text](https://github.com/elborisova3009/otus-networks/blob/master/labs/lab6/%D0%A1%D0%BA%D1%80%D0%B8%D0%BD%D1%88%D0%BE%D1%82%2014-10-2022%20131658.jpg)

Шаг 2. Пройду следующий тест с PC-B.  
В окне командной строки на PC-B выполните команду tracert на адрес PC-A.  

![alt text](https://github.com/elborisova3009/otus-networks/blob/master/labs/lab6/%D0%A1%D0%BA%D1%80%D0%B8%D0%BD%D1%88%D0%BE%D1%82%2014-10-2022%20132523.jpg)  

Вопрос:
Какие промежуточные IP-адреса отображаются в результатах?  
*192.168.30.1; 192.168.20.3*
