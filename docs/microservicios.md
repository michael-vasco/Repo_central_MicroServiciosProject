
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




