# Prueba 2 - Despliegue de una aplicación Django y React.js
Elaborar el deployment dockerizado de una aplicación en django (backend) con frontend
en React.js contenida en el repositorio. Es necesario desplegar todos los servicios en un solo docker-compose.
Se deben entregar los Dockerfiles pertinentes para elaborar el despliegue y justificar la forma en la que elabora el deployment (supervisor, scripts, dockercompose, kubernetes, etc)
Subir todo lo elaborado a un repositorio (github, gitlab, bitbucket, etc). En el repositorio se debe incluir el código de la aplicación y un archivo README.md
con instrucciones detalladas para compilar y desplegar la aplicación, tanto en una PC local como en la nube (AWS o GCP).

# Resolución
1) Utilizando Docker Compose integro el backend y frontend en un solo archivo ``` docker-compose.yml ```. De esta manera me aseguro de que ambos
   servicios se puedan comunicar entre si. El archivo se encuentra en ``` Craftech-Desafio-2024/Prueba 2/docker-compose.yml ```.
2) Asegurarse de que ```entrypoint.sh``` tenga permisos de ejecución, puedes hacerlo con: ```  chmod +x backend/entrypoint.sh ```.
3) Parado sobre: ``` Craftech-Desafio-2024/Prueba 2 ``` ejecutar: ``` docker-compose up --build ```
4) Acceder a la aplicación:
   * Backend (Django): http://localhost:8000
   * Frontend (React.js): http://localhost:3000

# Información Adicional
Los binarios del Frontend y del Backend son originarios de: https://github.com/craftech-inc/devops-interview-ultimate
Para esta prueba utilice Windows 11 como Sistema Operativo por lo tanto:
* Es necesario descargar Docker Engine: https://docs.docker.com/desktop/install/windows-install/
* Instalar minikube: https://minikube.sigs.k8s.io/docs/start/?arch=%2Fwindows%2Fx86-64%2Fstable%2F.exe+download
* Habilitar Kubernetes. Esto lo podemos hacer desde la misma interfaz de Docker Engine:
  ![image](https://github.com/frangcalzada/Craftech-Desafio-2024/assets/40276177/28cb040c-2f84-415b-82c6-034ec3972fcf)
  
* Como estoy utilizando Windows 11 se me presento el siguiente error en el contenedor django: 
            `` syntax error: unexpected end of file (expecting "do") ``
  
  Este error esta relacionado a un problema de formato en el archivo, para solucionarlo hay que hacer lo siguiente:
  

1) Asegurarnos de que el archivo tenga permisos de ejecución:
   
   `` chmod +x backend/entrypoint.sh ``

3) Tirar este comando para convertir los saltos de linea:
   
   `` dos2unix backend/entrypoint.sh ``
  
* Es importante revisar que los puertos 8000 y 3000 no esten siendo utilizados. En mi caso estaba teniendo un error ya que el puerto 3000 estaba siendo utilizado por un sitio en mi IIS.
