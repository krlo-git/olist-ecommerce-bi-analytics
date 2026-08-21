# Olist E-commerce — Business Intelligence Analytics

Proyecto de portafolio que aplica un ciclo completo de Business Intelligence — desde el levantamiento de requerimientos hasta un dashboard interactivo en Power BI — sobre datos reales de comercio electrónico brasileño.

## 📊 Sobre el dataset

Este proyecto utiliza el **Brazilian E-Commerce Public Dataset by Olist**, un dataset público con información de 100 mil pedidos realizados entre 2016 y 2018 en múltiples marketplaces de Brasil a través de la tienda Olist.

El dataset permite observar cada pedido desde múltiples dimensiones: estado del pedido, precio, pago y desempeño de envío, ubicación del cliente, atributos del producto y reseñas escritas por los clientes.

> Los datos son comerciales reales y fueron anonimizados. Las referencias a empresas y socios en el texto de las reseñas fueron reemplazadas por nombres de las grandes casas de *Game of Thrones*.

**Fuente:** [Brazilian E-Commerce Public Dataset by Olist — Kaggle](https://www.kaggle.com/olistbr/brazilian-ecommerce)

## 🏢 Contexto de negocio

Olist es la mayor tienda departamental de los marketplaces brasileños. Conecta pequeños negocios de todo Brasil con canales de venta sin complicaciones y con un solo contrato: los comerciantes venden sus productos a través de la tienda Olist y los envían directamente a los clientes usando los socios logísticos de Olist.

El flujo de negocio es el siguiente:
1. El cliente compra un producto en la tienda Olist
2. El vendedor recibe la notificación para completar el pedido
3. El pedido se envía al cliente mediante los socios logísticos de Olist
4. Una vez recibido el producto (o vencida la fecha estimada de entrega), el cliente recibe una encuesta de satisfacción por correo, donde puede calificar la experiencia y dejar comentarios

**Consideraciones importantes del negocio:**
- Un pedido puede tener múltiples ítems
- Cada ítem puede ser despachado por un vendedor distinto

## 🎯 Objetivo del proyecto

Construir una solución de Business Intelligence de extremo a extremo que permita responder preguntas clave de negocio sobre el desempeño comercial, logístico y de satisfacción del cliente de Olist, aplicando buenas prácticas de modelado de datos, ETL, calidad de datos y visualización.

### Preguntas de negocio que busca responder

1. ¿Qué categorías de producto generan más ingresos?
2. ¿Cómo varía el desempeño de entrega por región?
3. ¿Qué relación existe entre el tiempo de entrega y la satisfacción del cliente (reviews)?
4. ¿Cuáles son los métodos de pago más usados y su relación con el ticket promedio?
5. ¿Qué estados o regiones concentran más clientes y más ingresos?

## 🗂️ Estructura de datos

El dataset está compuesto por 9 tablas relacionadas entre sí:

| Tabla | Contenido |
|---|---|
| `olist_customers_dataset` | Información de clientes y su ubicación |
| `olist_orders_dataset` | Pedidos: fechas, estado |
| `olist_order_items_dataset` | Ítems de cada pedido, precio y flete |
| `olist_order_payments_dataset` | Método y valor de pago |
| `olist_order_reviews_dataset` | Reseñas y calificaciones de clientes |
| `olist_products_dataset` | Atributos de productos |
| `olist_sellers_dataset` | Información de vendedores |
| `olist_geolocation_dataset` | Coordenadas geográficas por código postal |
| `product_category_name_translation` | Traducción de categorías (PT → EN) |

### Relaciones clave entre tablas

- `order_id` conecta `orders` con `payments`, `order_items` y `reviews`
- `customer_id` conecta `orders` con `customers`
- `product_id` conecta `order_items` con `products`
- `seller_id` conecta `order_items` con `sellers`
- `zip_code_prefix` conecta `customers` y `sellers` con `geolocation`

*(Ver diagrama de relaciones en `/docs/er_diagram.png`)*

## 🛠️ Stack tecnológico

- **Python** (pandas, numpy) — exploración y ETL
- **SQL** — modelado relacional y carga de datos
- **Power BI** (DAX) — modelado dimensional y dashboard
- **Jupyter Notebooks** (VS Code) — desarrollo y documentación del análisis

## 📅 Plan de trabajo

| Semana | Entregable |
|---|---|
| 1 | Definición del problema de negocio y exploración inicial de datos |
| 2 | Modelado relacional y diagrama ER |
| 3 | ETL con Python y SQL |
| 4 | Esquema estrella y medidas DAX en Power BI |
| 5 | Construcción del dashboard |
| 6 | Validación de calidad de datos y control de versiones |
| 7 | Documentación final y video demo |

## 📁 Estructura del repositorio

```
olist-ecommerce-bi-analytics/
├── data/                   # CSV originales (no versionados en git)
├── notebooks/              # Notebooks de exploración y ETL
├── sql/                    # Scripts de creación de tablas y queries
├── powerbi/                # Archivo .pbix del dashboard
├── docs/                   # Diagramas, documento de requerimientos
├── README.md
└── .gitignore
```

## 🚀 Cómo reproducir este proyecto

1. Clona el repositorio
2. Descarga el dataset desde [Kaggle](https://www.kaggle.com/olistbr/brazilian-ecommerce) y colócalo en `/data`
3. Crea un entorno virtual e instala las dependencias:
   ```bash
   python -m venv venv
   venv\Scripts\Activate.ps1
   pip install -r requirements.txt
   ```
4. Ejecuta los notebooks en orden desde `/notebooks`

## 👤 Autor

Carlos — Proyecto desarrollado como parte de un portafolio de Business Intelligence y Ciencia de Datos.

## 📄 Licencia y agradecimientos

Dataset provisto por Olist bajo licencia pública en Kaggle. Este proyecto es de carácter educativo/portafolio.
