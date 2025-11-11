
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

 *Fecha:* 2025-11-08

### *Cambios relevantes*

* Implementación completa del CRUD de Usuario.
* Validaciones de datos y manejo de errores personalizado.
* Integración de paginación en endpoints de lectura.
* Pendiente: integración final de Swagger UI y despliegue en EC2.


---

## *Responsables*

| Rol                     | Nombre          | Usuario GitHub          | Observaciones              |
| ----------------------- | --------------- | ----------------------- | -------------------------- |
| Autor del microservicio | Nicolás Lozano  | @Nicolas-Lozano-Salazar | Desarrollo y documentación |
| DevOps                  | Nicolás Lozano  | @Nicolas-Lozano-Salazar | Imagen Docker y despliegue |
| Scrum Master            | michael stiven vasco cardenas  | @michael-vasco | — |

---



## notas de la semana

- Fecha: 2025-11-11  
- Cambios relevantes:  
  - se termino el servicio de usuario.
  - los ovas de arquitectura, sistemas operativos y analisis numerico han sido acabados y revisados
  - los servicios de facultad y curso se han puesto en revision
- Bloqueos/riesgos:  
  - problemas con las cuentas de aws para el uso de la instancia de EC2
  - inconvenientes con el manejo de docker
  - problemas de manejo de contraseñas en la base de datos
