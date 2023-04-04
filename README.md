список ВМ, их назначение в тестах, в настоящий момент:

```192.168.109.218 consul
192.168.109.219 redis-server
192.168.109.220 slave1
192.168.109.221 slave2
```
+++++++++++++++++++++++++++++++++++++++++++++++++++++

для каждого хоста\вм:
- consul agent

для ВМ с redis 
- Redis,Sentinel, consul agent, keepalived
 
+++++++++++++++++++++++++++++++++++++++++++++++++++++

дополняется постепенно

```
1. Consul
    1.1 Consul Agent
    1.2 Consul Template	
2. Redis
    2.1 Redis Sentinel
3. Keepalived

1. Consul - обеспечивает “discover services”, для этого на каждом хосте устанавливается Consul Agent.
Так же следит за состоянием сервисов, на основе проверок (health-check), можно использовать свои скрипты.
Consul  


Consul-template позволяет формировать файлы на основе шаблонов с данными, которые хранятся в Consul. 
Используется для формирования конфигурационных файлов для сервисов.
Template (шаблон конфига)



2. Redis, используем схему 1 мастер и 2 слейва. 
Sentinel это инструмент, который позволяет собрать кластер из СУБД Redis в режиме master-replica.
Redis Sentinel сам мониторит, настраивает и переключает роли. Если мастер-узел падает, сервис сам выбирает узел на замену, назначает его мастером и выполняет перенастройку, путем кворума между оставшимися нодами.

- мастер падает;
- Sentinel выжидает по умолчанию 5 секунд* (базовое значение, параметр down-after-milliseconds), давая мастеру время вернуться;
- если не дожидается — начинает выбор нового лидера:

3. Keepalived – используется для обеспечения высокой доступности Redis.
В ситуации описанной выше возможна потеря подключений, но keepalived -
в случае недоступности master’a  - переназначает виртуальный адрес на другую ноду, снижая шанс потери подключений\данных.
```

