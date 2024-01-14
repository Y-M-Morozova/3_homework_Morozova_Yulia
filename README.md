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
      
6. Определяю (идентифицирую свой диск 10 GB в системе(у меня это  ```vdb```) :

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

<br/><br/>

9. Создаю каталог (на этой машине у меня он будет ```/mnt/otus_data```) и монтирую новую файловую систему:

    ![5_5](https://github.com/Y-M-Morozova/3_homework_Morozova_Yulia/assets/153178571/65f44282-e2eb-42f6-b4e3-97a87ae59f65)

<br/><br/>
   
10. Чтобы автоматически монтировать файловую систему при каждой загрузке сервера, добавляю запись об этой файловой системе  в ```/etc/fstab``` файл:

    ![5_7](https://github.com/Y-M-Morozova/3_homework_Morozova_Yulia/assets/153178571/6d4df281-7123-44c3-9985-ebd4664c08ec)

<br/><br/>

11. Проверяю, что диск доступен и есть возможность чтения/записи на него(пишу, читаю в текcтовый файл ```/mnt/data/test_file```):

    ![5_8](https://github.com/Y-M-Morozova/3_homework_Morozova_Yulia/assets/153178571/50eca95c-f6e9-4b6a-915c-f1bc0d9eba58)

    ![5_9](https://github.com/Y-M-Morozova/3_homework_Morozova_Yulia/assets/153178571/d8915027-f271-487a-939f-38eeef2137ca)
    
<br/><br/>

12. рестартую свою ВМ для проверки, что диск после рестарта подключился, и  снова читаю файл ```/mnt/data/test_file``` , все ок:

    ![5_99](https://github.com/Y-M-Morozova/3_homework_Morozova_Yulia/assets/153178571/bfb25b39-76c0-4533-b504-fca920344d10)

    ![5_100](https://github.com/Y-M-Morozova/3_homework_Morozova_Yulia/assets/153178571/c1ba1ef9-6c5c-47e3-9930-4ce611297058)

<br/><br/>

13. Командой ```sudo chown -R postgres:postgres /mnt/otus_data/```делаю владельцем пользователя postgres каталога ```/mnt/otus_data```,
    переношу содержимое ```/var/lib/postgres/15``` в ```/mnt/otus_data```,
    пробую стартовать кластер postgres, но получаю ошибку:

    ![6_0](https://github.com/Y-M-Morozova/3_homework_Morozova_Yulia/assets/153178571/9f9ec949-9cea-4f62-9c11-8f16754d8425)

    ![6_2](https://github.com/Y-M-Morozova/3_homework_Morozova_Yulia/assets/153178571/15b691f5-5791-4106-bc53-482812882883)

<br/><br/>

 14. Кластер не может стартовать(ошибка выше), так как в конфигурационном файле ```/etc/postgresql/15/main/postgresql.conf```
     каталог данных Postgres определен как :
     ```data_directory = '/var/lib/postgresql/15/main'```, а я его переместила.
    Поэтому сначала изменяю эту строку на: ```data_directory = '/mnt/otus_data/15/main'``` в файле ```/etc/postgresql/15/main/postgresql.conf```,
    а затем успешно стартую Postgres:

     ![6_999](https://github.com/Y-M-Morozova/3_homework_Morozova_Yulia/assets/153178571/7660068f-6cd4-446c-aa3a-10af215dc544)

     ![99_3](https://github.com/Y-M-Morozova/3_homework_Morozova_Yulia/assets/153178571/53a90433-41ad-4714-ab69-3b32b83a206f)

<br/><br/>

15. Логинюсь в psql, еще раз проверяю ```data_directory``` и делаю запрос к своей тестовой таблице ```test``` - вс ок!

    ![11](https://github.com/Y-M-Morozova/3_homework_Morozova_Yulia/assets/153178571/1e4fcdc1-7ec2-4970-99ee-e9850ec8d22c)

<br/><br/> 

    

    
