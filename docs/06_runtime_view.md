# Vista de Tiempo de Ejecución

## Escenario Crítico: Registrar un Producto

### Descripción del Escenario

El usuario "Gestor de Inventario" desea agregar un nuevo producto al catálogo del sistema. Este es uno de los escenarios más críticos porque:
1. Es el punto de entrada para toda la gestión de compras
2. Requiere validaciones estrictas para garantizar la integridad de datos
3. Debe ser rápido y eficiente para no interrumpir el flujo de trabajo

### Flujo de Secuencia

![Diagrama de Secuencia - Registrar Producto](./images/registrar_producto.png)

### Explicación del Flujo

#### 1. Solicitud del Usuario
El Gestor de Inventario accede a la pantalla de registro de productos, completa el formulario con:
- Nombre del producto (obligatorio)
- Descripción (obligatoria)
- Unidad de medida (obligatoria)
- Proveedor (opcional)
- Categoría (opcional)

#### 2. Validación Frontend
React realiza validaciones básicas en el cliente:
- Verifica que los campos obligatorios no estén vacíos
- Valida el formato de los datos
- Deshabilita el botón de guardar si hay errores

#### 3. Envío de Datos
Al hacer clic en "Guardar", el frontend envía una solicitud POST al endpoint `/api/productos` con los datos en formato JSON.

#### 4. Procesamiento Backend
El Microservicio de Compras:
1. **Valida los datos** (Spring Validation)
   - Verifica que `nombre` no sea null o vacío
   - Verifica que `descripcion` no sea null
   - Verifica que `unidad` no sea null o vacío
   - Verifica que el proveedor exista (si se proporciona)

2. **Procesa el producto**
   - Asigna fecha de creación
   - Establece estado inicial = "Activo"
   - Genera código de producto (opcional)

3. **Persiste en Base de Datos**
   - Ejecuta INSERT en tabla `productos`
   - Retorna el ID generado

#### 5. Registro de Auditoría
Se registra la acción en la tabla `bitacora`:
- Usuario que registró
- Producto registrado
- Fecha y hora
- Acción: "REGISTRO_PRODUCTO"

#### 6. Respuesta al Frontend
El backend responde con:
- Código 201 Created
- Datos del producto registrado (incluyendo ID)
- Mensaje de éxito

#### 7. Actualización de UI
El frontend:
- Muestra mensaje de éxito al usuario
- Actualiza la lista de productos (o redirige al catálogo)
- Limpia el formulario

### Consideraciones de Rendimiento

| Aspecto | Métrica | Observación |
|---------|---------|-------------|
| **Tiempo de respuesta** | < 500 ms | Objetivo de rendimiento |
| **Transacciones** | ACID | Garantiza integridad de datos |
| **Concurrencia** | Hasta 100 usuarios simultáneos | Escalabilidad horizontal |

### Manejo de Errores

| Caso de Error | Respuesta del Sistema |
|---------------|----------------------|
| **Nombre vacío** | HTTP 400, mensaje: "El nombre es obligatorio" |
| **Nombre duplicado** | HTTP 409, mensaje: "El producto ya existe" |
| **Proveedor no existe** | HTTP 404, mensaje: "Proveedor no encontrado" |
| **Error de BD** | HTTP 500, mensaje: "Error interno del servidor" |
| **Timeout** | HTTP 504, mensaje: "Tiempo de espera agotado" |

### Ejemplo de Solicitud y Respuesta

**Solicitud (Frontend → Backend):**
```http
POST /api/productos
Content-Type: application/json
Authorization: Bearer <jwt_token>

{
  "nombre": "Laptop Dell XPS 13",
  "descripcion": "Laptop ultrabook con procesador Intel i7",
  "unidad": "unidad",
  "idProveedor": 5,
  "idCategoria": 3,
  "precioCompra": 3500000
}

###Respuesta exitosa
HTTP 201 Created
Content-Type: application/json

{
  "id": 1024,
  "nombre": "Laptop Dell XPS 13",
  "descripcion": "Laptop ultrabook con procesador Intel i7",
  "unidad": "unidad",
  "idProveedor": 5,
  "idCategoria": 3,
  "precioCompra": 3500000,
  "estado": "Activo",
  "fechaCreacion": "2025-08-04T10:30:00Z"
}
