# Fin-up
CONTEXTO

1. Contexto y Propósito General de FinUp
  ¿Qué es FinUp?: Es una propuesta de aplicación y proyecto de analítica/minería de datos concebida para la gestión, control y análisis de finanzas.
  Problema que resuelve: La falta de control del presupuesto, la baja visibilidad sobre los hábitos de consumo cotidianos y la dificultad de identificar gastos hormiga    o categorías con fuga de capital.
  Objetivo principal: Transformar datos transaccionales y financieros dispersos en métricas claras, visualizaciones intuitivas y modelos predictivos/recomendadores para   la toma de decisiones presupuestales inteligentes.
Valor para Minería de Datos:
  Identificación de patrones de gasto mediante agrupación (clustering).
  Clasificación automática de consumos.
  Predicción de flujos de caja y detección de anomalías en el presupuesto.
  Enriquecimiento de datos propios con fuentes externas (como datos socioeconómicos de las encuestas de hogares del DANE en Colombia).

2. Origen y Estructura de los Datos (Dataset)
    Origen de los datos: Dataset público de Kaggle (Informe Finanzas por Christian Olaya) entregado en un archivo en formato Excel multitabla (Finanzas_Datos.xlsx).         Contiene registros de transacciones comerciales y tablas maestras complementarias relativas a la región de América Latina y Canadá.
    Geografía del dataset: Incluye registros regionales de Colombia, México, Chile, Perú, Argentina y Canadá.

3. Tablas y Modelo de Datos
    El dataset se compone de dos tablas/hojas (Sheets) principales estructuradas bajo un esquema transaccional relacional (Star Schema / Snowflake Schema implícito):

 Tabla 1: Finanzas (Tabla de Hechos / Fact Table)
    Descripción: Registra las operaciones financieras detalladas ítem por ítem (ventas, costos, ingresos, volúmenes de compra/venta).
Volumen de datos: 7,082 filas y 15 columnas.

 Tabla 2: Lookups (Tabla de Dimensiones / Dimension Table)
    Descripción: Contiene los maestros de consulta o dimensiones de negocio para enriquecer la tabla de hechos.
Volumen de datos: 344 filas y 5 columnas.


4. Diccionario de Atributos y Tipos de Datos

   Nombre del Atributo   /      Tipo de Dato Lógico    /      Tipo de Dato Python    /  Descripción - Rol en el Proyecto      
            #	                   Entérico- ID	                object/int	            Identificador consecutivo de la transacción.
   Product Description	         Texto / Cadena            	  object	                Descripción detallada del producto transaccionado.
       Customer Name	           Texto / Cadena	              object    	            Nombre del cliente/entidad que realiza la transacción.
           Year                  Temporal	                float64 / int64	            Año de la transacción (ej. 2019, 2020).
           Prd.	                 Categórico / Período	    float64 / int64	            Período u orden mensual/trimestral del registro.
         Quantity                Numérico Continuo      	float64                     Cantidad de unidades adquiridas/gastadas.
         Revenue	               Numérico Continuo      	float64                     Ingreso total generado por la transacción.
         Costs	                 Numérico Continuo	      float64                    	Costo de adquisición o egreso operativo.
       CountNumérico             Entero                   float64 / int64Contador     frecuencia de la transacción.                                                             Count3/Column2/Column4    Numérico Continuo        float64                     Atributos numéricos auxiliares y margen calculado.
5.  Atributos de la Tabla Lookups
   
Nombre del Atributo        Tipo de Dato Lógico        Tipo de Dato Python         Descripción / Rol en el Proyecto
Cliente                      Categórico/Texto              object                 Nombre de la entidad/persona.
Region                       Categórico / Geográfico       object                 País o región geográfica de residencia/operación.
Producto                     Categórico / Texto            object                 Nombre maestro del artículo o ítem.
Tipo de Producto             Categórico / Clase            object                  Categorización/Línea a la que pertenece el producto.


6.  Arquitectura Tecnológica (POR RECONOCER) para FinUp
Para llevar a cabo el proyecto sin sobrecomplicar la infraestructura, se utilizará un entorno de trabajo accesible pero potente:

    Procesamiento de Datos y Análisis:
        Python (en Google Colab o Jupyter Notebooks): Permite ejecutar el código sin necesidad de instalar servidores ni configurar bases de datos complejas.
        Pandas: Para cargar el archivo de Excel (.xlsx), unir las hojas (Finanzas y Lookups), limpiar los datos nulos y calcular promedios, totales y frecuencias.
    
   Minería de Datos Básica (Scikit-Learn):
        Clasificación / Regresión simple: Para predecir o estimar el nivel de gasto futuro según la categoría del producto.
        Segmentación básica (K-Means): Para agrupar a los clientes o hábitos de consumo en categorías simples (ej. Gasto Alto, Gasto Moderado, Gasto Bajo).
        
   Visualización de Resultados:
        Matplotlib y Seaborn: Para generar barras, gráficos de pastel y diagramas de dispersión directamente desde el código en Python.
        Excel / Power BI: Como opción alternativa para crear gráficos dinámicos y tableros visuales sencillos sin programar interfaz web.

