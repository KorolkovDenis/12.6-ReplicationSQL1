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

![screen1](https://github.com/KorolkovDenis/)
![screen1](https://github.com/KorolkovDenis/)
![screen1](https://github.com/KorolkovDenis/)
![screen1](https://github.com/KorolkovDenis/)

## Дополнительные задания (со звёздочкой*)
Эти задания дополнительные, то есть не обязательные к выполнению, и никак не повлияют на получение вами зачёта по этому домашнему заданию. Вы можете их выполнить, если хотите глубже шире разобраться в материале.


### Задание 3* 

Выполните конфигурацию master-master репликации. Произведите проверку.

*Приложите скриншоты конфигурации, выполнения работы: состояния и режимы работы серверов.*

Ответ:

![screen1](https://github.com/KorolkovDenis/)
![screen1](https://github.com/KorolkovDenis/)
![screen1](https://github.com/KorolkovDenis/)


[Cсылка на google docs по «Репликация и масштабирование. Часть 1»]([https://docs.google.com/document/d/](https://docs.google.com/document/d/1Yxn2qyVMpI7dgJHVL_QKWgGjBdyFqmlq/edit?usp=drive_link&ouid=104113173630640462528&rtpof=true&sd=true)https://docs.google.com/document/d/1Yxn2qyVMpI7dgJHVL_QKWgGjBdyFqmlq/edit?usp=drive_link&ouid=104113173630640462528&rtpof=true&sd=true)
