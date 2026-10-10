# 🍞 SPELTA Caracas — Panadería Artesanal & Panel Operativo

Sistema web integral compuesto por la tienda pública en línea (**Single Page Application**) y el **Panel de Control Operativo del Obrador**, diseñado para **SPELTA Caracas**. Permite a los clientes armar pedidos con cálculo dinámico en divisas/bolívares y al equipo de producción gestionar pedidos en vivo, consolidar lotes de horneada y controlar el stock en tiempo real desde Google Sheets.

---

## 🚀 Características Principales

### 🛒 Tienda Pública (`index.html`)
- **Tasa Oficial BCV en Tiempo Real:** Sincronización en vivo con la API pública de `dolarapi.com` para obtener la cotización oficial del día[cite: 2].
- **Selector de Moneda Dinámico:** Visualización de precios en modo Dual (`$ / Bs.`), solo USD (`$`), o solo Bolívares (`Bs.`)[cite: 2].
- **Sincronización de Catálogo desde la Nube:** Descarga automática de disponibilidad y límites de producción (`maxQty`) desde Google Sheets al cargar[cite: 2].
- **Control Automático de Horario:** Bloqueo del botón de pedidos fuera del horario operacional (Lunes a Viernes de 8:00 AM a 4:00 PM)[cite: 2].
- **Checkout & Registro:** Envío de orden en segundo plano a Google Apps Script, generación de ID correlativo (`#SP-YYMMDD-XXX`) y redirección formateada hacia WhatsApp[cite: 2].
- **Sanitización de Entradas:** Filtrado activo de caracteres en campos de texto de los clientes para prevenir inyecciones de código (XSS)[cite: 2].

### 🥖 Panel de Control Operativo / Admin (`admin.html`)
- **Autenticación Segura en Servidor:** Validación del PIN de acceso gestionada directamente en el backend de Google Apps Script para evitar la exposición de credenciales en el cliente[cite: 1].
- **Plan de Horneado Consolidado:** Suma automática y en tiempo real de todas las unidades por producto pendientes por producir para los pedidos activos[cite: 1].
- **Cola de Pedidos en Vivo:** Visualización detallada de pedidos con filtros por estado (*Por Confirmar*, *En Horno*, *Listo*, *Entregado*), fecha, cliente y métricas financieras acumuladas ($ / Bs.)[cite: 1].
- **Control de Disponibilidad (Stock Toggles):** Interruptores en vivo para pausar o activar productos; si un producto se pausa en el admin, se muestra inmediatamente como "Agotado" en la tienda pública[cite: 1].
- **Sincronización Bidireccional:** Comunicación instantánea entre Google Apps Script, la Hoja de Cálculo y el cliente web[cite: 1].

---

## 🛠️ Tecnologías Utilizadas

- **HTML5 & CSS3**
- **Tailwind CSS v3** (vía CDN con configuración de tema personalizada)[cite: 1, 2]
- **JavaScript Vanilla ES6+** (Asíncrono, Async/Await, Fetch API)[cite: 1, 2]
- **Google Material Symbols & Typography** (Newsreader & Plus Jakarta Sans)[cite: 1, 2]
- **DolarAPI VE** (Servicio para obtener la tasa oficial del BCV)[cite: 1, 2]
- **Google Apps Script & Google Sheets** (Backend, base de datos en tiempo real y webhook)[cite: 1, 2]

---

## 📁 Estructura del Proyecto

```text
.
├── index.html          # Tienda pública para clientes (Catálogo, Canasta y Checkout)
├── admin.html          # Panel de control del Obrador (Gestión de pedidos, Plan de Horneada y Stock)
├── Código.gs           # Backend en Google Apps Script (Servidor web, API REST, Auth y comunicación con Sheets)
├── logo.png            # Logotipo oficial de SPELTA Caracas
├── README.md           # Documentación técnica del proyecto
└── images/             # Fotografías reales de los productos
    ├── mini-galletas.jpg
    ├── pan-trenzado.jpg
    ├── pan-chocolate.jpg
    └── ...
