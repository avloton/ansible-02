# Описание Playbook

Данный playbook устанавливает три роли:
- Clickhouse
- Vector
- LightHouse

Установка зависимостей:

```
ansible-galaxy install -r requirements.yml
```

Описание хостов содержится в inventory:

```
./inventory/prod.yml
```

Запуск playbook:

```
ansible-playbook -i inventory/prod.yml site.yml
```