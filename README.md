# 🍞 SPELTA Caracas — Panadería Artesanal & Panel Operativo

Sistema web integral compuesto por la tienda pública en línea (**Single Page Application**) y el **Panel de Control Operativo del Obrador**, diseñado para **SPELTA Caracas**. Permite a los clientes armar pedidos con cálculo dinámico en divisas/bolívares y al equipo de producción gestionar pedidos en vivo, consolidar lotes de horneada y controlar el stock en tiempo real desde Google Sheets[cite: 4].

---

## 🚀 Características Principales

### 🛒 Tienda Pública (`index.html`)
- **Tasa Oficial BCV en Tiempo Real:** Sincronización en vivo con la API pública de `dolarapi.com` para obtener la cotización oficial del día[cite: 2, 4].
- **Selector de Moneda Dinámico:** Visualización de precios en modo Dual (`$ / Bs.`), solo USD (`$`), o solo Bolívares (`Bs.`)[cite: 2, 4].
- **Sincronización de Catálogo desde la Nube:** Descarga automática de disponibilidad y límites de producción (`maxQty`) desde Google Sheets al cargar[cite: 2, 4].
- **Control Automático de Horario:** Bloqueo del botón de pedidos fuera del horario operacional (Lunes a Viernes de 8:00 AM a 4:00 PM)[cite: 2, 4].
- **Checkout Seguro & Registro:** Envío autenticado de la orden en segundo plano a Google Apps Script mediante un token secreto compartido, generación de ID correlativo (`#SP-YYMMDD-XXX`) y redirección formateada hacia WhatsApp[cite: 2, 3, 4].

### 🥖 Panel de Control Operativo / Admin (`admin.html`)
- **Autenticación Basada en Servidor:** Validación segura del PIN de acceso gestionada en el backend de Google Apps Script mediante sesiones efímeras generadas con `CacheService`[cite: 1, 2, 4].
- **Plan de Horneado Consolidado:** Suma automática y en tiempo real de todas las unidades por producto pendientes por producir para los pedidos activos[cite: 1, 4].
- **Cola de Pedidos en Vivo:** Visualización detallada de pedidos con filtros por estado (*Por Confirmar*, *En Horno*, *Listo*, *Entregado*), fecha, cliente y métricas financieras acumuladas ($ / Bs.)[cite: 1, 4].
- **Control de Disponibilidad (Stock Toggles):** Interruptores en vivo para pausar o activar productos; si un producto se pausa en el admin, se muestra inmediatamente como "Agotado" en la tienda pública[cite: 1, 4].

### 🛡️ Seguridad y Robustez en el Backend (`Código.gs`)
- **Protección de Credenciales:** El PIN de administración ya no se almacena en código abierto, sino de forma segura mediante las Propiedades del Script (`PropertiesService`)[cite: 2].
- **Control de Frecuencia (*Rate Limiting*):** Mecanismo de protección en caché para mitigar envíos masivos automatizados o abusos en la recepción de pedidos[cite: 2].
- **Sanitización Estricta:** Neutralización automática de caracteres y fórmulas maliciosas en hojas de cálculo (`=`, `+`, `-`, `@`) directamente en el servidor[cite: 2].

---

## 🛠️ Tecnologías Utilizadas

- **HTML5 & CSS3**
- **Tailwind CSS v3** (vía CDN con configuración de tema personalizada)[cite: 1, 2, 4]
- **JavaScript Vanilla ES6+** (Asíncrono, Async/Await, Fetch API)[cite: 1, 2, 4]
- **Google Material Symbols & Typography** (Newsreader & Plus Jakarta Sans)[cite: 1, 2, 4]
- **DolarAPI VE** (Servicio para obtener la tasa oficial del BCV)[cite: 1, 2, 4]
- **Google Apps Script & Google Sheets** (Backend seguro con control de caché, API REST, Webhook y base de datos en tiempo real)[cite: 1, 2, 4]

---

## 📁 Estructura del Proyecto

```text
.
├── index.html          # Tienda pública para clientes (Catálogo, Canasta y Checkout seguro)
├── admin.html          # Panel de control del Obrador (Gestión de pedidos, Plan de Horneada y Stock validado)
├── Código.gs           # Backend en Google Apps Script (Servidor web, API REST, Auth, Sanitización y Sheets)
├── logo.png            # Logotipo oficial de SPELTA Caracas
├── README.md           # Documentación técnica del proyecto
└── images/             # Fotografías reales de los productos
    ├── mini-galletas.jpg
    ├── pan-trenzado.jpg
    ├── pan-chocolate.jpg
    └── ...
