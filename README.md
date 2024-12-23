Проект представляет справочник городов по странам. Использует технологии MySQL, Hibernate, Redis, Docker.
Есть реляционная БД MySQL со схемой (страна-город, язык по стране). 
Из дампа записываем данные в mysql docker + записываем данные в redis на docker.
docker run --name mysql -d -p 3306:3306 -e MYSQL_ROOT_PASSWORD=root --restart unless-stopped -v mysql:/var/lib/mysql mysql:8
docker run -d --name redis -p 6379:6379 redis:latest
Сравниваем скорость получения данных из mysql vs redis по выборке из 10 городов. Делаем выборку по 10 городам.
Сравнение скорости провёл на основании 10 запусков. Получилось следующее:

Redis:	64,4 ms
MySQL:	79,5 ms
По итогу, Redis оказался шустрее MySQL приблизительно на 15 ms.


