# 🗂️ Diccionario de Datos (Data Dictionary)

## Estructura del Modelo
El modelo sigue un esquema de **Copo de Nieve (Snowflake Schema)** normalizado, compuesto por **53 tablas**. Esta estructura garantiza la integridad referencial y optimiza el almacenamiento.

A continuación, se describen las tablas organizadas por **Áreas Funcionales**:

---

### 1. 📊 Tablas de Hechos (Facts)
*Son las tablas centrales que contienen los datos métricos y las claves foráneas.*

| Tabla | Descripción Funcional |
| :--- | :--- |
| **Fact_Pif** | **Tabla Principal.** Contiene el registro único de cada Parte de Incendio Forestal (PIF). |
| **Fact_Operativa** | Datos de gestión: tiempos de respuesta, despliegue de brigadas y descargas de agua. |
| **Fact_Territorio** | Impacto físico: hectáreas quemadas desglosadas por tipo de vegetación y suelo. |
| **Fact_Economia** | Valoración económica de las pérdidas (madera, productos no maderables, costes). |

---

### 2. 🌍 Área Geográfica (Geography)
*Permite el análisis espacial desde la coordenada exacta hasta la región administrativa.*

* **Dim_Geografia:** Tabla maestra con latitud/longitud.
* **Jerarquía Administrativa:** `Comunidad`, `Provincia`, `Municipio`, `ComarcaI_sla`, `Cod_Entidad_Menor`.
* **Infraestructuras:** `Cod_Estacion_Meteorologica` (Clima), `Cod_Vigilante_Fijo` (Puestos de vigilancia).

---

### 3. 🔎 Área de Investigación (Causalidad)
*Tablas para analizar el origen y las motivaciones del fuego.*

* **Causas:** `Cod_Causa` (General), `Cod_Motivacion` (Específica), `Cod_Causante` (Autor).
* **Detalles:** `Cod_Certidumbre_Causa` (Nivel de certeza), `Cod_Iniciado_JuntoA` (Punto de inicio).

---

### 4. 🚁 Área Operativa y Medios
*Catálogos de recursos utilizados en la extinción.*

* **Medios Aéreos y Terrestres:** `Cod_Medio_Aereo`, `Cod_Medio_Pesado`, `Cod_Transporte_Personal`, `Cod_Medio_Personal_Exterior`.
* **Propiedad de Medios:** `Cod_Titularidad_Medio`.
* **Estrategia:** `Cod_Ataque` (Directo/Indirecto), `Cod_Retardante` (Químicos), `Cod_Detectado_Por`.
* **Estado del Incendio:** `Cod_Estado_Pif` (Conato/Incendio), `Cod_Tipo_Fuego`, `Cod_Peligro`, `Cod_Clase_Dia`.

---

### 5. 🌲 Área de Medio Ambiente y Territorio
*Contexto ecológico y valor natural de la zona afectada.*

* **Flora:** `Cod_Especie_Arbol`, `Cod_Mfe_Formacion_Arborea` (Mapa Forestal), `Cod_No_Arbolado_Herbaceo`.
* **Valoración:** `Especies_Valoracion` (Precios de madera/especie).
* **S
