# Tutorial original

https://www.youtube.com/watch?v=envBGHR3eBg

Aprende cómo desarrollar con Django usando Docker

1. Crear entorno virtual

```shell
python3 -m venv env
```

2. Activar entorno virtual

```shell
source env/bin/activate
```

3. Actualizar pip

```shell
pip install --upgrade pip
```

4. Instalar Django

```shell
pip install django
```

5. Crear proyecto Django en el directorio actual

```shell
django-admin startproject config .
```

6. Lanzamos servidor Django

```shell
python manage.py runserver
```

7. Construimos el contenedor

```shell
docker build -t docker/dockerizar-django .
```

8. Lanzamos el servidor mediante Docker

```shell
docker run -p 8000:8000 docker/dockerizar-django
```

9. Comando para sincronizar la edición con Docker

```shell
docker run -v /Users/jortega/Cursos/YouTube/docker/dockerizar-django/:/app -p 8000:8000 docker/dockerizar-django
```

## Ejecutar en segundo plano

```shell
docker run -d -v /Users/jortega/Cursos/YouTube/docker/dockerizar-django/:/app -p 8000:8000 docker/dockerizar-django
```

## Ver el logs

```shell
docker logs --follow 19e5ec07aad06e1ba587db3849238eeb6a0b2e83eb2b72364e69d625fa3a3702
```

## Para interactuar con el contenedor

```shell
docker exec -it 19e5ec07aad0 /bin/sh
```
Tip: sh porque alpine usa sh y no bash

## Una vez dentro de la consola del contenedor puedo ejecutar las migraciones

```shell
python manage.py migrate
```
```shell
python manage.py createsuperuser
```