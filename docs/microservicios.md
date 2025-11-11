
# inventario de microservicios (equipo)

## tabla resumen

| Servicio (ID)  | Descripción breve                       | Repo URL                               | Base URL (EC2)             | Swagger UI                            | Responsable               | Estado      |
| -------------- | --------------------------------------- | -------------------------------------- | -------------------------- | ------------------------------------- | ------------------------- | ----------- |
| usuario-service   | Autenticación JWT (login/refresh)       |  https://github.com/Nicolas-Lozano-Salazar/Usuario_serv  | http://<ip-o-dominio>:8081 | http://<ip-o-dominio>:8081/swagger-ui | nicolas lozano salazar  (@Nicolas-Lozano-Salazar) | Finalizado |
| facultad-service    | CRUD facultades              | https://github.com/michael-vasco/Facultad-Service.git    | http://<ip-o-dominio>:8082 | http://<ip-o-dominio>:8082/swagger-ui |  michael stiven vasco cardenas (@michael-vasco) | En progreso |
| curso-service  | CRUD para cursos dentro de programas   | https://github.com/Santi202305/Corse-Service.git  | http://<ip-o-dominio>:8083 | http://<ip-o-dominio>:8083/swagger-ui |  santiago garcia granda (@santi202305) | En progreso   |
| programa-service | CRUD para programas dentro de facultades | none | http://<ip-o-dominio>:8084 | http://<ip-o-dominio>:8084/swagger-ui | michael stiven vasco cardenas  (@michael-vasco) | Pendiente   |


## responsables (vista rápida)

| Rol | Nombre | Usuario GitHub | Observaciones |
|---|---|---|---|
| Scrum Master |  michael stiven vasco cardenas | @michael-vasco | — |
| DevOp | santiago garcia granda  | @santi202305 | EC2, puertos, dominios |
| DevOps | nicolas lozano salazar  | @nicolas-lozano-salazar | EC2, puertos, dominios |
| DevOps |  Javier eduardo moran  | @javier-eduardo-moran-jurado | http://18.119.253.236:8080 |
| DevOps | german andres rojas  | @yermanandress | http://172-31-14-229:8080 |
| Autor de servicio | nicolas lozano salazar | @nicolas-lozano-salazar | usuario-service |
| Autor de servicio | michael stiven vasco cardenas | @michael-vasco | facultad-service |
| Autor de servicio | santiago garcia granda | @santi202305 | curso-service |


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
