# iptables

ДЗ

    Сценарии iptables

    реализовать knocking port
    centralRouter может попасть на ssh inetrRouter через knock скрипт пример в материалах.

    добавить inetRouter2, который виден(маршрутизируется (host-only тип сети для виртуалки)) с хоста или форвардится порт через локалхост.

    запустить nginx на centralServer.
    пробросить 80й порт на inetRouter2 8080.
    дефолт в инет оставить через inetRouter.

    Формат сдачи ДЗ - vagrant + ansible

    реализовать проход на 80й порт без маскарадинга

---

Запуск стенда

    vagrant up 


реализовать knocking port

На centralRouter необходимо выполнить 

    ./knock.sh 192.168.255.1 8881 7777 9991

    ssh root@192.168.255.1

Проверка    

![](https://github.com/MaxOOOOON/iptables/blob/main/pictures/Screenshot_20211103_004952.png)  

Проверка проброса порта     

![](https://github.com/MaxOOOOON/iptables/blob/main/pictures/Screenshot_20211103_004326.png)  
