# 🍞 SPELTA Caracas — Panadería Artesanal & Panel Operativo

Sistema web integral compuesto por la tienda pública en línea (**Single Page Application**) y el **Panel de Control Operativo del Obrador**, diseñado para **SPELTA Caracas**. Permite a los clientes armar pedidos con cálculo dinámico en divisas/bolívares y al equipo de producción gestionar pedidos en vivo, consolidar lotes de horneada y controlar el stock en tiempo real desde Google Sheets.

---

## 🚀 Características Principales

### 🛒 Tienda Pública (`index.html`)
- **Tasa Oficial BCV en Tiempo Real:** Sincronización en vivo con la API pública de `dolarapi.com` para obtener la cotización oficial del día.
- **Selector de Moneda Dinámico:** Visualización de precios en modo Dual (`$ / Bs.`), solo USD (`$`), o solo Bolívares (`Bs.`).
- **Sincronización de Catálogo desde la Nube:** Descarga automática de disponibilidad y límites de producción (`maxQty`) desde Google Sheets al cargar.
- **Control Automático de Horario:** Bloqueo del botón de pedidos fuera del horario operacional (Lunes a Viernes de 8:00 AM a 4:00 PM).
- **Checkout & Registro:** Envío de orden en segundo plano a Google Apps Script, generación de ID correlativo (`#SP-YYMMDD-XXX`) y redirección formateada hacia WhatsApp.

### 🥖 Panel de Control Operativo / Admin (`admin.html`)
- **Plan de Horneada Consolidado:** Suma automática y en tiempo real de todas las unidades por producto pendientes por producir para los pedidos activos.
- **Cola de Pedidos en Vivo:** Visualización detallada de pedidos con filtros por estado (*Por Confirmar*, *En Horno*, *Listo*, *Entregado*), fecha, cliente y métricas financieras acumuladas ($ / Bs.).
- **Control de Disponibilidad (Stock Toggles):** Interruptores en vivo para pausar o activar productos; si un producto se pausa en el admin, se muestra inmediatamente como "Agotado" en la tienda pública.
- **Sincronización Bidireccional:** Comunicación instantánea entre Google Apps Script, la Hoja de Cálculo y el cliente web.

---

## 🛠️ Tecnologías Utilizadas

- **HTML5 & CSS3**
- **Tailwind CSS v3** (vía CDN con configuración de tema personalizada)
- **JavaScript Vanilla ES6+** (Asíncrono, Async/Await, Fetch API)
- **Google Material Symbols & Typography** (Newsreader & Plus Jakarta Sans)
- **DolarAPI VE** (Servicio para obtener la tasa oficial del BCV)
- **Google Apps Script & Google Sheets** (Backend, base de datos en tiempo real y webhook)

---

## 📁 Estructura del Proyecto

```text
.
├── index.html          # Tienda pública para clientes (Catálogo, Canasta y Checkout)
├── admin.html          # Panel de control del Obrador (Gestión de pedidos, Plan de Horneada y Stock)
├── Código.gs           # Backend en Google Apps Script (Servidor web, API REST y comunicación con Sheets)
├── logo.png            # Logotipo oficial de SPELTA Caracas
├── README.md           # Documentación técnica del proyecto
└── images/             # Fotografías reales de los productos
    ├── mini-galletas.jpg
    ├── pan-trenzado.jpg
    ├── pan-chocolate.jpg
    └── ...
