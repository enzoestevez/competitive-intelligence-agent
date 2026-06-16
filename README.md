# 🔍 Competitive Intelligence Agent

Agente de inteligencia competitiva automatizado que monitorea competidores semanalmente, extrae datos de productos vía API pública y genera reportes ejecutivos con IA.

🔗 **[Ver dashboard en Google Sheets →](#)*https://docs.google.com/spreadsheets/d/1VqX24b8Qwg0BxrhfRLXSGlXmiH6_p8ERUC7X5Q_E8cI/edit?usp=sharing* 

---

## 🎯 Problema de negocio

Las marcas de indumentaria necesitan monitorear competidores de forma constante: qué productos destacan, cómo evolucionan los precios, qué dicen los clientes. Hoy ese proceso es manual, tarda horas y es inconsistente. Este agente lo automatiza completamente.

**Lo que automatiza:**
- Extracción semanal de datos de productos de competidores vía API
- Almacenamiento estructurado en Google Sheets
- Generación de reporte ejecutivo con análisis de IA
- Todo sin intervención humana

---

## ⚙️ Arquitectura del flujo

```
Schedule (trigger semanal)
        ↓
HTTP Request → dummyjson.com/products API
(datos de productos: nombre, precio, rating)
        ↓
Tools → Set Variable
(construcción del prompt para Claude AI)
        ↓
Google Sheets → Add Row (datos_competidores)
(almacenamiento estructurado por competidor)
        ↓
Claude API → HTTP POST
(análisis ejecutivo: tendencias, movimientos, recomendaciones)
        ↓
Google Sheets → Add Row (output_ia)
(reporte guardado con fecha y timestamp)
```

---

## 🛠️ Stack tecnológico

| Herramienta | Uso |
|---|---|
| Make | Orquestación del flujo automatizado |
| HTTP / REST API | Extracción de datos de productos |
| Google Sheets | Almacenamiento y base de datos |
| Claude AI (Anthropic) | Generación de análisis ejecutivo |

---

## 🚀 Cómo usar este proyecto

### 1. Configurar Google Sheets

Creá un Sheet con estas pestañas y columnas:

**datos_competidores:**
`fecha | semana | competidor | categoria | producto_destacado | precio_ars | descuento_pct | resenas_positivas | resenas_negativas | rating | fuente`

**output_ia:**
`fecha | semana | análisis_ia | generado_por | competidores_analizados`

### 2. Importar el escenario en Make

1. Creá una cuenta gratuita en [make.com](https://make.com)
2. Nuevo escenario → importá el blueprint `make_blueprint.json` de este repo
3. Conectá tu cuenta de Google Sheets
4. Configurá tu API key de Claude (ver sección siguiente)

### 3. Configurar Claude API

En el módulo HTTP que llama a Claude API, agregá en Headers:

```
Authorization: Bearer TU_API_KEY_AQUI
Content-Type: application/json
```

Conseguí tu API key en [console.anthropic.com](https://console.anthropic.com)

### 4. Activar el Schedule

Activá el escenario en Make → se ejecuta automáticamente cada lunes a las 9:00 AM.

---

## 📊 Output del agente

Cada semana el agente genera automáticamente:

**En `datos_competidores`:** una fila por competidor con productos destacados, precios y ratings

**En `output_ia`:** reporte ejecutivo con:
- Tendencias de precios detectadas
- Productos y categorías destacadas
- Movimientos estratégicos relevantes
- Recomendaciones concretas accionables

---

## 📈 Ejemplo de reporte generado

> **REPORTE SEMANA 24 — Inteligencia Competitiva**
>
> Mango AR lanzó nueva colección con rating 4.5, el más alto del mercado esta semana. Zara AR aplica 20% de descuento en outerwear, señal de cambio de temporada. Recomendación: acelerar comunicación de nueva colección propia antes de que Mango AR consolide posición en el segmento premium.

---

## 👤 Autor

**[Enzo Estevez]**
Analista de datos | Business Analytics | Automatización con IA

[www.linkedin.com/in/enzoestevez](#) · [https://enzoestevez.com/](#) · [mailto:enzoestevez6@gmail.com](#)
