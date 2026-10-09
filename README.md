# 🍞 SPELTA Caracas — Panadería Artesanal

Aplicación web ligera (Single Page Application) diseñada para **SPELTA Caracas**, una micropanadería artesanal. Permite a los clientes explorar el menú de productos, consultar la tasa oficial de cambio del Banco Central de Venezuela (BCV) en tiempo real, armar su pedido y enviarlo directamente vía WhatsApp, registrando automáticamente la transacción en Google Sheets.

---

## 🚀 Características Principales

- **Tasa Oficial BCV en Tiempo Real:** Integración directa con la API pública de `dolarapi.com` para obtener la cotización oficial del día[cite: 2].
- **Selector de Moneda Dinámico:** Los clientes pueden visualizar los precios en modo Dual (`$ / Bs.`), solo USD (`$`), o solo Bolívares (`Bs.`)[cite: 1].
- **Gestión de Canasta en Vivo:** Incremento/decremento de cantidades por producto con límites de pedido (`maxQty`) por ítem[cite: 2].
- **Control de Horario de Atención:** Desactivación automática del botón de pedidos y visualización de un banner interactivo si la tienda está fuera de su horario operacional[cite: 2].
- **Integración con Google Sheets & WhatsApp:**
  1. Envía un `POST` en segundo plano a una App de **Google Apps Script** para guardar la orden[cite: 2].
  2. Genera un ID correlativo de pedido (`#SP-XXXX`)[cite: 2].
  3. Prepara el resumen del pedido formateado y codificado para abrir directamente la app de WhatsApp[cite: 1, 2].
- **Fallback Visual para Imágenes:** Muestra placeholders elegantes con íconos temáticos para productos que aún no cuentan con fotografía real.

---

## 🛠️ Tecnologías Utilizadas

- **HTML5 & CSS3**
- **Tailwind CSS v3** (vía CDN)[cite: 1, 2]
- **JavaScript Vanilla** (sin frameworks pesados)[cite: 1, 2]
- **Google Material Symbols & Fonts** (Newsreader & Plus Jakarta Sans)[cite: 1, 2]
- **DolarAPI VE** (Servicio para obtener la tasa oficial BCV)[cite: 2]
- **Google Apps Script** (Procesamiento del webhook para Google Sheets)[cite: 2]

---

## 📁 Estructura del Proyecto

```text
.
├── index.html          # Código principal de la aplicación (HTML, CSS y JS unificados)
├── logo.png            # Logotipo oficial de la marca (Fondo #efe4c8)
├── README.md           # Documentación del proyecto
└── images/             # Carpeta contenedora de las fotos reales de los productos
    ├── mini-galletas.jpg
    ├── cookie-balls.jpg
    ├── pan-trenzado.jpg
    └── ...
