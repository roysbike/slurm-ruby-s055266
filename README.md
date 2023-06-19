**Описание плейбука для развертывания и настройки приложения на Ruby**

- Название: Deploy and configure myapp
- Хост: slurm2.360on.ru

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

roles/postgres:

Описание: Роль для установки  Postgres-server 

Описание: Роль для развертывания и настройки приложения Ruby
roles/nginxinc.nginx:

Описание: Роль для развертывания и настройки приложения  Nginx

#### Deploy с помощью docker:

ansible-playbook docker_deploy.yml

Данные playbook установит docker на host (centos7) , скопирует проект, соберет его и запустит с помощью docker-compose. 
