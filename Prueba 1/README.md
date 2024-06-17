# Prueba 1 - Diagrama de Red
Produzca un diagrama de red (puede utilizar lucidchart) de una aplicación web en GCP o AWS y escriba una descripción de
texto de 1/2 a 1 página de sus elecciones y arquitectura.

El diseño debe soportar:
• Cargas variables
• Contar con HA (alta disponibilidad)
• Frontend en Js
• Backend con una base de datos relacional y una no relacional
• La aplicación backend consume 2 microservicios externos

# Desarrollo de la Prueba 1:
Aplicación utilizada: Draw.io (https://app.diagrams.net/)

# Diagrama de Red para Prueba 1:
![image](https://github.com/frangcalzada/Craftech-Desafio-2024/assets/40276177/c9f59c0a-12fc-4023-80f5-76416fda5ebe)

# WorkFlow del Diagrama:
* Usuario: el usuario interactua con el frontend desplegado en Amazon S3 a través de Amazon CloudFront para que exista una entrega rápida de contenido.
* Frontend en JS: el frontend va a estar desarrollado en JS, se va alojar en Amazon S3 y va a ser distribuído globalmente por Amazon CloudFront para ganar escabilidad y baja latencia.
* Backend en AWS: el backend va a ser desarrollado como microservicios en instancias de Amazon EC2 y manejado por Auto Scaling Groups para asegurar HA (Alta disponibilidad).
* Amazon RDS: base de datos relacional que va a ser gestionada para almacenar datos estructurados y con opción de respaldo automático y escalabilidad vertical.
* Amazon DynamoDB: base de datos NoSQL que va a ser gestionada para almacenar datos no estructurados con escalabilidad horizontal automática y HA.
* Amazon API Gateway: maneja las solicitudes de API que provinen del frontend JS y ls rutas hacia los microservicios backend y los microservicios externos.



