# Prueba 2 - Despliegue de una aplicación Django y React.js
Elaborar el deployment dockerizado de una aplicación en django (backend) con frontend
en React.js contenida en el repositorio. Es necesario desplegar todos los servicios en un solo docker-compose.
Se deben entregar los Dockerfiles pertinentes para elaborar el despliegue y justificar la forma en la que elabora el deployment (supervisor, scripts, dockercompose, kubernetes, etc)
Subir todo lo elaborado a un repositorio (github, gitlab, bitbucket, etc). En el repositorio se debe incluir el código de la aplicación y un archivo README.md
con instrucciones detalladas para compilar y desplegar la aplicación, tanto en una PC local como en la nube (AWS o GCP).

# Información Adicional
Los binarios del Frontend y del Backend son originarios de: https://github.com/craftech-inc/devops-interview-ultimate
Para esta prueba utilice Windows 11 como Sistema Operativo por lo tanto:
* Es necesario descargar Docker Engine: https://docs.docker.com/desktop/install/windows-install/
* Instalar minikube: https://minikube.sigs.k8s.io/docs/start/?arch=%2Fwindows%2Fx86-64%2Fstable%2F.exe+download
* Habilitar Kubernetes. Esto lo podemos hacer desde la misma interfaz de Docker Engine:
  ![image](https://github.com/frangcalzada/Craftech-Desafio-2024/assets/40276177/28cb040c-2f84-415b-82c6-034ec3972fcf)
  
* Como estoy utilizando Windows 11 se me presento el siguiente error en el contenedor django:
            "syntax error: unexpected end of file (expecting "do")"
  Este error esta relacionado a un problema de formato en el archivo, para solucionarlo hay que hacer lo siguiente:
  
  1) Reemplazar "entrypoint.sh" por el siguiente:
     ``#!/bin/sh

if [ "$DATABASE" = "postgres" ]; then
    echo "Waiting for postgres..."

    while ! nc -z $SQL_HOST $SQL_PORT; do
      sleep 0.1
    done

    echo "PostgreSQL started"
fi

# Uncomment below to flush db e.g. after running tests
# Just make sure you really mean it 
# python manage.py flush --no-input

# We have base custom user model so need to makemigrations out of box

python manage.py makemigrations core
python manage.py flush --no-input
python manage.py migrate
python manage.py loaddata initial_data.json
# python manage.py collectstatic --noinput
python manage.py runserver 0.0.0.0:8000

exec "$@" ``

2) Asegurarnos de que el archivo tenga permisos de ejecución:
   `` chmod +x backend/entrypoint.sh ``

3) Tirar este comando para convertir los saltos de linea:
   `` dos2unix backend/entrypoint.sh ``
  
