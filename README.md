# Prueba Técnica - Gestión de Animales

Esta aplicación Full Stack permite gestionar información relacionada con animales, ofreciendo funcionalidades para crear, leer y eliminar (CRD) registros de diferentes tipos de animales.

## Características principales

- Gestión de animales con información detallada (nombre, tipo, descripción, enlace a Wikipedia, imagen)
- Backend desarrollado con NestJS y documentado con Swagger
- Frontend implementado con ReactJS y TypeScript
- Base de datos relacional MySQL/MariaDB con Prisma como ORM

## Requisitos del Proyecto
La solución debe incluir los siguientes componentes:
- [X] Una API Backend desarrollada en NestJS, documentada con Swagger, que exponga los endpoints necesarios para la gestión de los animales.
- [X] Una interfaz Frontend desarrollada en ReactJS con TypeScript, que consuma los datos desde la API y permita al usuario interactuar de forma clara e intuitiva.
- [X] Un sistema de persistencia de datos usando una base de datos relacional MySQL o MariaDB.

## Criterios de Evaluación

Se tendrán en cuenta aspectos como:
- Organización del código
- Uso de buenas prácticas de desarrollo
- Manejo de excepciones
- Diseño de la interfaz y experiencia de usuario (UX)
- Funcionalidad general del sistema

El repositorio con todo el código debe ser subido a GitHub y enviado al siguiente correo con tu nombre completo: jevojob@gmail.com. Una vez finalizada la prueba, el participante deberá realizar un pitch de 5 minutos en el que explique, según su criterio, los aspectos más relevantes que haya desarrollado o implementado durante la prueba técnica.

## Puntos Extra

### Flujo de autenticación con JWT

Para implementar la autenticación con JWT primero lo que haría es instalar las dependencias necesarias para trabajar con esta atutenticación, seguidamente crearía un nuevo schema para prisma el cual sería User y le daría los datos y tipos de datos correspondientes, de aquí creo el módulo de autenticación el cual estaría compuesto por un Auth Module, service y controller y utilizaría JwStrategy para definir la estrategía de verificación del token, además usaría JwtAuthGuard para proteger las rutas que requieren de autenticación como lo podría ser en este caso eliminar un animal del catálogo. Luego dejando de lado la implementación expondría los endpoints para la autenticación y protegería las rutas como lo mencioné anteriormente. Ya en cuanto al flujo de la autenticación primero sería el registro de usuario donde el frontend envia las credenciales al backend y este valida los datos y los guarda en la base de datos mysql. Luego está el inició de sesión que similar al registro lo que haría es tomar las credenciales enviadas del frontend validarlas y si lo son entonces generar un token JWT con un payload que incluye el id y el email de usuario para así retornar el token al frontend, este token se almacena en el cliente en el sessionstorage y así puedo acceder a él cuando lo necesite verificar en el frontend

### Despliegue de la solución

El despliegue para el frontend lo haría en Vercel ya que es demasiado sencillo y rápido, además de que a pesar de que tenemos una página estática en este momento quizá a futuro se puede implementar más cosas los cuales la conviertan en una página dinámica y teniendola en vercel nos facilitaría este proceso por lo que nos ofrece un firewall integrado y permite generar el dominio y la certificación SSL de manera automática lo que nos evita trabajo a nosotros. Para hacerlo ingresaría a Vercel y vincularía el repositorio donde lo tengo guardado para que así vercel puede hacer los despliegues por cada commmit que se haga esto teniendo en cuenta que en desarrollo por cada funcionalidad que se agregue se debe de testear en local haciendo una compilación del código para que así cuando se haga el push en github se sepa con certeza que el código se desplegará a producción efectivamente.

Para el backend utilizaría render, la cual es una herramienta sencilla y ofrece de manera rápida un despliegue del backend, sin embargo el único pero de esta es que para acceer a funcionalidades que son necesarias como ejecutar comandos desde la terminal pues se debe adquirir una suscripción, sin embargo es bastante útil ya que no es tan costosa y para la facilidad que ofrece. Por otro lado esta también nos permite conectarnos de manera segura desde cualquier conexión así que podríamos consumir esta url desde el frontend sin nigún problema.
Al igual que con vercel el procedimiento es prácticamente el mismo, lo único que cambia es la plataforma.

Estas herramientas son las que utilizaría para desplegar la solución porque son las más fáciles de utilizar sin necesidad de tener que hacer muchas maniobras como por ejemplo sería AWS, la cual es excelente pero aparte de la complejidad que tiene tiene costos elevados para proyectos tan simples como estos.