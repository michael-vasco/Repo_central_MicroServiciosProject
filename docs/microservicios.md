
# inventario de microservicios (equipo)

## tabla resumen

| Servicio (ID)  | Descripción breve                       | Repo URL                               | Base URL (EC2)             | Swagger UI                            | Responsable               | Estado      |
| -------------- | --------------------------------------- | -------------------------------------- | -------------------------- | ------------------------------------- | ------------------------- | ----------- |
| usuario-service   | Autenticación JWT (login/refresh)       |  https://github.com/Nicolas-Lozano-Salazar/Usuario_serv  | http://<ip-o-dominio>:8081 | http://<ip-o-dominio>:8081/swagger-ui | nicolas lozano salazar  (@Nicolas-Lozano-Salazar) | Finalizado |
| facultad-service    | CRUD facultades              | https://github.com/michael-vasco/Facultad-Service.git    | http://<ip-o-dominio>:8082 | http://<ip-o-dominio>:8082/swagger-ui |  michael stiven vasco cardenas (@michael-vasco) | En progreso |
| curso-service  | CRUD para cursos dentro de programas   | https://github.com/Santi202305/Corse-Service.git  | http://<ip-o-dominio>:8083 | http://<ip-o-dominio>:8083/swagger-ui |  santiago garcia granda (@santi202305) | En progreso   |
| programa-service | CRUD para programas dentro de facultades | none | http://<ip-o-dominio>:8084 | http://<ip-o-dominio>:8084/swagger-ui | michael stiven vasco cardenas  (@michael-vasco) | Pendiente   |

### *usuario-service*

* *Responsable:* Nicolás Lozano (@Nicolas-Lozano-Salazar)
* *Repositorio:* https://github.com/Nicolas-Lozano-Salazar/Usuario_serv
* *Docker Hub:* nicolasls/usuario-service:latest
* *Base URL (EC2):* http://<ip-o-dominio>:8080
* *Swagger UI:* http://<ip-o-dominio>:8080/swagger-ui

---

### *Entidades principales*

#### Usuario

| Campo          | Tipo   | Restricciones             |
| -------------- | ------ | ------------------------- |
| id             | Long   | Autogenerado              |
| cedula         | Long   | Único, no nulo            |
| contrasena     | String | Entre 6 y 100 caracteres  |
| correo         | String | Único, formato válido     |
| nombreCompleto | String | Entre 2 y 100 caracteres  |
| rol            | String | Máx. 50 caracteres        |
| telefono       | Long   | Numérico, máx. 15 dígitos |

---

### *Endpoints principales*

| Método     | Ruta                                           | Descripción                    |
| ---------- | ---------------------------------------------- | ------------------------------ |
| *GET*    | /api/v1/usuario-service/usuarios             | Lista todos los usuarios       |
| *GET*    | /api/v1/usuario-service/usuarios/page/{page} | Lista usuarios por página      |
| *GET*    | /api/v1/usuario-service/usuarios/{id}        | Busca un usuario por ID        |
| *POST*   | /api/v1/usuario-service/usuarios             | Crea un nuevo usuario          |
| *PUT*    | /api/v1/usuario-service/usuarios             | Actualiza un usuario existente |
| *DELETE* | /api/v1/usuario-service/usuarios             | Elimina un usuario existente   |

---

### *Tecnologías*

* *Spring Boot 3.2.x*
* *JDK 23*
* *Jakarta Validation (Bean Validation)*
* *Spring Data JPA*
* *Maven*
* *Docker*
* *Swagger* (pendiente integración)

---

### *Características*

* API REST funcional con validaciones de entrada.
* Manejo de excepciones personalizadas (UsuarioNoEncontradoException, ValidationException, etc.).
* Paginación implementada con PageRequest.
* Entidad Usuario completamente validada con anotaciones @NotNull, @Email, @Size, @Digits.
* Contenerización lista para despliegue en Docker.
* Compatible con Swagger UI para documentación automática.

---

## *Responsables*

| Rol                     | Nombre          | Usuario GitHub          | Observaciones              |
| ----------------------- | --------------- | ----------------------- | -------------------------- |
| Autor del microservicio | Nicolás Lozano  | @Nicolas-Lozano-Salazar | Desarrollo y documentación |
| DevOps                  | Nicolás Lozano  | @Nicolas-Lozano-Salazar | Imagen Docker y despliegue |
| Scrum Master            | michael stiven vasco cardenas  | @michael-vasco | — |

---

 *Fecha:* 2025-11-08

### *Cambios relevantes*

* Implementación completa del CRUD de Usuario.
* Validaciones de datos y manejo de errores personalizado.
* Integración de paginación en endpoints de lectura.
* Pendiente: integración final de Swagger UI y despliegue en EC2.


---

### *facultad-service*

* *Responsable:*  michael stiven vasco cardenas (@michael-vasco)
* *Docker Hub:* michaelvasco/facultad-service:latest
* *Base URL (EC2):* http://<ip-o-dominio>:8080
* *Swagger UI:* http://<ip-o-dominio>:8080/swagger-ui

---

### *Entidades principales*

#### facultad

| Campo          | Tipo   | Restricciones             |
| -------------- | ------ | ------------------------- |
| id             | Long   | Autogenerado              |
| nombre         | String   | no vacio, no nulo, entre 2 a 50 caracteres            |
| contraseña     | String | Entre 6 y 100 caracteres  |
| descripcion         | String | no mas de 255 caracteres |
| direccion | String | Entre 5 y 100 caracteres, no nulo, no vacio  |
| ciudad            | String | entre 2 a 50 caracteres, no nulo, no vacio        |
| cupos       | Integer   | Numérico, no nulo, no vacio, entre 1 a 500 cupos |

---

### *Endpoints principales*

| Método     | Ruta                                           | Descripción                    |
| ---------- | ---------------------------------------------- | ------------------------------ |
| *GET*    | /api/v1/facultad-service/facultades             | Lista todos los facultades       |
| *GET*    | /api/v1/facultad-service/facultades/page/{page} | Lista facultades por página      |
| *GET*    | /api/v1/facultad-service/facultades/{id}        | Busca un facultad por ID        |
| *POST*   | /api/v1/facultad-service/facultades             | Crea un nuevo facultad          |
| *PUT*    | /api/v1/facultad-service/facultades             | Actualiza un facultad existente |
| *DELETE* | /api/v1/facultad-service/facultades             | Elimina un facultad existente   |

---

### *Tecnologías*

* *Spring Boot 3.4.4*
* *JDK 21*
* *Jakarta Validation (Bean Validation)*
* *Spring Data JPA*
* *Maven*
* *Docker*  (pendiente integración)
* *Swagger* (pendiente integración)

---

### *Características*

* API REST funcional con validaciones de entrada.
* Manejo de excepciones personalizadas (FacultadNoEncontradoException, ValidationException, etc.).
* Paginación implementada con PageRequest.
* Entidad Facultad completamente validada con anotaciones @NotNull, @Email, @Size, @Digits.
* Compatible con Swagger UI para documentación automática.

---

## *Responsables*

| Rol                     | Nombre          | Usuario GitHub          | Observaciones              |
| ----------------------- | --------------- | ----------------------- | -------------------------- |
| Autor del microservicio | michael stiven vasco cardenas  | @michael-vasco | Desarrollo y documentación |
| DevOps                  | michael stiven vasco cardenas  | @michael-vasco | none |

---

 *Fecha:* 2025-11-11

### *Cambios relevantes*

* Implementación completa del CRUD de Facultad.
* Validaciones de datos y manejo de errores personalizado.
* Integración de paginación en endpoints de lectura.
* Pendiente: integración final de Swagger UI y despliegue en EC2.

---

### OvaArquitectura - Service
- *Responsable:* German Andres Rojas Cardona (@yermanandress)
- *Repositorio:* https://github.com/yermanandress/ova-arquitectura
- *Docker Hub:* germanandress/ovaarq-app:latest
- *Base URL (EC2):* http://172-31-14-229:8080
- *Swagger UI:* http://<ip-o-dominio>:<puerto>/swagger-ui  
- *Entidades principales:*  
  - <EntidadPrincipal> (campos clave: …)  
- *Endpoints mínimos:*  
- POST /api/ova/pregunta → guardar nueva pregunta
- GET /api/ova/pregunta → obtener pregunta aleatoria
- GET /api/ova/validar/{id}/{indice} → validar respuesta por índice
- *Tecnologías:* Spring Boot 3.2.5, JNI, C Native, Docker, JDK 21  
- *Checklist de verificación (semanal):*  
  - [✔] Compila y arranca local  
  - [✔] /actuator/health *UP* en local  
  - [ ] Swagger accesible en EC2  
  - [✔] Push diario con commits significativos  
  - [✔] Historia/tarea en Jira: *En progreso* → *Terminado* al finalizar

---

## responsables (vista rápida)

| Rol | Nombre | Usuario GitHub | Observaciones |
|---|---|---|---|
| Autor De Ova Arquitectura | German Rojas | @yermanandress | Microservicio De Cuestionario Arquitectura |
| DevOps | German Rojas | @yermanandress | Docker y despliegue |

---

## notas de la semana
- Fecha: 2025-11-08

### Cambios relevantes:

  - Implementación de JNI con librería nativa libovaarq.so
  - Endpoints GET y POST para preguntas funcionando
  - Integración básica con Docker para despliegue local

### Bloqueos/riesgos:

  - Conflictos de puertos al levantar Docker
  - Dependencia de librería nativa y cJSON (libovaarq.so)
  - Swagger aún no desplegado en EC2

---

### lagrange-service
- *Responsable:* Javier Morán (@Javier-Moran-Jurado)  
- *Repositorio:* https://github.com/Javier-Moran-Jurado/Lib-Lagrange.git  
- *Docker Hub:* javier200521/lagrange-app:latest  
- *Base URL (EC2):* http://18.119.253.236:8080  
- *Swagger UI:* http://<ip-o-dominio>:8080/swagger-ui  
- *Entidades principales:*  
  - InterpolacionRequest (puntos: double[][], x: double)  
- *Endpoints:*  
  - POST /api/lagrange/interpolar - Interpolación con puntos personalizados  
  - GET /api/lagrange/test - Prueba con valores predefinidos  
- *Tecnologías:* Spring Boot 3.2.5, JNI, C Native, Docker, JDK 21  
- *Características:*  
  -  Integración JNI con librería nativa C  
  -  Contenerizado con Docker  
  -  API REST funcional  
  -  Interpolación polinómica de Lagrange  

---

## responsables (vista rápida)

| Rol | Nombre | Usuario GitHub | Observaciones |
|---|---|---|---|
| Autor de lagrange-service | Javier Morán | @Javier-Moran-Jurado | Microservicio de interpolación numérica |
| DevOps | Javier Morán | @Javier-Moran-Jurado | Docker y despliegue |
| Scrum Master | michael stiven vasco cardenas | @michael-vasco | — |

---

## notas de la semana
- Fecha: 2025-11-07  
- Cambios relevantes:  
  - Spring Boot + JNI integrado exitosamente  
  -  Endpoints REST /api/lagrange/interpolar y /test funcionando  
  -  Docker image construida y lista para despliegue  
  -  Pendiente: Configurar Swagger UI  
  -  Pendiente: Despliegue en EC2 con IP pública

---

## roundrobin-service
- Responsable: Nicolás Lozano (@nicolasls)
- Repositorio: https://github.com/Nicolas-Lozano-Salazar/Ova_Operativos
- Docker Hub: nicolasls/springboot-jni:latest
- Base URL (EC2): http://<ip-o-dominio>:8080
- Swagger UI: http://<ip-o-dominio>:8080/swagger-ui
- Entidades principales:
- ProcesosDTO (id: int, llegada: int, rafaga: int, prioridad: int)
- Endpoints:
- POST /api/sistemas-operativos/roundrobin/{quantum} → Ejecuta el algoritmo Round Robin
- Tecnologías: Spring Boot 3.2.x, JNI (Java Native Interface), C/C++ nativo, Docker, JDK 26
- Características:
- Integración JNI con librería nativa libRoundRobin
- Contenerizado con Docker
- API REST funcional
- Simulación completa del algoritmo de planificación Round Robin
  
## responsables 

| Rol | Nombre | Usuario GitHub | Observaciones |
|---|---|---|---|
| Autor de Ova_Operativos | Nicolas Lozano | @Nicolas-Lozano-Salazar | Ova de Sistemas Operativos |
| DevOps | Nicolas Lozano | @Nicolas-Lozano-Salazar | Docker y despliegue |
| Scrum Master | Nombre Apellido | @usuario | — |

Fecha: 2025-11-08
- Cambios relevantes:

  - Integración completa entre Spring Boot y la librería JNI
  - Endpoint /api/sistemas-operativos/roundrobin/{quantum} funcionando correctamente 
  - Imagen Docker construida y lista para subir a Docker Hub
  - Pendiente: Integrar documentación con Swagger UI
  - Pendiente: Despliegue final en instancia EC2 con IP pública

---

### corse-service

* Responsable:  Santiago García (@Santi202305)  
* Repositorio base (.zip): https://github.com/Santi202305/Curse-Service.git  
* Docker Hub: santiago2305/corse_service-app:latest  
* Base URL (EC2): http://<ip-o-dominio>:8080  
* Swagger UI: http://<ip-o-dominio>:8080/swagger-ui  

---

### Entidades principales

#### curso

| Campo        | Tipo    | Restricciones |
|--------------|---------|---------------|
| id           | Long    | Autogenerado |
| nombre       | String  | No nulo, no vacío, 2–50 caracteres |
| descripcion  | String  | Máximo 255 caracteres |
| cupo         | Integer | No nulo, numérico, entre 1 y 500 |

---

### Endpoints principales

Controlador: CursoRestController.java  
Versión detectada: /api/v1/cursos

| Método | Ruta | Descripción |
|--------|-------|-------------|
| GET | /api/v1/cursos | Lista todos los cursos |
| GET | /api/v1/cursos/{id} | Busca un curso por ID |
| POST | /api/v1/cursos | Crea un nuevo curso |
| PUT | /api/v1/cursos/{id} | Actualiza un curso existente |
| DELETE | /api/v1/cursos/{id} | Elimina un curso por ID |

---

### Tecnologías

* Spring Boot (versión del proyecto en pom.xml)
* JDK 17+  
* Spring Web  
* Spring Data JPA  
* Validaciones básicas por anotaciones  
* SQL Script (Curso-Serve.sql)  
* Maven  
* Docker  
* Swagger 

---

### Características

* API REST funcional para gestión de cursos.
* Manejo de excepciones personalizado mediante GlobalExceptionHandler.
* Entidad Curso con atributos validados y mapeados con JPA.
* Script SQL incluido para carga inicial de datos.
* Configuración basada en application.yml.

---

## Responsables

| Rol                     | Nombre          | Usuario GitHub   | Observaciones |
|-------------------------|------------------|------------------|---------------|
| Autor del microservicio | Santiago García | @Santi202305 | Desarrollo de CRUD y clientes REST |
| DevOps                  | Santiago García | @Santi202305 | Dockerfile implementado |
---

Fecha: 2025-11-11

### Cambios relevantes

* Implementación completa del CRUD de Curso.
* Manejo de excepciones centralizado.
* Organización del proyecto en capas (delivery, domain, infraestructura HTTP).

---
