# Морозова Юлия, OTUS, группа Postgre-DBA-2023-11

## Домашнее задание №3 по теме: «Физический уровень PostgreSQL»

<br/><br/>

1. Создаю ВМ c Ubuntu 20.04 LTS в ЯО :

    ![1_0](https://github.com/Y-M-Morozova/3_homework_Morozova_Yulia/assets/153178571/eda1997f-907b-47c9-a45b-dc8fe09737d9)
 
<br/><br/>

2.	Создаю docker-сеть pg-net:

    ![2](https://github.com/Y-M-Morozova/2_homework_Morozova_Yulia/assets/153178571/c45b2e71-11f7-463c-92c8-c36391c1ab5d)

<br/><br/>

3.	Подключаю созданную сеть pg-net к контейнеру(pg-server) сервера Postgres, версия 15, порт хоста 5432, порт контейнера 5432, создаю и монтирую ЛОКАЛЬНУЮ папку для хранения данных: /var/lib/postgresql/data:

    ![3](https://github.com/Y-M-Morozova/2_homework_Morozova_Yulia/assets/153178571/a8699bfe-809f-4c87-ad00-16245ce1bdfd)

<br/><br/>
