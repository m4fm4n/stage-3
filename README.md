Дипломный проект для SkillFactory
---

Этап третий.

Логгирование и мониторинг.

---

  1. Зайти на сервер SRV и запустить скрипт, разворачивающий elasticsearch+kibana+fluentd:

```
sudo ./stage-3-settings.sh
```

  2. Перейти по адресу http://<public_ip_SRV>:5601 в браузере

2.1. В разделе Discover создать data view по паттерну "logstash-*"


  3. Для оповещения в Telegram необходимо внести свои данные в файл /opt/monitoring/docker-compose.yml:

```
            TELEGRAM_ADMIN: 0000000 # ID Telegram
            TELEGRAM_TOKEN: 0000000:xxxxyyyyzzzz # Token Telegram bot
```

  4. Выполнить команду, для запуска мониторинга:

```
sudo docker-compose -f /opt/monitoring/docker-compose.yml up -d
```

  5. Перейти по адресу http://<public_ip_SRV>:3000 в браузере

  6. Осуществить вход со стандартными значениями (admin/admin), изменить пароль (по желанию)

  7. Добавить Data source - Prometheus; Prometheus server URL: http://prometheus:9090 

  8. В Dashboards воспользоваться импортом дашбордов: Prometheus Blackbox Exporter(id 7587) для мониторинга приложения,  Node Exporter Full(id 1860) для сервера мониторинга.


