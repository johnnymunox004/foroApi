# FORO HUB CHALLENGE

![Balloons](https://raw.githubusercontent.com/johnnymunox004/foroApi/main/assets/balloons-4111586_1280.png)

Una plataforma donde los usuarios pueden plantear sus preguntas sobre determinados temas, creada con una API REST usando Spring para gestionar datos y relaciones entre usuarios y respuestas de un tema.

## Funcionalidades

Nuestra API se centrará específicamente en los tópicos, y debe permitir a los usuarios:

### Crear un CRUD (CREAR, LEER, ACTUALIZAR, ELIMINAR):

- Crear un nuevo tópico
- Mostrar todos los tópicos creados
- Mostrar un tópico específico
- Actualizar un tópico
- Eliminar un tópico

Validaciones realizadas según las reglas de negocio.

### Implementación de una base de datos relacional para la persistencia de la información

### Servicio de autenticación/autorización para restringir el acceso a la información

## Programas, archivos y versiones utilizados:

- **Java JDK:** versión 17 en adelante - [Descarga la última versión LTS de Java gratuita](https://www.oracle.com/java/technologies/javase-jdk17-downloads.html).
- **Maven:** versión 4 en adelante.
- **Spring Boot:** versión 3 en adelante.
- **MySQL:** versión 8 en adelante.
- **IDE (Entorno de desarrollo integrado):** IntelliJ IDEA (opcional).

## Configuración al crear Spring Initializr:

- **Java:** versión 17 en adelante.
- **Maven:** Initializr utiliza la versión 4.
- **Spring Boot:** Proyecto en formato JAR.
- **Dependencias para agregar al crear el proyecto con Spring Initializr:**
  - Lombok
  - Spring Web
  - Spring Boot DevTools
  - Spring Data JPA
  - Flyway Migration
  - MySQL Driver
  - Validation
  - Spring Security

## Construcción de la base de datos:

Algunos enlaces importantes tanto para la instalación de MySQL como para la configuración de la base de datos a través del proyecto Spring:

- [MySQL Installer](https://dev.mysql.com/downloads/installer/)

Agregar algunas dependencias en nuestro `pom.xml` (Validation, MySQL Driver, Spring Data JPA, Flyway Migration).

Crear un tópico con la siguiente información: id, título, mensaje, fecha de creación, status (estado del tópico), autor, curso.

![Diagrama de Base de datos](file:///C:/Users/USER/Desktop/ForoHubApi/assets/diagrama_base_de_datos_forohub.png)

Nota: se representa una base de datos más completa pero no se implementan todas las tablas presentes en él - es suficiente centrarse en la tabla de tópicos.

## CRUD (CREATE, READ, UPDATE, DELETE):

La API cuenta con:

- Un endpoint para el registro de tópicos, que acepta solicitudes del tipo POST para la URI `/tópicos`. Los datos (título, mensaje, autor y curso) deben ser enviados en el cuerpo de la solicitud, en formato JSON.
- Un endpoint para el listado de un tópico específico, que acepta solicitudes del tipo GET para la URI `/tópicos/{id}`. Los datos (título, mensaje, fecha de creación, estado, autor y curso) deben ser devueltos en el cuerpo de la respuesta, en formato JSON.
- Un endpoint para listar todos los tópicos, que acepta solicitudes del tipo GET para la URI `/tópicos`. Se muestran los primeros 10 resultados ordenados por fecha de creación del tópico en orden ascendente.
- Un endpoint para la actualización de los datos de un determinado tópico, que acepta solicitudes del tipo PUT para la URI `/tópicos/{id}`.
- Un endpoint para la eliminación de un tópico específico, que acepta solicitudes del tipo DELETE para la URI `/tópicos/{id}`.

## Pruebas de la API:

Las pruebas de las funcionalidades de la API pueden realizarse utilizando alguna herramienta de pruebas de API, como Postman o Insomnia:

- [Postman](https://www.postman.com/)
- [Insomnia](https://insomnia.rest/)

![Registro Tópico](file:///C:/Users/USER/Desktop/ForoHubApi/assets/Registro_Topico.png)

## Autenticación y configuración de Seguridad:

Solo los usuarios autenticados pueden interactuar con la API. Para configurar la autenticación se utilizó Spring Security. Se implementó un mecanismo de autenticación en la API, modificando la estructura de la base de datos para incluir una nueva tabla para almacenar los datos de autenticación de los usuarios. Se utilizó Flyway Migration para la creación de migraciones.

### Generar un token con JWT:

Para agregar mayor seguridad, se requiere tokens para autenticación. El JWT (JSON Web Token) es un estándar utilizado para compartir información entre cliente y servidor que será muy útil en esta tarea. Esta biblioteca es importante precisamente para poder generar el token en el estándar JWT y así agregarlo en la configuración de seguridad de nuestro proyecto, creando una clase DTO `UsernamePasswordAuthenticationToken` para recibir el nombre de usuario y contraseña.

- Web: [JWT.IO](https://jwt.io/)
