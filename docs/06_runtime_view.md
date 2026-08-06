# Vista de Tiempo de Ejecución

## Escenario Crítico: Registrar un Producto

### Descripción del Escenario

El **Gestor de Inventario** desea agregar un nuevo producto al catálogo del sistema para mantenerlo actualizado y disponible para futuras órdenes de compra. Este escenario es crítico porque:

1. **Es el punto de entrada** para toda la gestión de compras
2. **Requiere validaciones estrictas** para garantizar la integridad de los datos
3. **Debe ser rápido y eficiente** para no interrumpir el flujo de trabajo del usuario
4. **Impacta directamente** en la calidad del catálogo de productos

### Diagrama de Secuencia UML

El siguiente diagrama muestra la interacción entre los componentes del sistema durante el registro de un nuevo producto:

![Diagrama de Secuencia - Registrar Producto](./images/Diagrama%20UML.png)

*Código fuente disponible en: [./diagrams/Diagrama UML.puml](./diagrams/Diagrama%20UML.puml)*

### Explicación del Flujo

#### Flujo 1: Registro Exitoso (Criterio de Aceptación 1)

| Paso | Componente | Acción | Descripción |
|------|------------|--------|-------------|
| **1** | Usuario | Interacción | El Gestor de Inventario accede a la pantalla de registro de productos |
| **2** | UI | Visualización | La interfaz muestra el formulario vacío con los campos requeridos |
| **3** | Usuario | Entrada de datos | Completa todos los campos obligatorios (nombre, descripción, unidad) |
| **4** | Usuario | Acción | Hace clic en el botón "Guardar" |
| **5** | UI → Controlador | Solicitud | Envía los datos del producto al Controlador de Productos |
| **6** | Controlador → Servicio | Procesamiento | Solicita al Servicio la creación del producto |
| **7** | Servicio → Repositorio | Persistencia | El Servicio pide al Repositorio guardar el producto |
| **8** | Repositorio → BD | Operación SQL | Ejecuta un INSERT INTO en la tabla `productos` |
| **9** | BD → Repositorio | Respuesta | Retorna el ID generado para el nuevo producto |
| **10** | Repositorio → Servicio | Confirmación | Confirma que el producto fue guardado exitosamente |
| **11** | Servicio → Controlador | Confirmación | Retorna el producto registrado con su ID |
| **12** | Controlador → UI | Respuesta | Envía confirmación de éxito al frontend |
| **13** | UI → Usuario | Visualización | Muestra mensaje "Producto registrado correctamente" |

**Tiempo estimado total:** ~300-500 ms

---

#### Flujo 2: Validación de Campo Obligatorio (Criterio de Aceptación 2)

| Paso | Componente | Acción | Descripción |
|------|------------|--------|-------------|
| **1** | Usuario | Interacción | Accede a la pantalla de registro |
| **2** | Usuario | Entrada de datos | Deja el campo "Nombre" vacío (error intencional) |
| **3** | Usuario | Acción | Hace clic en "Guardar" |
| **4** | UI → Controlador | Solicitud | Envía los datos incompletos al Controlador |
| **5** | Controlador | Validación | Detecta que el campo "Nombre" está vacío |
| **6** | Controlador → UI | Error | Retorna mensaje de error: "El nombre es obligatorio" |
| **7** | UI → Usuario | Visualización | Muestra mensaje de error: "El campo Nombre es obligatorio" |

**Puntos clave:**
- ❌ El producto **NO** se guarda en la base de datos
- ✅ El usuario recibe feedback inmediato del error
- 🔄 El formulario mantiene los datos ingresados para corregirlos

---

#### Flujo 3: Verificación en Catálogo (Criterio de Aceptación 3)

| Paso | Componente | Acción | Descripción |
|------|------------|--------|-------------|
| **1** | Usuario | Acción | Consulta el listado de productos |
| **2** | UI → Controlador | Solicitud | Pide todos los productos al Controlador |
| **3** | Controlador → Servicio | Solicitud | Pide la lista de productos al Servicio |
| **4** | Servicio → Repositorio | Consulta | Solicita todos los productos al Repositorio |
| **5** | Repositorio → BD | Operación SQL | Ejecuta SELECT * FROM productos |
| **6** | BD → Repositorio | Resultados | Retorna todos los productos (incluyendo el nuevo) |
| **7** | Repositorio → Servicio | Lista | Retorna la lista de productos |
| **8** | Servicio → Controlador | Lista | Retorna la lista al Controlador |
| **9** | Controlador → UI | Lista | Envía la lista actualizada al frontend |
| **10** | UI → Usuario | Visualización | Muestra el listado con el nuevo producto disponible |

---

### Detalles Técnicos de la Implementación

#### Estructura de Datos del Producto

```json
{
  "id": 1024,
  "nombre": "Laptop Dell XPS 13",
  "descripcion": "Laptop ultrabook con procesador Intel i7, 16GB RAM",
  "unidad": "unidad",
  "precioCompra": 3500000,
  "idProveedor": 5,
  "idCategoria": 3,
  "estado": "Activo",
  "fechaCreacion": "2025-08-04T10:30:00Z",
  "fechaActualizacion": "2025-08-04T10:30:00Z"
}

POST /api/productos
Content-Type: application/json
Authorization: Bearer <jwt_token>

{
  "nombre": "Laptop Dell XPS 13",
  "descripcion": "Laptop ultrabook con procesador Intel i7, 16GB RAM, SSD 512GB",
  "unidad": "unidad",
  "precioCompra": 3500000,
  "idProveedor": 5,
  "idCategoria": 3
}

HTTP 201 Created
Content-Type: application/json

{
  "id": 1024,
  "nombre": "Laptop Dell XPS 13",
  "descripcion": "Laptop ultrabook con procesador Intel i7, 16GB RAM, SSD 512GB",
  "unidad": "unidad",
  "precioCompra": 3500000,
  "idProveedor": 5,
  "idCategoria": 3,
  "estado": "Activo",
  "fechaCreacion": "2025-08-04T10:30:00Z",
  "fechaActualizacion": "2025-08-04T10:30:00Z"
}

HTTP 400 Bad Request
Content-Type: application/json

{
  "codigo": "ERR-001",
  "mensaje": "El campo 'nombre' es obligatorio",
  "timestamp": "2025-08-04T10:30:00Z"
}
