# Prueba 3 - CI/CD
Dockerizar un nginx con el index.html default. Elaborar un pipeline que ante cada cambio realizado sobre el index.html buildee
la nueva imagen y la actualize en la plataforma elegida. (docker-compose, swarm, kuberenetes, etc.) Para la creacion del CI/CD se puede utilizar cualquier
plataforma (CircleCI, Gitlab, Github, Bitbucket.)

# Resolución
1) Cree un archivo estatico llamado index.html URL: https://frangcalzada.github.io/Craftech-Desafio-2024/Prueba%203/index.html
   ![image](https://github.com/frangcalzada/Craftech-Desafio-2024/assets/40276177/386f4ce3-3841-4bf1-808d-eff0b7812b3b)
   
2) Cree un Dockerfile: este archivo lo utilizo para construir la imagen Docker de nginx con el index.html incorporado.
3) El Dockerfile esta configurado para:
   * Utilizar la imagen base oficial de nginx.
   * Copiar el index.html dentro del contenedor nginx.
4) Configure un Pipeline CI/CD con GitHub Actions, para ello cree un archivo llamado ```ci-cd.yml```
   * Este se activa cada vez que se realiza un push a la rama ```main```
   * Construye la imagen Docker usando el Dockerfile ubicado en la carpeta ```Prueba 3```
   * Sube la imagen Docker al GitHub Container Registry utilizando credenciales almacenadas como secreto.
  
5) Configurar GitHub Pages
   * En la sección de configuración de GitHub Pages (Settings > Pages), seleccioné main como la rama de origen.
   * Configuré la carpeta /(root) para que GitHub Pages sirva el contenido desde la raíz de la rama main.
     
6) Tuve que configurar el README.md del repositorio original para que al hacer click en en titulo de Prueba 3 me lleve al index.html
   ya que no pude configurar para desde la URL: https://frangcalzada.github.io/Craftech-Desafio-2024/ pueda acceder ahi directamente.

# Información Adicional
1) Es necesario crear un Secret en el repositorio que se llame GH_TOKEN.
2) El valor de GH_TOKEN tiene que ser el Token que se genera desde https://github.com/settings/tokens
Dejo una captura de los Workflows en Actions donde se puede ver que cuando un cambio sobre index.html se hace un nuevo build.
![image](https://github.com/frangcalzada/Craftech-Desafio-2024/assets/40276177/7ed68c0b-3b66-4296-aa35-99852c84711b)
![image](https://github.com/frangcalzada/Craftech-Desafio-2024/assets/40276177/3031266e-d1a8-49a7-a740-30365c9e8eb5)
3) La idea principal era hacer el deploy en Heroku pero me pide una tarjeta de credito, al parecer es de pago, es por eso que termine haciendo todo en Github.

   
