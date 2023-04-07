# ServerConnect
# ServerConnect

django-clean-template
Чистый шаблон django: nginx + gunicorn + supervisor

### 1. Ставим необходимые пакеты



```commandline
sudo apt-get update && sudo apt-get upgrade -y
```

```commandline
sudo apt-get install -y  htop git curl nano nginx  supervisor
```

```commandline
sudo apt-get install -y python3-pip python3-dev python3-venv
```

### 2. Ставим нужный пакет Python

```commandline
python3 --version 
```

### 3. Создаем директории 

```commandline
mkdir code && cd code && mkdir project1 && cd project1
```

/home/user/code/project1

### 4. Создаем виртуальное окружение и активируем его

```commandline
python3 -m venv env
```

```commandline
source env/bin/activate
```

### 5. Апдейтим пакеты устанавливаем Django

```commandline
pip install -U pip setuptools
```

```commandline
pip install django gunicorn
```

### 6. стартуем django project

```
django-admin startproject config .
```
### 7. Переходим в папку на уровне с manage.py и создаем gunicorn config

```commandline
sudo nano gunicorn_conf.py
```

### 8. В текущей папке создаем папку bin/ и создаем скрипт gunicorn и выдаем ему права

```commandline
mkdir bin/ && cd bin/
```

```commandline
sudo nano start_gunicorn.sh
```

```commandline
sudo chmod +x bin/start_gunicorn.sh
```

### 9. Настраиваем конфиги nginx и рестартим

```commandline
cd /etc/nginx/sites-enabled/  && sudo nano default
```
коментим текущие настройки вставляем свои

проверяем правильность настроек

```commandline
sudo nginx -t
```

```commandline
sudo service nginx restart
```

### 10. Настраиваем supervisor и запускаем

```commandline
cd /etc/supervisor/conf.d && sudo nano project1.conf
```
```commandline
sudo service supervisor start
```
### 11. Прописываем домен и рестартим сервер

в setting.py  прописываем hosts ip "127.0.0.1"

```commandline
sudo reboot
```

