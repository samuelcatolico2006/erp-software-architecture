# Restricciones Arquitectónicas

## Decisiones Tecnológicas

### Backend
- **Lenguaje:** Java 17
- **Framework:** Spring Boot 3.x
- **Arquitectura:** Microservicios (Módulo de Compras como microservicio independiente)
- **API:** RESTful con OpenAPI 3.0 (Swagger)
- **Seguridad:** Spring Security + JWT (JSON Web Tokens)
- **ORM:** Spring Data JPA (Hibernate)
- **Base de Datos:** PostgreSQL 15

### Frontend
- **Framework:** React 18
- **Lenguaje:** TypeScript
- **Estado:** Redux Toolkit
- **UI:** Material-UI (MUI) o Tailwind CSS
- **Comunicación:** Axios para consumo de API REST

### Infraestructura
- **Contenerización:** Docker
- **Orquestación:** Kubernetes (opcional para producción)
- **CI/CD:** GitHub Actions
- **Monitoreo:** Prometheus + Grafana
- **Logging:** ELK Stack (Elasticsearch, Logstash, Kibana)

## Restricciones Técnicas

| Categoría | Restricción | Justificación |
|-----------|-------------|---------------|
| **Arquitectura** | Debe ser modular y escalable horizontalmente | Crecimiento futuro del negocio |
| **Seguridad** | Todos los endpoints deben estar autenticados | Protección de datos sensibles |
| **Datos** | Transacciones ACID para operaciones críticas | Integridad de datos de compras |
| **Integración** | API REST para futuras integraciones | Interoperabilidad con otros sistemas |
| **Despliegue** | Debe soportar contenedores Docker | Facilidad de despliegue en cualquier entorno |
| **Base de Datos** | Migraciones manejadas con Flyway | Control de versiones de esquema |

## Restricciones de Negocio

| Restricción | Descripción |
|-------------|-------------|
| **Cumplimiento** | Debe cumplir con normativas fiscales locales (facturación electrónica) |
| **Idioma** | Interfaz en español |
| **Moneda** | Operaciones en Pesos Colombianos (COP) |
| **Horario** | Disponible 24/7 |
| **Auditoría** | Todas las transacciones deben ser auditables |

## Restricciones de Proyecto

| Restricción | Descripción |
|-------------|-------------|
| **Plazo** | MVP en 3 meses |
| **Equipo** | 4 desarrolladores (2 backend, 2 frontend) |
| **Presupuesto** | Limitado para infraestructura en la nube |
| **Documentación** | Documentación técnica en arc42 + código |
