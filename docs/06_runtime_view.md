# Vista de Tiempo de Ejecución

## Escenario Crítico: Registrar un Producto

### Descripción del Escenario

El **Gestor de Inventario** desea agregar un nuevo producto al catálogo del sistema para mantenerlo actualizado y disponible para futuras órdenes de compra. Este escenario es crítico porque:

1. **Es el punto de entrada** para toda la gestión de compras
2. **Requiere validaciones estrictas** para garantizar la integridad de los datos
3. **Debe ser rápido y eficiente** para no interrumpir el flujo de trabajo del usuario
4. **Impacta directamente** en la calidad del catálogo de productos

### Diagrama de Secuencia UML

```plantuml
@startuml
title "Diagrama de Secuencia - Registrar Nuevos Productos (HU-01)"

' Definición de actores y componentes
actor "Gestor de Inventario" as Usuario
participant "Interfaz de Usuario\n(UI)" as UI
participant "Controlador de\nProductos" as Controlador
participant "Servicio de\nProductos" as Servicio
participant "Repositorio de\nProductos" as Repositorio
participant "Validador de\nDatos" as Validador
database "Base de Datos" as BD

' === FLUJO 1: Registro exitoso (Criterio 1) ===
== Registro exitoso (Criterio 1) ==
Usuario -> UI: Accede a pantalla de registro
activate UI

UI --> Usuario: Muestra formulario vacío
deactivate UI

Usuario -> UI: Completa todos los datos\ny hace clic en "Guardar"
activate UI

UI -> Controlador: registrarProducto(datosProducto)
activate Controlador

Controlador -> Validador: validarDatos(datosProducto)
activate Validador

Validador --> Controlador: Datos válidos
deactivate Validador

Controlador -> Servicio: crearProducto(datosProducto)
activate Servicio

Servicio -> Repositorio: save(producto)
activate Repositorio

Repositorio -> BD: INSERT INTO productos\n(nombre, descripcion, unidad)
activate BD
BD --> Repositorio: ID del producto generado
deactivate BD

Repositorio --> Servicio: Producto guardado\ncon ID asignado
deactivate Repositorio

Servicio --> Controlador: Producto registrado
deactivate Servicio

Controlador --> UI: Confirmación: "Producto guardado"
deactivate Controlador

UI --> Usuario: Muestra mensaje de éxito:\n"Producto registrado correctamente"
deactivate UI

' === FLUJO 2: Validación de campo obligatorio (Criterio 2) ===
== Validación de campo obligatorio (Criterio 2) ==
Usuario -> UI: Accede a pantalla de registro
activate UI

UI --> Usuario: Muestra formulario vacío
deactivate UI

Usuario -> UI: Deja campo "Nombre" vacío,\ncompleta los demás campos\ny hace clic en "Guardar"
activate UI

UI -> Controlador: registrarProducto(datosProducto)
activate Controlador

Controlador -> Validador: validarDatos(datosProducto)
activate Validador

note right of Validador
  Detección de error:
  El campo "Nombre" está vacío
end note

Validador --> Controlador: Error: "El nombre es obligatorio"
deactivate Validador

Controlador --> UI: Error de validación
deactivate Controlador

UI --> Usuario: Muestra mensaje de error:\n"El campo Nombre es obligatorio"\ny no guarda el producto
deactivate UI

' === FLUJO 3: Verificación en catálogo (Criterio 3) ===
== Verificación en catálogo (Criterio 3) ==
Usuario -> UI: Consulta el listado de productos
activate UI

UI -> Controlador: obtenerTodosLosProductos()
activate Controlador

Controlador -> Servicio: listarProductos()
activate Servicio

Servicio -> Repositorio: findAll()
activate Repositorio

Repositorio -> BD: SELECT * FROM productos
activate BD
BD --> Repositorio: Lista completa de productos\n(incluye el nuevo)
deactivate BD

Repositorio --> Servicio: Lista<Producto>
deactivate Repositorio

Servicio --> Controlador: Lista<Producto>
deactivate Servicio

Controlador --> UI: Lista<Producto> actualizada
deactivate Controlador

UI --> Usuario: Muestra el listado con\nel nuevo producto disponible
deactivate UI

@enduml
