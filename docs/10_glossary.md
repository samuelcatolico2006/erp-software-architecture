# Glosario

## Términos del Dominio - Módulo de Compras

Este glosario contiene las definiciones de los términos clave utilizados en el Módulo de Compras del sistema ERP. Su propósito es establecer un lenguaje común y claro entre todos los stakeholders del proyecto.

---

### Términos de Negocio

#### Producto
**Definición:** Bien o servicio que la empresa adquiere de un proveedor para su uso interno, transformación o venta. En el contexto del Módulo de Compras, es el artículo que se solicita mediante una orden de compra.

**Atributos clave:**
- Nombre
- Descripción
- Unidad de medida
- Precio de compra
- Estado (Activo/Inactivo)

**Ejemplo:** "Laptop Dell XPS 13", "Papel bond carta", "Servicio de mantenimiento"

---

#### Proveedor
**Definición:** Entidad (persona natural o jurídica) que suministra productos o servicios a la empresa. El proveedor es un actor clave en el proceso de compras.

**Atributos clave:**
- Nombre/Razón social
- RUC/NIT
- Teléfono
- Email
- Dirección
- Estado (Activo/Inactivo)

**Ejemplo:** "Dell Colombia S.A.S.", "Papelería El Lápiz", "Servicios Generales SAS"

---

#### Orden de Compra
**Definición:** Documento formal y vinculante que autoriza la adquisición de productos o servicios de un proveedor específico. Detalla cantidades, precios, condiciones de pago, plazos de entrega y términos de la transacción.

**Atributos clave:**
- Número de orden (único)
- Fecha de creación
- Proveedor
- Lista de productos con cantidades
- Monto total
- Estado
- Fecha de entrega esperada
- Condiciones de pago

**Estados posibles:**
- **Pendiente:** Orden creada, esperando aprobación
- **Aprobada:** Orden autorizada por el gestor de compras
- **Enviada:** Orden enviada al proveedor
- **Recibida:** Productos recibidos en almacén
- **Cancelada:** Orden anulada

**Ejemplo:** "OC-2025-00123 - Compra de laptops a Dell por valor de $10,500,000"

---

#### Catálogo de Productos
**Definición:** Listado estructurado y actualizado de todos los productos que la empresa puede adquirir, con sus características, especificaciones y precios de referencia.

**Propósito:**
- Centralizar la información de productos
- Facilitar la búsqueda y selección
- Mantener consistencia en las compras

---

#### Categoría
**Definición:** Clasificación agrupada de productos según características comunes para facilitar su organización, búsqueda y análisis.

**Ejemplos:**
- "Electrónicos"
- "Papelería"
- "Muebles de oficina"
- "Insumos de limpieza"

---

#### Unidad de Medida
**Definición:** Estándar utilizado para cuantificar productos, permitiendo estandarizar cantidades y precios en las transacciones de compra.

**Ejemplos:**
- **Unidades (un):** Para productos contables por pieza
- **Kilogramos (kg):** Para productos de peso
- **Litros (l):** Para líquidos
- **Metros (m):** Para productos lineales
- **Cajas (cj):** Para productos empaquetados

---

#### SKU (Stock Keeping Unit)
**Definición:** Código único y alfanumérico que identifica de manera específica un producto en el inventario. Permite una gestión precisa y diferenciada de cada variante de producto.

**Ejemplo:** "LAP-DELL-XPS13-16GB" o "PAP-BOND-75G-A4"

**Características:**
- Único por producto
- Facilita el seguimiento de inventario
- Permite identificar variaciones (color, tamaño, etc.)

---

#### Estado de Orden
**Definición:** Indicador de la situación actual por la que atraviesa una orden de compra dentro de su ciclo de vida.

**Estados y significados:**

| Estado | Descripción | Acción siguiente |
|--------|-------------|------------------|
| **Pendiente** | Orden creada, esperando revisión y aprobación | Aprobar o rechazar |
| **Aprobada** | Orden autorizada por el gestor | Enviar al proveedor |
| **Enviada** | Orden notificada al proveedor | Esperar confirmación y envío |
| **Recibida** | Productos llegaron al almacén | Verificar y actualizar inventario |
| **Cancelada** | Orden anulada por decisión del gestor | No requiere acción |

---

### Términos Técnicos y Operativos

#### Stock Mínimo
**Definición:** Cantidad límite de un producto que, al ser alcanzada, activa automáticamente una alerta de reabastecimiento. Sirve como indicador temprano para evitar desabastecimiento.

**Propósito:**
- Evitar rupturas de inventario
- Planificar compras oportunas
- Mantener niveles óptimos de servicio

**Ejemplo:** Si el stock mínimo de un producto es 10 unidades, al llegar a ese nivel se genera una alerta de compra.

---

#### Reabastecimiento
**Definición:** Proceso de comprar productos adicionales para mantener o incrementar los niveles de inventario, asegurando que siempre haya disponibilidad para las operaciones de la empresa.

**Tipos:**
- **Reabastecimiento automático:** Basado en reglas de stock mínimo
- **Reabastecimiento planificado:** Basado en proyecciones de demanda
- **Reabastecimiento por demanda:** Basado en solicitudes específicas

---

#### Historial de Precios
**Definición:** Registro cronológico de los cambios de precio de un producto a lo largo del tiempo. Permite analizar tendencias, negociar mejores condiciones y mantener transparencia en las compras.

**Información que almacena:**
- Producto
- Precio anterior
- Precio nuevo
- Fecha del cambio
- Usuario que realizó el cambio
- Razón del cambio

---

#### Auditoría (Bitácora)
**Definición:** Registro detallado y cronológico de todas las acciones realizadas en el sistema, incluyendo quién, qué, cuándo y desde dónde se realizó cada operación.

**Propósito:**
- Garantizar trazabilidad
- Cumplir con requisitos normativos
- Facilitar investigaciones
- Detectar actividades sospechosas

**Información que registra:**
- Usuario que ejecutó la acción
- Fecha y hora
- Acción realizada (crear, actualizar, eliminar)
- Entidad afectada (producto, proveedor, orden)
- Detalles adicionales

---

### Roles del Sistema

#### Gestor de Compras
**Definición:** Rol responsable de la planificación, ejecución, seguimiento y control de las adquisiciones de la empresa. Es el actor principal del Módulo de Compras.

**Responsabilidades:**
- Crear y aprobar órdenes de compra
- Gestionar proveedores
- Negociar condiciones comerciales
- Realizar seguimiento de entregas
- Generar reportes de gestión

---

#### Gestor de Inventario
**Definición:** Rol encargado de mantener y actualizar el catálogo de productos, controlar los niveles de stock y coordinar las actividades de almacenamiento.

**Responsabilidades:**
- Registrar y actualizar productos
- Mantener niveles de stock
- Gestionar categorías
- Realizar conteos físicos
- Generar alertas de reabastecimiento

---

### Términos de Tecnología y Arquitectura

#### API REST
**Definición:** Interface de Programación de Aplicaciones que sigue los principios REST (Representational State Transfer) para permitir la comunicación entre el frontend y el backend, así como con otros sistemas externos.

**Características:**
- Utiliza HTTP como protocolo
- Intercambia datos en formato JSON
- Es stateless (sin estado)
- Utiliza operaciones CRUD (GET, POST, PUT, DELETE)

**Endpoints principales del Módulo de Compras:**
- `GET /api/productos` - Consultar productos
- `POST /api/productos` - Registrar producto
- `GET /api/proveedores` - Consultar proveedores
- `POST /api/ordenes` - Crear orden de compra

---

#### JWT (JSON Web Token)
**Definición:** Estándar para la transmisión segura de información entre partes como un objeto JSON. Se utiliza en el sistema para la autenticación y autorización de usuarios.

**Componentes:**
- **Header:** Tipo de token y algoritmo de cifrado
- **Payload:** Información del usuario y permisos
- **Signature:** Firma digital para verificar integridad

**Propósito:**
- Autenticar usuarios
- Controlar acceso a recursos
- Mantener sesiones seguras

---

#### Microservicio
**Definición:** Enfoque arquitectónico donde una aplicación se compone de pequeños servicios independientes, cada uno ejecutando un proceso específico y comunicándose a través de APIs.

**Ventajas:**
- Escalabilidad independiente
- Despliegue autónomo
- Equipos especializados
- Tecnologías heterogéneas

**En el proyecto:** El Módulo de Compras es implementado como un microservicio independiente.

---

#### SPA (Single Page Application)
**Definición:** Aplicación web que carga una única página HTML y actualiza dinámicamente el contenido a medida que el usuario interactúa, sin necesidad de recargar la página completa.

**Tecnologías:**
- React
- TypeScript
- Redux para manejo de estado

**Ventajas:**
- Experiencia de usuario fluida
- Menor consumo de ancho de banda
- Desarrollo modular

---

### Otros Términos Relevantes

#### ERP (Enterprise Resource Planning)
**Definición:** Sistema de planificación de recursos empresariales que integra diferentes áreas funcionales de la empresa (compras, ventas, inventario, finanzas, recursos humanos) en una plataforma unificada.

**Propósito:**
- Centralizar información
- Eliminar silos de datos
- Optimizar procesos
- Mejorar la toma de decisiones

---

#### MVP (Minimum Viable Product)
**Definición:** Versión inicial del producto con las funcionalidades mínimas necesarias para ser lanzada al mercado y validar la propuesta de valor con los usuarios reales.

**En el proyecto:**
- Registro de productos
- Gestión de proveedores
- Creación de órdenes de compra
- Consulta de órdenes

---

#### Gateway / API Gateway
**Definición:** Punto de entrada único que enruta las solicitudes a los microservicios correspondientes y aplica políticas transversales como autenticación, autorización, rate limiting y logging.

**Funcionalidades:**
- Enrutamiento de solicitudes
- Autenticación y autorización
- Rate limiting
- Agregación de logs
- Balanceo de carga

---

#### Rate Limiting
**Definición:** Técnica para limitar el número de solicitudes que un cliente puede hacer a un servidor en un período de tiempo determinado, previniendo abusos y ataques de denegación de servicio.

**Ejemplo:** Máximo 100 solicitudes por minuto por usuario.

---

#### CI/CD (Continuous Integration / Continuous Deployment)
**Definición:** Prácticas para integrar y desplegar código de forma automatizada y frecuente, asegurando que el software esté siempre en un estado desplegable.

**En el proyecto:**
- GitHub Actions para CI/CD
- Pruebas automáticas en cada push
- Despliegue automático a entornos de staging

---

#### ORM (Object-Relational Mapping)
**Definición:** Técnica de programación que permite mapear objetos de programación orientada a objetos a tablas de bases de datos relacionales, facilitando la interacción con la base de datos.

**En el proyecto:**
- Spring Data JPA
- Hibernate como implementación
- Entidades Java mapeadas a tablas SQL

---

### Tabla de Acrónimos

| Acrónimo | Significado | Descripción |
|----------|-------------|-------------|
| **API** | Application Programming Interface | Interfaz para comunicación entre sistemas |
| **BD** | Base de Datos | Almacenamiento persistente de datos |
| **CI/CD** | Continuous Integration/Continuous Deployment | Prácticas de integración y despliegue continuo |
| **ERP** | Enterprise Resource Planning | Sistema de planificación de recursos |
| **JPA** | Java Persistence API | Especificación para ORM en Java |
| **JWT** | JSON Web Token | Estándar para autenticación |
| **MVP** | Minimum Viable Product | Producto Mínimo Viable |
| **ORM** | Object-Relational Mapping | Mapeo objeto-relacional |
| **REST** | Representational State Transfer | Estilo arquitectónico para APIs |
| **SKU** | Stock Keeping Unit | Unidad de mantenimiento de inventario |
| **SPA** | Single Page Application | Aplicación de una sola página |
| **SQL** | Structured Query Language | Lenguaje para consultas a BD |
| **UI** | User Interface | Interfaz de usuario |
| **UML** | Unified Modeling Language | Lenguaje de modelado unificado |

---

### Glosario Rápido (Referencia)

| Término | Definición Corta |
|---------|------------------|
| **Producto** | Bien o servicio que se compra |
| **Proveedor** | Entidad que suministra productos |
| **Orden de Compra** | Documento formal de compra |
| **Catálogo** | Listado de productos disponibles |
| **Categoría** | Clasificación de productos |
| **Unidad** | Medida de cantidad del producto |
| **SKU** | Código único de producto |
| **Stock Mínimo** | Límite para alerta de reabastecimiento |
| **Reabastecimiento** | Proceso de comprar más inventario |
| **Historial de Precios** | Registro de cambios de precio |
| **Auditoría** | Registro de acciones del sistema |
| **Gestor de Compras** | Rol que gestiona adquisiciones |
| **Gestor de Inventario** | Rol que gestiona productos |
| **API** | Interfaz de comunicación entre sistemas |
| **Microservicio** | Servicio independiente y modular |
| **Gateway** | Punto de entrada único al sistema |

---

### Historial de Cambios

| Versión | Fecha | Cambios | Responsable |
|---------|-------|---------|-------------|
| 1.0 | 2025-08-04 | Creación inicial del glosario | Equipo de Desarrollo |
| 1.1 | 2025-08-05 | Adición de términos técnicos y acrónimos | Equipo de Desarrollo |

---

*Este glosario es un documento vivo y debe actualizarse a medida que el proyecto evoluciona y se identifican nuevos términos.*
