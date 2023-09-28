# Домашнее задание к занятию "`ELK`" - `Стрекозов Владимир`  

### Задание 1. Elasticsearch  
Установите и запустите Elasticsearch, после чего поменяйте параметр cluster_name на случайный.  
Приведите скриншот команды `curl -X GET 'localhost:9200/_cluster/health?pretty`, сделанной на сервере с установленным Elasticsearch. Где будет виден нестандартный cluster_name.  
![](https://github.com/Svalker1989/ElasticSearch/blob/main/Z1.PNG)  
P.S. Для себя  
Команды, которые использовал для работы с БД ElasticSearch в Dev Tools  
Получить все индексы с записями:  
`GET _search  
{  
  "query": {  
    "match_all": {}  
  }  
}`  
Получить список индексов:  
`GET _cat/indices`  
Удалить индекс по имени:  
`DELETE *index_name*`  
Работает на порту 9200  

### Задание 2. Kibana   
Установите и запустите Kibana.  
Приведите скриншот интерфейса Kibana на странице `http://<ip вашего сервера>:5601/app/dev_tools#/console`, где будет выполнен запрос `GET /_cluster/health?pretty`.  
![](https://github.com/Svalker1989/ElasticSearch/blob/main/Z2.PNG)  
P.S. Для себя  
Для просмотра логов в разделе discovery сначала создать index pattern в Stack Management->Index Pattern  
### Задание 3. Logstash  
Установите и запустите Logstash и Nginx. С помощью Logstash отправьте access-лог Nginx в Elasticsearch.  
Приведите скриншот интерфейса Kibana, на котором видны логи Nginx.  
![](https://github.com/Svalker1989/ElasticSearch/blob/main/Z3.PNG)  
P.S. Для себя  
Файл конфигурации, который берет файл лога и отправляет на порт эластика с кастомным именем индекса:  
[logstash.conf](https://github.com/Svalker1989/ElasticSearch/blob/main/logstash.conf)  
### Задание 4. Filebeat  
Установите и запустите Filebeat. Переключите поставку логов Nginx с Logstash на Filebeat.  
Приведите скриншот интерфейса Kibana, на котором видны логи Nginx, которые были отправлены через Filebeat.  
![](https://github.com/Svalker1989/ElasticSearch/blob/main/Z4.PNG)  
P.S. Для себя  
Файл конфигурации, который слушает всё что к нему прилетает на порт 5044 и отправляет на порт эластика с кастомным именем индекса:  
[logstash_FB.conf](https://github.com/Svalker1989/ElasticSearch/blob/main/logstash_FB.conf)  
Для запуска filebeat со своим конфигурационным yml файлом и выводом лога в командню строку `filebeat -e -c *yml name*`  
Конфиг filebeat для отправки в логстэш лога nginx  
[filebeat_to_logstash_nginx.yml](https://github.com/Svalker1989/ElasticSearch/blob/main/filebeat_to_logstash_nginx.yml)  
Конфиг filebeat для отправки в логстэш syslog, файл кладем в `/etc/filebeat`  
[filebeat_to_logstash_syslog.yml](https://github.com/Svalker1989/ElasticSearch/blob/main/filebeat_to_logstash_syslog.yml)  
### Задание 5*. Доставка данных  
Настройте поставку лога в Elasticsearch через Logstash и Filebeat любого другого сервиса , но не Nginx. Для этого лог должен писаться на файловую систему, Logstash должен корректно его распарсить и разложить на поля.  
Приведите скриншот интерфейса Kibana, на котором будет виден этот лог и напишите лог какого приложения отправляется.  
![](https://github.com/Svalker1989/ElasticSearch/blob/main/Z5.PNG)
