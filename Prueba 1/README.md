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
* Amazon CloudFront: permite distribuir el contenido estático del frontend almacenado en Amazon S3 y de esa manera minimizar la latencia y mejorar la experiencia de usuario.
* Frontend en JS: el frontend va a estar desarrollado en JS, se va alojar en Amazon S3 y va a ser distribuído globalmente por Amazon CloudFront.
* Amazon API Gateway: actua como punto de entrada y de esa manera maneja las solicitudes de API que provinen del frontend JS y las rutas hacia los microservicios backend y los microservicios externos.
* Backend en AWS: el backend va a ser desarrollado como microservicios en instancias de Amazon EC2 y manejado por Auto Scaling Groups para asegurar HA (Alta disponibilidad). Va a recibir las solicitudes
  del frontend a través de API Gateway, procesar la lógica de negocio y acceder a las bases de datos (Amazon RDS y Amazon DynamoDB).
* Amazon RDS: base de datos relacional que va a ser gestionada para almacenar datos estructurados y con opción de respaldo automático y escalabilidad vertical.
* Amazon DynamoDB: base de datos NoSQL que va a ser gestionada para almacenar datos no estructurados con escalabilidad horizontal automática y HA.

# Ejemplo de cómo funcionaría aplicado a una tienda online de libros:
Un usuario quiero comprar un libro en una tienda online. El sitio carga rápidamente gracias a CloudFront, que distribuye las imágenes y el diseño de la página desde Amazon S3.
Cuando el usuario hace click en "comprar", esa solicitud se envía a través de Amazon API Gateway al backend en AWS.
El backend en AWS verifica si el libro está disponible haciendo una consulta en Amazon DynamoDB (DB no relacional) y si es así, registra el pedido en Amazon RDS (DB relacional) para que el usuario
pueda pagarlo y recibirlo.
Gracias a la infraestructura de escalabilidad y de HA que nos brinda AWS nos aseguramos de que la compra se pueda realizar sin problemas y que el sitio web siga funcionando perfectamente para otros usuarios al
mismo tiempo.


