# Vista de Bloques de Construcción

## C2 - Diagrama de Contenedores

![Diagrama de Contenedores](./images/C2.png)

## Explicación de Contenedores

### 1. Aplicación Frontend (React SPA)

**Responsabilidad:** Proporcionar la interfaz de usuario para interactuar con el módulo de compras.

**Tecnología:** React, TypeScript, Redux Toolkit, Material-UI

**Funcionalidades principales:**
- Pantalla de gestión de productos
- Pantalla de gestión de proveedores
- Pantalla de creación y gestión de órdenes de compra
- Dashboard de compras

**Interfaces:**
- Se comunica con el backend a través de API REST

---

### 2. API Gateway (Spring Cloud Gateway)

**Responsabilidad:** Punto de entrada único para todas las solicitudes del frontend.

**Funcionalidades:**
- Enrutamiento de solicitudes al microservicio correcto
- Autenticación y autorización (JWT)
- Rate limiting para prevenir abusos
- Logging de todas las solicitudes

**Interfaces:**
- Recibe solicitudes HTTPS del frontend
- Reenvía al microservicio correspondiente

---

### 3. Microservicio de Compras (Spring Boot)

**Responsabilidad:** Contiene toda la lógica de negocio del módulo de compras.

**Módulos internos:**

| Componente | Responsabilidad |
|------------|-----------------|
| **ProductController** | Gestiona endpoints de productos |
| **ProveedorController** | Gestiona endpoints de proveedores |
| **OrdenController** | Gestiona endpoints de órdenes de compra |
| **ProductService** | Lógica de negocio para productos |
| **ProveedorService** | Lógica de negocio para proveedores |
| **OrdenService** | Lógica de negocio para órdenes |
| **ProductRepository** | Acceso a datos de productos |
| **ProveedorRepository** | Acceso a datos de proveedores |
| **OrdenRepository** | Acceso a datos de órdenes |

**Interfaces:**
- API REST para el frontend
- JPA para la base de datos
- REST para sistemas externos

---

### 4. Base de Datos PostgreSQL

**Responsabilidad:** Almacenamiento persistente de todos los datos del módulo.

**Tablas principales:**
- `productos`: Catálogo de productos
- `proveedores`: Información de proveedores
- `categorias`: Clasificación de productos
- `ordenes_compra`: Órdenes de compra
- `detalle_orden`: Líneas de las órdenes
- `historico_precios`: Historial de precios de productos

---

### 5. Servicios Externos (Futuro)

**Sistema de Finanzas:**
- Recibe información de órdenes para facturación
- API REST para consultar estados de pago

**Sistema de Inventario:**
- Recibe actualizaciones de stock
- API REST para consultar disponibilidad

## Flujo de Datos
