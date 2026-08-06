# Introducción y Objetivos

## Objetivo del Sistema

El sistema ERP (Enterprise Resource Planning) tiene como objetivo centralizar y optimizar la gestión de los recursos empresariales, proporcionando una plataforma integrada que permita administrar de manera eficiente los procesos de compras, inventario, ventas, finanzas y recursos humanos.

El **Módulo de Compras** es un componente crítico del sistema que permitirá a la empresa gestionar todo el ciclo de vida de las adquisiciones, desde la identificación de necesidades hasta la recepción de mercancías, garantizando:

- **Optimización de costos:** Reducción de gastos mediante mejores negociaciones con proveedores.
- **Eficiencia operativa:** Automatización de procesos manuales y reducción de errores.
- **Visibilidad completa:** Trazabilidad total de las órdenes de compra.
- **Toma de decisiones basada en datos:** Informes y análisis para la gestión de compras.

## Requisitos de Negocio del Módulo de Compras

| ID | Requisito | Prioridad | Descripción |
|----|-----------|-----------|-------------|
| **R01** | Gestión de Productos | Alta | Registrar, consultar, actualizar y eliminar productos del catálogo |
| **R02** | Gestión de Proveedores | Alta | Registrar y mantener información de proveedores |
| **R03** | Creación de Órdenes de Compra | Alta | Generar órdenes de compra con productos y cantidades |
| **R04** | Consulta de Órdenes de Compra | Media | Visualizar y filtrar órdenes de compra por estado y fechas |
| **R05** | Actualización de Estado de Órdenes | Media | Cambiar estado: Pendiente → Aprobada → Enviada → Recibida |
| **R06** | Gestión de Categorías | Media | Clasificar productos por categorías |
| **R07** | Historial de Precios | Baja | Registrar cambios de precios de productos |
| **R08** | Reportes de Compras | Media | Generar informes de compras por período y proveedor |

## Objetivos de Calidad

| ID | Objetivo | Métrica | Prioridad |
|----|----------|---------|-----------|
| **Q01** | Rendimiento | Tiempo de respuesta < 2 segundos para consultas | Alta |
| **Q02** | Disponibilidad | 99.9% de uptime | Alta |
| **Q03** | Seguridad | Autenticación y autorización basada en roles | Alta |
| **Q04** | Usabilidad | Interfaz intuitiva, menos de 5 clics para tareas comunes | Media |
| **Q05** | Mantenibilidad | Código modular con cobertura de pruebas > 80% | Media |

## Stakeholders

| Rol/Name | Contacto | Expectativas |
|----------|----------|--------------|
| **Gerente de Compras** | jperez@empresa.com | Control total del proceso de compras, reportes ejecutivos, aprobación de órdenes |
| **Gestor de Inventario** | mlopez@empresa.com | Catálogo de productos actualizado, stock mínimo, alertas de reabastecimiento |
| **Equipo de Desarrollo** | dev@empresa.com | Código limpio, documentación completa, API bien definida |
| **Director de TI** | ctorres@empresa.com | Sistema escalable, seguro y con alta disponibilidad |
| **Proveedores** | - | Portal para ver órdenes, facturación electrónica (futuro) |
