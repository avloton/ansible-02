# Описание Playbook

Данный Playbook содержит три Plays: 

- Install Clickhouse.

Служит для установки `Clickhouse`.

- Install Vector.

Служит для установки `Vector`.

- Install LightHouse.

Служит для установки `LightHouse`.

## Tasks

Описание Tasks:

- Get clickhouse distrib.

Две задачи, которые организованы в блок, обе служат для загрузки файлов пакетов установки `Clickhouse`.
Первая задача организует цикл по нескольким пакетам, в случае ошибки выполняется вторая задача.

- Install clickhouse packages.

Установка пакетов Clickhouse, запланировать вызов handler `Start clickhouse service`.

- Restart ClickHouse.

Принудительный запуск handler, который должен перезапустить `Clickhouse`. 
Данный шаг необходим, так как следующая задача должна выполнить подключение к БД.

- Create database.

Создание БД `logs`, запись результата в переменную `create_db`.
Если код возврата не равен `0` и не равен `82` (БД существует), то задача считается проваленной.
Если код возврата равен `0`, то создание БД прошло успешно.

- Get Vector distrib.

Загрузка файлов пакетов для установки `Vector`.

- Install Vector.

Установка Vector, запланировать вызов handler `Start Vector`

- Vector config template.

Подготовка шаблона файла конфигурации для `vector`.

- Check Host.

Проверка на то, что на хосте установлен дистрибутив `Centos`.
Если проверка не пройдена, то дальнейшие задачи на хосте не выполняем.

- Install repository EPEL.

Установка репозитория EPEL.

- Install Git.

Установка `Git`.

- Install Nginx.

Установка `Nginx`.

- Clear web directory.

Очистка директории, в которую будем ложить файлы `LightHouse`.

- Clone LightHouse repository.

Клонирование репозитория `LightHouse`, запланировать вызов handler `Start Nginx`.

## Handlers

Описание Handlers:

- Start clickhouse service.

Перезапуск службы `clickhouse-server`.

- Start Vector.

Перезагрузка демона `systemd`, включение службы `vector` в `systemd`, перезапуск службы `vector`. 

- Start Nginx.

Перезагрузка демона `systemd`, включение службы `nginx` в `systemd`, перезапуск службы `nginx`. 


## Tags

Описание Tags:

- clickhouse.

Тэг присвоен для Play `Install Clickhouse`. Может служить для установки `Clickhouse`.

- vector.

Тэг присвоен для Play `Install Vector`. Может служить для установки `Vector`.

- lighthouse.

Тэг присвоен для Play `Install LightHouse`. Может служить для установки `LightHouse`.