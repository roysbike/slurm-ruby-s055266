**Описание плейбука для развертывания и настройки приложения на Ruby**

Есть два варианта запустить проект 

1) Через playbook  playbook.yml. Данный плей соберет окружение на удаленной VM centos7 и запустит его
2) Через docker .Playbook Установится docker , скопируется код , соберется контейнер для ruby , а nginx и postgres возьмется с hub.docker

#### Переменные:

```yaml
vars:
  app_dir: /tmp/xpaste_practicum
  local_app_code: files/xpaste_practicum
  local_nginx_conf: files/xpaste_practicum/config/nginx.conf
  app_user: roys
  app_name: puma_service
  app_secret: 34mvds2
  rails_log_to_stdout: 1
  rails_env: production
  db_host: 127.0.0.1
  db_port: 5432
  app_db: app
  app_db_user: app
  app_db_password: 2sDM1az
````

#### Роли:

roles/postgres: Описание: Роль для установки  Postgres-server 

roles/app - Описание: Роль для развертывания и настройки приложения Ruby

roles/nginxinc.nginx: Роль для развертывания и настройки приложения  Nginx

#### Deploy с помощью docker:

ansible-playbook docker_deploy.yml

Данные playbook установит docker на host (centos7) , скопирует проект, соберет его и запустит с помощью docker-compose. 
