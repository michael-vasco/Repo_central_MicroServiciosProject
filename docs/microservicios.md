
# inventario de microservicios (equipo)

## tabla resumen

| Servicio (ID)  | Descripción breve                       | Repo URL                               | Base URL (EC2)             | Swagger UI                            | Responsable               | Estado      |
| -------------- | --------------------------------------- | -------------------------------------- | -------------------------- | ------------------------------------- | ------------------------- | ----------- |
| usuario-service   | servicio de guardado y gestion de usuarios       |  https://github.com/Nicolas-Lozano-Salazar/Usuario_serv  | http://<ip-o-dominio>:8081 | http://<ip-o-dominio>:8081/swagger-ui | nicolas lozano salazar  (@Nicolas-Lozano-Salazar) | Finalizado |
| facultad-service    | CRUD facultades              | https://github.com/michael-vasco/Facultad-Service.git    | http://<ip-o-dominio>:8082 | http://<ip-o-dominio>:8082/swagger-ui |  michael stiven vasco cardenas (@michael-vasco) | finalizado |
| curso-service  | CRUD para cursos dentro de programas   | https://github.com/Santi202305/Corse-Service.git  | http://<ip-o-dominio>:8083 | http://<ip-o-dominio>:8083/swagger-ui |  santiago garcia granda (@santi202305) | finalizado   |
| programa-service | CRUD para programas dentro de facultades | https://github.com/michael-vasco/Programa-service.git | http://<ip-o-dominio>:8084 | http://<ip-o-dominio>:8084/swagger-ui | michael stiven vasco cardenas  (@michael-vasco) | finalizado   |
| lagrange-service | Ova de analisis numerico | https://github.com/Javier-Moran-Jurado/Lib-Lagrange.git | http://<ip-o-dominio>:8084 | http://<ip-o-dominio>:8084/swagger-ui | javier edurado moran  (javier-moran-jurado) | finalizado   |
| ovaarquitectura-service | Ova de arquitectura de computadores | https://github.com/yermanandress/ova-arquitectura | http://<ip-o-dominio>:8084 | http://<ip-o-dominio>:8084/swagger-ui | german andres rojas  (@yermanandres) | finalizado   |
| roundrobin-service | Ova de sistemas operativos | https://github.com/Nicolas-Lozano-Salazar/Ova_Operativos | http://<ip-o-dominio>:8084 | http://<ip-o-dominio>:8084/swagger-ui | nicolas lozano salazar  (@nicolas-lozano-salazar) | finalizado   |
| Angular-app-web | Sistema web de gestion de servicios en linea | none | http://<ip-o-dominio>:8084 | http://<ip-o-dominio>:8084/swagger-ui | santiago garcia granda  (@santi202305) | finalizado   |

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
* *Docker*  
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
* Docker Hub: santiago2305/corse_service-corse-service:latest  
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

* Implementación completa del CRUD de Curso.
* Manejo de excepciones centralizado.
* Organización del proyecto en capas (delivery, domain, infraestructura HTTP).
  
---

### *programa-service*

* *Responsable:*  michael stiven vasco cardenas (@michael-vasco)
* *Docker Hub:* michaelvasco/programa-service:latest
* *Base URL (EC2):* http://<ip-o-dominio>:8080
* *Swagger UI:* http://<ip-o-dominio>:8080/swagger-ui

---

### *Entidades principales*

#### programa

| Campo          | Tipo   | Restricciones             |
| -------------- | ------ | ------------------------- |
| id             | Long   | Autogenerado              |
| nombre         | String   | no vacio, no nulo, entre 2 a 50 caracteres            |
| descripcion         | String | no mas de 255 caracteres |
| cupos       | Integer   | Numérico, no nulo, no vacio, entre 1 a 500 cupos |

---

### *Endpoints principales*

| Método     | Ruta                                           | Descripción                    |
| ---------- | ---------------------------------------------- | ------------------------------ |
| *GET*    | /api/v1/programa-service/programas             | Lista todos los facultades       |
| *GET*    | /api/v1/programa-service/programas/page/{page} | Lista facultades por página      |
| *GET*    | /api/v1/programa-service/programas/{id}        | Busca un facultad por ID        |
| *POST*   | /api/v1/programa-service/programas             | Crea un nuevo facultad          |
| *PUT*    | /api/v1/programa-service/programas             | Actualiza un facultad existente |
| *DELETE* | /api/v1/programa-service/programas             | Elimina un facultad existente   |

---

### *Tecnologías*

* *Spring Boot 3.4.4*
* *JDK 21*
* *Jakarta Validation (Bean Validation)*
* *Spring Data JPA*
* *Maven*
* *Docker*
* *Swagger* (pendiente integración)

---

### *Características*

* API REST funcional con validaciones de entrada.
* Manejo de excepciones personalizadas (ProgramaNoEncontradoException, ValidationException, etc.).
* Paginación implementada con PageRequest.
* Entidad Programa completamente validada con anotaciones @NotNull, @Email, @Size, @Digits.
* Compatible con Swagger UI para documentación automática.

---

## *Responsables*

| Rol                     | Nombre          | Usuario GitHub          | Observaciones              |
| ----------------------- | --------------- | ----------------------- | -------------------------- |
| Autor del microservicio | michael stiven vasco cardenas  | @michael-vasco | Desarrollo y documentación |
| DevOps                  | michael stiven vasco cardenas  | @michael-vasco | none |

---

 *Fecha:* 2025-11-23

### *Cambios relevantes*

* Implementación completa del CRUD de Programa.
* Validaciones de datos y manejo de errores personalizado.
* Integración de paginación en endpoints de lectura.
* Pendiente: integración final de Swagger UI y despliegue en EC2.

---


## Sistema de Gestión de Clientes - Angular

Aplicación web full-stack con Angular 17 y microservicios Spring Boot para gestión de clientes y usuarios.

[![Angular](https://img.shields.io/badge/Angular-17-red)](https://angular.io/)
[![TypeScript](https://img.shields.io/badge/TypeScript-5.2-blue)](https://www.typescriptlang.org/)
[![License](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)

---

## Descripción

Sistema completo que incluye:
- Autenticación con validaciones de seguridad
- Dashboard interactivo
- CRUD de clientes
- Diseño responsive
- Integración con microservicios

---

## Demo Rápida
```bash
# Clonar e instalar
git clone https://github.com/Santi202305/Angular-app-web.git
cd Angular-app-web
npm install

# Ejecutar
ng serve

# Abrir navegador
http://localhost:4200
```

**Credenciales de prueba:**
- Crear cuenta en `/registro`
- Contraseña: Mínimo 8 caracteres (Ej: `Abcd1234`)

---

## Arquitectura
```
Frontend (Angular)  →  API REST  →  Microservicios (Spring Boot)
                                    ├── Usuario Service (8080)
                                    └── Cliente Service (8081)
```

---

## Estructura del Proyecto
```
src/app/
├── components/
│   ├── clientes/           # Gestión de clientes
│   ├── cuestionario/       # Ova Arquitectura
│   ├── cursos/             # Gestion De Cursos
│   ├── dashboard/          # Panel principal
│   ├── lagrange/           # Ova Analisis Numerico
│   ├── login/              # Inicio de sesión
│   └── registro/           # Registro de usuarios
├── environments/
│   ├── environment.prod    # Gestión de clientes
│   └── environment         # Registro de usuarios
├── models/                 # Interfaces TypeScript
│   ├── clientes/           # Gestión de clientes
│   └── curso/              # Gestion De Cursos
├── services/               # Servicios HTTP
│   ├── cliente.service.ts
│   ├── curso.service.ts
│   └── validacion.service.ts
└── app.routes.ts           # Configuración de rutas
```

---

## Características Frontend

### Seguridad
- Validación de nombres (sin palabras ofensivas)
- Validación estricta de emails
- Contraseñas seguras (8+ chars, mayúsculas, minúsculas, números)
- Sanitización contra XSS
- Prevención de inyección SQL

### UI/UX
- Diseño responsive mobile-first
- Animaciones y transiciones suaves
- Validaciones en tiempo real
- Alertas con SweetAlert2

### Funcionalidades
| Módulo | Rutas | Descripción |
|--------|-------|-------------|
| Login | `/login` | Inicio de sesión |
| Registro | `/registro` | Crear cuenta nueva |
| Dashboard | `/dashboard` | Panel con menú lateral |
| Clientes | `/clientes` | Lista de clientes |
| Detalle | `/clientes/detalle/:id` | Ver/Eliminar cliente |
| Lagrange | `/lagrange` | Ova Analisis Numerico |
| Cuestionario | `/cuestionario` | Ova Arquitectura |

---

## Tecnologías

**Frontend:**
- Angular 17 (Standalone Components)
- TypeScript 5.2
- RxJS 7.8
- SweetAlert2
- CSS3 Responsive

**Backend (Microservicios):**
- Spring Boot 3.x
- PostgreSQL
- Docker & Docker Compose

---

## Servicios Backend

### Usuario Service
* **Puerto:** 8080
* **Base URL:** `http://localhost:8080`

**Endpoints:**
```
GET    /api/v1/usuario-service/usuarios
POST   /api/v1/usuario-service/usuarios
PUT    /api/v1/usuario-service/usuarios
DELETE /api/v1/usuario-service/usuarios
```

### Cliente Service
* **Puerto:** 8081
* **Base URL:** `http://localhost:8081`

**Endpoints:**
```
GET    /api/v1/cliente-service/clientes
GET    /api/v1/cliente-service/clientes/{id}
POST   /api/v1/cliente-service/clientes
PUT    /api/v1/cliente-service/clientes/{id}
DELETE /api/v1/cliente-service/clientes/{id}
```

---

## Instalación Completa

### 1. Frontend
```bash
# Clonar repositorio
git clone https://github.com/Santi202305/Angular-app-web.git
cd Angular-app-web

# Instalar dependencias
npm install

# Instalar SweetAlert2
npm install sweetalert2

# Ejecutar
ng serve
```

### 2. Backend (Docker)
```bash
# Crear compose.yaml
services:
  postgres:
    image: 'postgres:latest'
    environment:
      - 'POSTGRES_DB=curso_springboot'
      - 'POSTGRES_PASSWORD=a1b2c3d4'
      - 'POSTGRES_USER=devdb'
    ports:
      - '5432:5432'

  cliente-service:
    image: 'cliente-service:latest'
    ports:
      - '8081:8080'
    depends_on:
      - postgres

# Iniciar servicios
docker compose up -d

# Verificar
curl http://localhost:8081/api/v1/cliente-service/clientes
```

---

## Uso Rápido

1. **Registrarse:** Ve a `/registro` y crea una cuenta
2. **Login:** Inicia sesión con tus credenciales
3. **Dashboard:** Explora el menú lateral
4. **Clientes:** Click en "Clientes" para ver la lista
5. **Detalle:** Click en "Ver Detalle" para más información
6. **Eliminar:** Usa el botón rojo para eliminar (confirmación incluida)

---

## Validaciones Implementadas
```typescript
// Nombre de usuario
- Mínimo 2 caracteres
- Solo letras y espacios
- Sin palabras ofensivas

// Email
- Formato válido (@ejemplo.com)
- Sin caracteres especiales peligrosos

// Contraseña
- Mínimo 8 caracteres
- Al menos 1 mayúscula
- Al menos 1 minúscula
- Al menos 1 número
- Sin código HTML/JavaScript
```

---

## Autor

**Santiago García Granda**
- GitHub: [@Santi202305](https://github.com/Santi202305)
- Repositorio: [Angular-app-web](https://github.com/Santi202305/Angular-app-web.git)

---

## Versión Actual: v1.0.0

**Fecha:** 2025-01-15

### Completado
- Sistema de autenticación completo
- Dashboard funcional con menú lateral
- CRUD de clientes con validaciones
- Validaciones de seguridad (XSS, SQL injection)
- Diseño responsive mobile-first
- Integración con SweetAlert2

### En Desarrollo
- Integración JWT para tokens
- Guards de protección de rutas
- Deploy en servidor
- Tests unitarios y e2e
- PWA (Progressive Web App)

---

