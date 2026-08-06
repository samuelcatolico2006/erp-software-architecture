# Contexto y Alcance

## Contexto de Negocio

El **Módulo de Compras** interactúa con diversos actores externos e internos en el ecosistema empresarial:

### Actores del Sistema

| Actor | Descripción | Interacción Principal |
|-------|-------------|----------------------|
| **Gestor de Compras** | Responsable de gestionar órdenes de compra | Crea, aprueba y consulta órdenes |
| **Gestor de Inventario** | Administra el catálogo de productos | Registra y actualiza productos |
| **Proveedor** | Entidad externa que suministra productos | Recibe órdenes, confirma envíos (futuro) |
| **Sistema de Finanzas** | Sistema contable externo | Registro de facturas y pagos |
| **Sistema de Inventario** | Módulo de inventario | Actualización de stock al recibir mercancía |

### Diagrama de Contexto (C1)

![Diagrama de Contexto](./images/c1_context.png)

### Explicación del Diagrama

El **Módulo de Compras** actúa como un sistema central que coordina las adquisiciones:

1. **Gestor de Compras** → Sistema: Crea y gestiona órdenes de compra
2. **Gestor de Inventario** → Sistema: Mantiene el catálogo de productos
3. **Sistema de Compras** → Proveedor: Notifica órdenes (futuro)
4. **Sistema de Compras** → Sistema de Finanzas: Comparte datos de órdenes para facturación
5. **Sistema de Compras** → Sistema de Inventario: Notifica la recepción de mercancía

### Interfaces Externas

| Sistema Externo | Tipo de Interfaz | Datos Intercambiados |
|-----------------|------------------|---------------------|
| **Sistema de Finanzas** | REST API | Órdenes de compra, proveedores, montos |
| **Sistema de Inventario** | REST API / Eventos | Productos, cantidades, actualizaciones de stock |
| **Proveedores** | Email / API (futuro) | Órdenes de compra, confirmaciones |

---

## Contexto Técnico

### Diagrama de Contexto Técnico
