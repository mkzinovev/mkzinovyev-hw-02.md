# Домашнее задание к занятию "Система мониторинга Zabbix" - `Зиновьев Михаил`
ОС: Red OS 7.3

---
### Использованные команды


## Задание 1. Установка Zabbix Server с веб-интерфейсом (PostgreSQL + Apache)


### 1. Установка PostgreSQL
```bash
sudo dnf install -y postgresql-server postgresql-contrib
sudo postgresql-setup initdb
sudo systemctl enable --now postgresql
```

---


### 2. Создание базы данных и пользователя Zabbix
```bash
sudo -u postgres psql

CREATE USER zabbix WITH PASSWORD 'StrongPassword';
CREATE DATABASE zabbix OWNER zabbix;
\q
```

### 3. Подключение официального репозитория Zabbix
```bash
sudo rpm -Uvh https://repo.zabbix.com/zabbix/6.0/rhel/7/x86_64/zabbix-release-6.0-4.el7.noarch.rpm
sudo dnf clean all
sudo dnf makecache
```

### 4. Установка Zabbix Server + Web + Agent
```bash
sudo dnf install -y \
zabbix-server-pgsql \
zabbix-web-pgsql \
zabbix-apache-conf \
zabbix-sql-scripts \
zabbix-agent
```

### 5. Импорт схемы базы данных
```bash
cd /tmp
zcat /usr/share/zabbix-sql-scripts/postgresql/server.sql.gz | sudo -u zabbix psql zabbix
```

### 6. Настройка Zabbix Server
```bash
sudo nano /etc/zabbix/zabbix_server.conf
```

Изменён параметр:
```bash
DBPassword=StrongPassword
```

### 7. Настройка PHP 
```bash
sudo nano /etc/php.ini
date.timezone = Europe/Moscow
```

### 8. Запуск сервисов
```bash
sudo systemctl enable --now zabbix-server zabbix-agent httpd
sudo systemctl restart zabbix-server httpd
```

### 9. Проверка статусов
```bash
systemctl status zabbix-server --no-pager
systemctl status httpd --no-pager
```

### Админка Zabbix
![Zabbix админка](adminka.png)


---

### Задание 2

`Приведите ответ в свободной форме........`

1. `Заполните здесь этапы выполнения, если требуется ....`
2. `Заполните здесь этапы выполнения, если требуется ....`
3. `Заполните здесь этапы выполнения, если требуется ....`
4. `Заполните здесь этапы выполнения, если требуется ....`
5. `Заполните здесь этапы выполнения, если требуется ....`
6. 

```
Поле для вставки кода...
....
....
....
....
```

`При необходимости прикрепитe сюда скриншоты



---

### Задание 3

`Приведите ответ в свободной форме........`

1. `Заполните здесь этапы выполнения, если требуется ....`
2. `Заполните здесь этапы выполнения, если требуется ....`
3. `Заполните здесь этапы выполнения, если требуется ....`
4. `Заполните здесь этапы выполнения, если требуется ....`
5. `Заполните здесь этапы выполнения, если требуется ....`
6. 

```
Поле для вставки кода...
....
....
....
....
```

`При необходимости прикрепитe сюда скриншоты
![Название скриншота](ссылка на скриншот)`

### Задание 4

`Приведите ответ в свободной форме........`

1. `Заполните здесь этапы выполнения, если требуется ....`
2. `Заполните здесь этапы выполнения, если требуется ....`
3. `Заполните здесь этапы выполнения, если требуется ....`
4. `Заполните здесь этапы выполнения, если требуется ....`
5. `Заполните здесь этапы выполнения, если требуется ....`
6. 

```
Поле для вставки кода...
....
....
....
....
```

`При необходимости прикрепитe сюда скриншоты
![Название скриншота](ссылка на скриншот)`
