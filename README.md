# docker-3rd-lab

Отчёт

Создание redis

![image alt](https://github.com/kawaiiRichard/docker-3rd-lab/blob/4ed5fc07fc734304b471ab73634d2a95552feb70/images/init_redis.png)

Проверка

![image alt](https://github.com/kawaiiRichard/docker-3rd-lab/blob/a9a39ffc452a61df995e22a54455bf7a89c326e8/images/redis_check.png)

http://localhost:8085 :

![image alt](https://github.com/kawaiiRichard/docker-3rd-lab/blob/a9a39ffc452a61df995e22a54455bf7a89c326e8/images/localhost8085.png)

Удаление контейнеров

![image alt](https://github.com/kawaiiRichard/docker-3rd-lab/blob/a9a39ffc452a61df995e22a54455bf7a89c326e8/images/containers_delete.png)

Запуск

![image alt](https://github.com/kawaiiRichard/docker-3rd-lab/blob/a9a39ffc452a61df995e22a54455bf7a89c326e8/images/compose_init.png)

Проверка

![image alt](https://github.com/kawaiiRichard/docker-3rd-lab/blob/a9a39ffc452a61df995e22a54455bf7a89c326e8/images/compose_check_1.png)

![image alt](https://github.com/kawaiiRichard/docker-3rd-lab/blob/a9a39ffc452a61df995e22a54455bf7a89c326e8/images/compose_check_2.png)

Применение изменений и масштаб

![image alt](https://github.com/kawaiiRichard/docker-3rd-lab/blob/a9a39ffc452a61df995e22a54455bf7a89c326e8/images/changes.png)

![image alt](https://github.com/kawaiiRichard/docker-3rd-lab/blob/a9a39ffc452a61df995e22a54455bf7a89c326e8/images/scaling.png)

Подобрало два порта: 32768 и 32769

![image alt](https://github.com/kawaiiRichard/docker-3rd-lab/blob/a9a39ffc452a61df995e22a54455bf7a89c326e8/images/localhost32768.png)

![image alt](https://github.com/kawaiiRichard/docker-3rd-lab/blob/a9a39ffc452a61df995e22a54455bf7a89c326e8/images/localhost32769.png)

Полное уничтожение стека

![image alt](https://github.com/kawaiiRichard/docker-3rd-lab/blob/a9a39ffc452a61df995e22a54455bf7a89c326e8/images/whole_stack_delete.png)

32768-й порт

![image alt](https://github.com/kawaiiRichard/docker-3rd-lab/blob/834a13e5dfba5b6042c1639b9465c68d0cf0b934/images/32768_check.png)

32769-й порт

![image alt](https://github.com/kawaiiRichard/docker-3rd-lab/blob/834a13e5dfba5b6042c1639b9465c68d0cf0b934/images/32769_check.png)

Ответы на вопросы

1. Зачем в Ч.1 использовался --link и почему в Compose он не нужен?
   --link использовался для ручного связывания контейнеров, создания записей в /etc/hosts и передачи переменных окружения. В Compose это не нужно, так как Compose автоматически создает общую сеть и разрешает имена сервисов через DNS.

2. Чем отличается image от build в Compose?
   image - использует готовый образ из registry

build - собирает образ из Dockerfile

3. Почему нельзя масштабировать сервис с публикацией фиксированного порта на одном хосте?
   Нельзя потому, что порт на хосте может быть занят только одним процессом. Способы обхода:

Использование динамических портов ("0:5000")

Использование балансировщика нагрузки (nginx, haproxy)

Развертывание на разных хостах (Docker Swarm, Kubernetes)

4. Что делает docker compose down -v и чем отличается от down без -v?
   docker compose down - останавливает и удаляет контейнеры, сети

docker compose down -v - дополнительно удаляет именованные volumes

5. Как в Compose обеспечивается сетевое имя сервиса для обращения из другого сервиса?
   Compose создает DNS-записи для каждого сервиса. Имя сервиса в docker-compose.yml становится hostname'ом в сети. Например, сервис redis доступен по имени redis из других сервисов.




