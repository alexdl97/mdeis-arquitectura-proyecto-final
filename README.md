# OpenMarket Software

## 🌟 Descripción General

OpenMarket es una **plataforma de comercio electrónico multi-proveedor** que conecta clientes con múltiples vendedores, ofreciendo un catálogo unificado, proceso de compra integrado y seguimiento en tiempo real.

El siguiente repositorio representa la arquitectura del proyecto o software Open Market Software,
el cual para efectos practicos todo el proyecto estará en 1 solo repositorio.

## Estructura del Repositorio Principal: OpenMarket-Software

Este repositorio contiene la implementación del sistema **Open Market Software** basado en microservicios.

### 📂 Estructura Principal

```
openmarket-software/
├── apps/
│ ├── api-gateway/ # Punto de entrada único (NestJS)
│ ├── frontend/ # Aplicación web (Angular)
│ └── mobile-app/ # App móvil (Flutter)
│
├── services/ # Microservicios (NestJS/Node.js)
│ ├── logistics/ # Gestión de envíos y transportistas
│ ├── notifications/ # Notificaciones por email/SMS
│ ├── orders/ # Procesamiento de pedidos
│ ├── payments/ # Pasarelas de pago
│ ├── products/ # Catálogo de productos
│ ├── reports/ # Generación de reportes
│ ├── suppliers/ # Gestión de proveedores
│ └── users/ # Autenticación y perfiles
│
├── docker-compose.yml # Orquestación de contenedores
└── README.md # Documentación general
```

# Aplicaciones
En la carpeta de apps tenemos 3 aplicaciones, api-gateway, frontend y mobile-app las cuales se explicaran a continucación.

## Estructura del API Gateway

Este documento explica la organización de carpetas del API Gateway diseñado para el sistema **Open Market Software**.

### 📂 Estructura de Carpetas


```text
api-gateway/
├── src/
│ ├── auth/ # Autenticación y autorización
│ ├── routes/ # Enrutamiento a microservicios
│ │ ├── logistic.routes.ts → Microservicio de logística
│ │ ├── notifications.routes.ts → Microservicio de notificaciones
│ │ ├── order.routes.ts → Microservicio de pedidos
│ │ ├── payment.routes.ts → Microservicio de pagos
│ │ ├── product.routes.ts → Microservicio de productos
│ │ ├── reports.routes.ts → Microservicio de reportes
│ │ ├── suppliers.routes.ts → Microservicio de proveedores
│ │ └── users.routes.ts → Microservicio de usuarios
│ │
│ ├── middlewares/ # Procesamiento global de peticiones
│ │
│ └── shared/ # Utilidades compartidas
│
├── package.json # Dependencias del proyecto
└── README.md # Documentación general
```

## Estructura del Frontend

Este documento describe la organización del proyecto frontend para el sistema **Open Market Software**.

### 📂 Estructura de Carpetas
```
frontend/
├── src/
│ ├── app/
│ │ ├── core/ # Funcionalidades transversales
│ │ │ ├── api/ # Servicios para consumir API Gateway
│ │ │ ├── auth/ # Autenticación y gestión de sesión
│ │ │ └── interceptors/ # Interceptores HTTP
│ │ │
│ │ ├── modules/ # Módulos por funcionalidad
│ │ │ ├── auth/ # Login/registro
│ │ │ ├── logistic/ # Gestión logística
│ │ │ ├── orders/ # Pedidos y seguimiento
│ │ │ ├── products/ # Catálogo de productos
│ │ │ ├── reports/ # Reportes y estadísticas
│ │ │ └── shared/ # Componentes reutilizables
│ │ │
│ ├── assets/ # Recursos estáticos
│ ├── environments/ # Configuración por entorno
│ └── index.html # Punto de entrada HTML
│
├── package.json # Dependencias del proyecto
└── README.md # Documentación general
```

## Estructura de la App Móvil

Este documento describe la organización del proyecto móvil para **Open Market Software**.

### 📂 Estructura de Carpetas

```
mobile-app/
├── lib/
│ ├── auth/ # Autenticación y gestión de usuario
│ │ ├── bloc/ # Lógica de estado (BLoC)
│ │ ├── models/ # DTOs y entidades
│ │ ├── repositories/ # Conexión con API
│ │ └── views/ # Pantallas (login, registro)
│ │
│ ├── cart/ # Carrito de compras
│ │ ├── bloc/
│ │ ├── models/
│ │ └── views/
│ │
│ ├── core/ # Funcionalidades transversales
│ │ ├── api/ # Cliente HTTP y configuración
│ │ ├── constants/ # Colores, strings, rutas
│ │ ├── utils/ # Helpers y formateadores
│ │ └── widgets/ # Componentes reutilizables
│ │
│ ├── orders/ # Gestión de pedidos
│ ├── products/ # Catálogo de productos
│ ├── profile/ # Perfil de usuario
│ └── main.dart # Punto de entrada
```

# Microservicios
A continuación se explicará la estructura que maneja cada microservicio.

## Microservicio de Logística

Este servicio gestiona todo lo relacionado con envíos, seguimiento de pedidos e integración con transportistas para el sistema **Open Market Software**.

### 📂 Estructura del Código

```
logistics/
├── src/
│ ├── integrations/ # Adaptadores para APIs externas
│ │
│ ├── shipping/ # Gestión de envíos
│ │ ├── dto/ # Objetos de transferencia
│ │ │ └── create-shipment.dto.ts
│ │ ├── entities/ # Entidades de base de datos
│ │ │ └── shipment.entity.ts
│ │ ├── shipping.controller.ts # Endpoints REST
│ │ └── shipping.service.ts # Lógica de negocio
│ │
│ ├── tracking/ # Seguimiento de pedidos
│ │ ├── tracking.controller.ts
│ │ └── tracking.service.ts
│ │
│ └── index.ts # Punto de entrada
│
├── package.json # Dependencias
└── README.md # Documentación específica
```

## Microservicio de Notificaciones

Este servicio gestiona el envío de notificaciones a clientes y proveedores para el sistema **Open Market Software**.

### 📂 Estructura del Código
```
├── src/
│ ├── notification/ # Módulo principal
│ │ ├── dto/ # Objetos de transferencia
│ │ │ ├── create-notification.dto.ts
│ │ │
│ │ ├── entities/ # Entidades de base de datos
│ │ │ └── notification.entity.ts
│ │ │
│ │ ├── providers/ # Proveedores de notificación
│ │ │ ├── email.provider.ts
│ │ │ ├── sms.provider.ts
│ │ │
│ │ ├── notification.controller.ts # Endpoints REST
│ │ ├── notification.service.ts # Lógica de negocio
│ │ └── index.ts # Configuración del módulo
│ │
├── package.json # Dependencias
└── README.md # Documentación específica
```

## Microservicio de Pedidos (Orders)

Este servicio gestiona todo el ciclo de vida de los pedidos en **Open Market Software**, desde la creación hasta el cumplimiento.

### 📂 Estructura del Código
```
orders/
├── src/
│ ├── dto/ # Objetos de Transferencia de Datos
│ │ ├── create-order.dto.ts
│ │ └── update-order.dto.ts
│ │
│ ├── entities/ # Entidades de Base de Datos
│ │ └── order.entity.ts
│ │
│ ├── order.controller.ts # Endpoints API REST
│ ├── order.service.ts # Lógica de negocio principal
│ └── index.ts # Configuración del módulo
│
├── package.json # Dependencias
└── README.md # Documentación específica
```

## Microservicio de Pagos (Payments)

Este servicio gestiona todas las transacciones financieras en **Open Market Software**, integrando múltiples pasarelas de pago.

### 📂 Estructura del Código

```
├── src/
│ ├── payment/ # Módulo principal
│ │ ├── dto/ # Objetos de Transferencia
│ │ │ ├── create-payment.dto.ts
│ │ │
│ │ ├── entities/ # Entidades de base de datos
│ │ │ └── transaction.entity.ts
│ │ │
│ │ ├── payment-methods/ # Implementación de pasarelas
│ │ │ ├── payment-method.interface.ts
│ │ │ ├── stripe.ts
│ │ │ └── paypal.ts
│ │ │
│ │ ├── payment.controller.ts # Endpoints API
│ │ ├── payment.service.ts # Lógica central
│ │ └── index.ts # Configuración
│ │
├── package.json # Dependencias
└── README.md # Documentación específica
```

## Microservicio de Productos

Este servicio gestiona el catálogo central de productos para **Open Market Software**, incluyendo inventario y datos de proveedores.

### 📂 Estructura del Código

```
products/
├── src/
│ ├── product/ # Módulo principal
│ │ ├── dto/ # Objetos de Transferencia
│ │ │ ├── create-product.dto.ts
│ │ │ ├── update-product.dto.ts
│ │ │ └── product-response.dto.ts
│ │ │
│ │ ├── entities/ # Entidades de base de datos
│ │ │ └── product.entity.ts
│ │ │
│ │ ├── product.controller.ts # Endpoints API
│ │ ├── product.service.ts # Lógica de negocio
│ │ └── index.ts # Configuración
│ │
├── package.json # Dependencias
└── README.md # Documentación específica
```

## Microservicio de Reportes

Este servicio genera reportes analíticos y financieros para **Open Market Software**, procesando datos de múltiples microservicios.

### 📂 Estructura del Código

```
reports/
├── src/
│ ├── jobs/ # Tareas programadas
│ ├── report/ # Módulo principal
│ │ ├── dto/
│ │ │ └── create-report.dto.ts # Parámetros de reporte
│ │ │
│ │ ├── entities/
│ │ │ └── sales-report.entity.ts # Modelo de datos
│ │ │
│ │ ├── templates/ # Plantillas de reporte
│ │ │ └── sales.template.hbs # Handlebars template
│ │ │
│ │ ├── report.controller.ts # Endpoints API
│ │ ├── report.service.ts # Lógica de generación
│ │ └── index.ts # Configuración
│ │
├── package.json # Dependencias
└── README.md # Documentación específica
```

## Microservicio de Proveedores

Este servicio gestiona la integración con proveedores externos para **Open Market Software**, sincronizando catálogos de productos e inventarios.

### 📂 Estructura del Código

```
suppliers/
├── src/
│ ├── jobs/ # Tareas programadas
│ │ └── job-sync-every-day.service.ts # Sincronización diaria
│ │
│ ├── supplier/ # Módulo principal
│ │ ├── dto/ # Objetos de Transferencia
│ │ │ ├── create-supplier.dto.ts
│ │ │
│ │ ├── entities/ # Entidades de base de datos
│ │ │ ├── supplier.entity.ts
│ │ │
│ │ ├── supplier.controller.ts # Endpoints API
│ │ ├── supplier.service.ts # Lógica de negocio
│ │ └── index.ts # Configuración
│ │
├── package.json # Dependencias
└── README.md # Documentación
```

## Microservicio de Usuarios

Este servicio gestiona la identidad y acceso en **Open Market Software**, manejando autenticación, autorización y perfiles de usuario.

### 📂 Estructura del Código
```
users/
├── src/
│ ├── auth/ # Autenticación
│ │ ├── auth.service.ts # Lógica de login/JWT
│ │ └── index.ts # Configuración
│ │
│ ├── roles/ # Gestión de roles
│ │ ├── dto/
│ │ │ └── create-rol.dto.ts
│ │ │
│ │ ├── entities/
│ │ │ └── role.entity.ts
│ │ │
│ │ ├── role.controller.ts # CRUD de roles
│ │ ├── role.service.ts # Lógica de permisos
│ │ └── index.ts # Configuración
│ │
│ ├── user/ # Gestión de usuarios
│ │ ├── dto/
│ │ │ ├── create-user.dto.ts
│ │ │
│ │ ├── entities/
│ │ │ └── user.entity.ts
│ │ │
│ │ ├── user.controller.ts # Endpoints públicos
│ │ ├── user.service.ts # Lógica de negocio
│ │ └── index.ts # Configuración
│ │
│ ├── shared/ # Utilidades comunes
│ └── index.ts # Punto de entrada
│
├── package.json # Dependencias
└── README.md # Documentación
```
