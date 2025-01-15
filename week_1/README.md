# КОНСПЕКТ

Пробовал те команды которые написаны выше, не всегда они получаются, ниже приведу список команд которые у меня вышли, но для того чтобы и правда понять что и где происходит я больше обращался к документации по адресу https://learn.conduktor.io/kafka/kafka-consumer-cli-tutorial/. 
Запускал все в контейнерах. Все необходимые файлы лежат в директории /bin. Итак команды:

- `kafka-topics --bootstrap-server localhost:9092 --create --topic samples --partitions 1 --replication-factor 1` 
Команда нужна была для того чтобы создать топик с именем samples, что такое партиции и реплицирующий фактор пока мне не понятно

- `kafka-console-producer --topic samples --bootstrap-server localhost:9092`
Команда нужна для того чтобы писать сообщения в кафку, не забываем имя топика и указываем его правильно. После написания этой команды консоль переведет строку и на новой строке напечатает > Можено вводить сообщения через Enter для завершения необходимо сделать ctrl+c

- `kafka-console-consumer --bootstrap-server localhost:9092 --topic samples --formatter kafka.tools.DefaultMessageFormatter --property print.timestamp=true --property print.key=true --property print.value=true --from-beginning`
Для чтения так же указывается сервер имя топика формат и какие то еще настройки для отображения . В доке написано так, “если вы хотите прочитать исторические данные используйте --from-beginning” я попробовал ввести команду без этого, и ничего не вывелось, видимо указывать какие данные все таки надо :) ААА только что допер что он видимо без этого флага будет читать в режиме онлайн :) 


P.S. Для закрепления прочитаю три статьи из оф документации 

1) https://learn.conduktor.io/kafka/kafka-topics-cli-tutorial/
Значит тут что было интересного, узнали как создавать топик (в целом выше описывал, но буду приводить все примеры команд)

- `kafka-topics --bootstrap-server localhost:9092 --topic first_topic --create --partitions 3 --replication-factor 1`
Обязательно надо указывать –bootstrap-server об этом пишут после каждого пункта, после - - topic идет его имя, партиции нужня для поддержания многопоточночти а репликатион фактор хер знает зачем…))
- `kafka-topics --bootstrap-server localhost:9092 --describe --topic samples`
Просмотр информации о топике
- `kafka-topics --bootstrap-server localhost:9092 --alter --topic samples --partitions 5`
Изменение параметров топика, в данном случае добавил партиций
- `kafka-topics --bootstrap-server localhost:9092 --topic samples --delete`
 Ну и удаление топика 

2) https://learn.conduktor.io/kafka/kafka-producer-cli-tutorial/

3) https://learn.conduktor.io/kafka/kafka-consumer-cli-tutorial/ 