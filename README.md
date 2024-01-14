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
<br/><br/>

4. Останавливаю postgres:

    ![3](https://github.com/Y-M-Morozova/3_homework_Morozova_Yulia/assets/153178571/3bc05b14-9f08-47b9-ac34-deebaad39c99)

   <br/><br/>

5.  Создаю новый диск к ВМ размером 10GB и добавляю его в своей ВМ в яндекс облаке:
  
    ![4](https://github.com/Y-M-Morozova/3_homework_Morozova_Yulia/assets/153178571/516aec6e-9c0c-4920-af68-c3b3d1ee1af4)

    <br/><br/>
      
6. Определяю (идентифицирую свой диск 10 GB в системе(у меня это : ```vdb```) :

    ![4_2](https://github.com/Y-M-Morozova/3_homework_Morozova_Yulia/assets/153178571/02ab13f0-b364-488c-b42d-76fafb03b56a)

   <br/><br/>

7. Партицирую новый диск:

- выбираю стандарт GPT:

    ![5](https://github.com/Y-M-Morozova/3_homework_Morozova_Yulia/assets/153178571/7c871eb0-27ca-4d7c-a3fd-45bd9bf8871c)

- создаю новый раздел на весь диск :

    ![5_111](https://github.com/Y-M-Morozova/3_homework_Morozova_Yulia/assets/153178571/63e85247-39e2-4c73-b3f2-2047db9b12d6)

    <br/><br/>
    
8. Создаю файловую систему в новом разделе:

   ![5_3](https://github.com/Y-M-Morozova/3_homework_Morozova_Yulia/assets/153178571/ce1eee95-efe6-4b31-8fc1-2e71bb00989a)

   ![5_4](https://github.com/Y-M-Morozova/3_homework_Morozova_Yulia/assets/153178571/e335b3db-a873-47e9-a1b0-b09467496ce4)

   


  
     
   
