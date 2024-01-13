# Морозова Юлия, OTUS, группа Postgre-DBA-2023-11

## Домашнее задание №3 по теме: «Физический уровень PostgreSQL»

<br/><br/>

1. Создаю ВМ c Ubuntu 20.04 LTS в ЯО :

    ![1_0](https://github.com/Y-M-Morozova/3_homework_Morozova_Yulia/assets/153178571/eda1997f-907b-47c9-a45b-dc8fe09737d9)
 
<br/><br/>

2.	Устанавливаю  PostgreSQL 15 и проверяю кластер:

    ![1_2](https://github.com/Y-M-Morozova/3_homework_Morozova_Yulia/assets/153178571/21376cde-e71b-440f-a951-9c9124ea739b)

<br/><br/>

3.	Логинюсь пользователем postgres в psql и создаю для тестов таблицу test, вставляю туда строку, так же смотрю конфигурационные файлы: 

    ![2_2](https://github.com/Y-M-Morozova/3_homework_Morozova_Yulia/assets/153178571/4d4d876d-20b8-4ae1-be29-e769a995e765)

<br/><br/>

и обращаю внимание, что data directory - на текущий момент по умолчанию:

```
postgres=# show data_directory;
       data_directory
-----------------------------
 /var/lib/postgresql/15/main
(1 row)
```


