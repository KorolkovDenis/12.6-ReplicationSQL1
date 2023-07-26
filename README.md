### Домашнее задание к занятию «Репликация и масштабирование. Часть 1» - Корольков Денис

### Задание 1

На лекции рассматривались режимы репликации master-slave, master-master, опишите их различия.

*Ответить в свободной форме.*

Ответ:
```
Master-Slave репликация
В этом подходе выделяется один основной сервер базы данных, который называется Master. На нем происходят все изменения в данных (любые запросы INSERT/UPDATE/DELETE).
Slave сервер постоянно копирует все изменения с Master. С приложения на Slave-сервер отправляются запросы чтения данных (запросы SELECT). Таким образом Master-сервер отвечает за изменения данных, а Slave за чтение.
```

### Задание 2

Выполните конфигурацию master-slave репликации, примером можно пользоваться из лекции.

*Приложите скриншоты конфигурации, выполнения работы: состояния и режимы работы серверов.*

Ответ:

```
apt-get install mysql-server mysql-client
mkdir -p /var/log/mysql
chown -R mysql: /var/lib/mysql
chown -R mysql: /var/log/mysql
mysqld –initialize
systemctl start mysql
nano /etc/mysql/mysql.conf.d/mysqld.cnf 
добавляю:
bind-address = 192.168.1.160
server-id = 1
log_bin = /var/log/mysql/mysql-bin.log
service mysql restart
mysql -u root -p
FLUSH PRIVILEGES;
CREATE USER 'replication'@'%' IDENTIFIED WITH mysql_native_password BY 'MysqlPass';
GRANT REPLICATION SLAVE ON *.* TO 'replication'@'%';
SHOW MASTER STATUS;

```

![screen1](https://github.com/KorolkovDenis/12.6-ReplicationSQL1/blob/main/screenshots/screen1.jpg)

На SLAVE:
```
CHANGE MASTER TO MASTER_HOST='192.168.1.160',MASTER_USER='replication', MASTER_PASSWORD='MysqlPass', MASTER_LOG_FILE='mysql-bin.000001', MASTER_LOG_POS= 841;
```

![screen2](https://github.com/KorolkovDenis/12.6-ReplicationSQL1/blob/main/screenshots/screen2.jpg)

```
START SLAVE;
SHOW SLAVE STATUS\G
SHOW DATABASES;
```

![screen3](https://github.com/KorolkovDenis/12.6-ReplicationSQL1/blob/main/screenshots/screen3.jpg)

Создаем на Мастере БД test_1. БД test_1 сразу реплицируется на SLAVE БД.

![screen4](https://github.com/KorolkovDenis/12.6-ReplicationSQL1/blob/main/screenshots/screen4.jpg)

## Дополнительные задания (со звёздочкой*)
Эти задания дополнительные, то есть не обязательные к выполнению, и никак не повлияют на получение вами зачёта по этому домашнему заданию. Вы можете их выполнить, если хотите глубже шире разобраться в материале.


### Задание 3* 

Выполните конфигурацию master-master репликации. Произведите проверку.

*Приложите скриншоты конфигурации, выполнения работы: состояния и режимы работы серверов.*

Ответ:

```
Теперь на нашем MASTER БД вводим:
CHANGE MASTER TO MASTER_HOST='192.168.1.173',MASTER_USER='replication', MASTER_PASSWORD='MysqlPass', MASTER_LOG_FILE='mysql-bin.000001', MASTER_LOG_POS= 1039;
START SLAVE;
```

![screen5](https://github.com/KorolkovDenis/12.6-ReplicationSQL1/blob/main/screenshots/screen5.jpg)
```
SHOW SLAVE STATUS\G
```
![screen6](https://github.com/KorolkovDenis/12.6-ReplicationSQL1/blob/main/screenshots/screen6.jpg)
![screen7](https://github.com/KorolkovDenis/12.6-ReplicationSQL1/blob/main/screenshots/screen7.jpg)


[Cсылка на google docs по «Репликация и масштабирование. Часть 1»]([https://docs.google.com/document/d/](https://docs.google.com/document/d/1Yxn2qyVMpI7dgJHVL_QKWgGjBdyFqmlq/edit?usp=drive_link&ouid=104113173630640462528&rtpof=true&sd=true)https://docs.google.com/document/d/1Yxn2qyVMpI7dgJHVL_QKWgGjBdyFqmlq/edit?usp=drive_link&ouid=104113173630640462528&rtpof=true&sd=true)
