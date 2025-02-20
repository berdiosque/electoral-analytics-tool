# electoral-analytics-tool
Herramienta de análisis electoral con PostgreSQL y Metabase



# 🗳️ Análisis Electoral Personalizado - Servicio de Datos Estratégicos

**Transforma datos electorales caóticos en dashboards accionables para campañas políticas.**  
*(Low-Code | Adaptable | Enfoque Cualitativo + Cuantitativo)*

---

## 📌 ¿Por qué un Servicio Personalizado > SaaS Genérico?

| **Ventaja**               | **Explicación**                                                                 |
|---------------------------|---------------------------------------------------------------------------------|
| **Adaptabilidad**         | Procesamos datos en *cualquier formato* (PDFs, Excel, CSV, JSON).               |
| **Privacidad Controlada** | DNIs hasheados manualmente + acuerdos de confidencialidad por cliente.          |
| **Costo Razonable**       | Sin inversión en infraestructura cloud compleja (USD 17/mes en servidor básico).|
| **Análisis Humano**       | Interpretación sociológica de datos + recomendaciones estratégicas.            |

![Comparación Servicio vs SaaS](images/comparacion.png)  
*Ejemplo de dashboard personalizado vs plantilla genérica.*

---

## 🛠️ ¿Qué Incluye el Servicio?

### 1. **Procesamiento de Datos**
- Normalización de:
  - Padrones electorales (DNI, circuito, edad(!), género(!)).
  - Resultados históricos (por circuito y partido).
  - Datos de ANSES (subsidios, jubilaciones).
  - Otras bases de datos que permitan obtener más datos sociodemográficos.
  
- Ejemplo de limpieza con Python:
  ```python
  def limpiar_dni(df):
      # Eliminar caracteres no numéricos
      df['dni'] = df['dni'].str.replace('[^0-9]', '', regex=True)
      return df

### 2. **Dashboards Interactivos**
- Acceso web a Metabase con filtros:
  - Por circuito, rango de edad, género, tipo de subsidio.
- Consultas predefinidas:
  ```sql
  -- Jubilados en circuitos donde el Partido X obtuvo >40% de votos
  SELECT circuito, COUNT(*) AS total_jubilados
  FROM padron
  WHERE dni IN (SELECT dni FROM subsidios WHERE tipo = 'jubilación')
    AND circuito IN (SELECT circuito FROM resultados WHERE partido = 'X' AND votos > 40)
  GROUP BY circuito;
  ```
- Entrega y acceso:
  - Los dashboards estarán disponibles en un dominio personalizado (ej: analisiselectoral.enter.com.ar/cliente_X)
  - El acceso se gestionará mediante credenciales individuales proporcionadas al cliente.
  - Cada usuario tendrá permisos de solo lectura para visualizar y filtrar datos según los criterios disponibles.

### 3. **Informe Estratégico**
  - Consolidación de los datos procesados en un documento claro, estructurado y orientado a la toma de decisiones.
  - Insight claves y conclusiones cualitativas para la formulación de estrategias electorales.
  - Ej:
    - "Reforzar presencia territorial en circuito X debido a alto porcentaje de votantes indecisos en elecciones anteriores".
    - "Orientar campaña hacia jubilados en el ciruito Y, donde este grupo representa el 40% del electorado".
    - "Fortalecer discurso sobre empleo joven en circuito Z, donde el 35% de los votantes tiene entre 18 y 25 años".
    - "Reformular estrategia en el circuito M, donde se estima que el voto joven (18-25 años) tuvo una mayor inclinación hacia la oposición en las últimas elecciones."

---

## 💻 Tecnologías Utilizadas

| **Herramienta**       | **Función**                                      | **Costo**        |
|-----------------------|--------------------------------------------------|------------------|
| Python + Pandas       | Limpieza, cálculo de métricas y normalización.   | Gratuito (OSS)   |
| PostgreSQL            | Almacenamiento de datos normalizados.            | Gratuito (OSS)   |
| Metabase              | Visualización interactiva (dashboards).          | Gratuito (OSS)   |
| AWS                   | Servidor en la nube para alojar DBs y Metabase   | USD 20/mes aprox |

---

## 📈 Ejemplo

**Problema**: El *Partido Y* necesita aumentar votos en circuitos urbanos con alta deserción juvenil.  
**Solución**:
1. Cruzar padrón electoral con datos de ANSES (AUH) y resultados 2023.
2. Identificar 3 circuitos con:
   - >30% de jóvenes (18-25).
   - Baja participación histórica (<50%).
3. Dashboard clave:
   ![Dashboard AUH](images/dashboard_auh.png)


---

## 📦 Entregables al Cliente

- **Enlace privado a Dashboard Metabase**: Ej: `https://analisiselectoral.enter.com.ar/cliente-x`.
- **Informe PDF**: Incluye:
  - Gráficos estáticos.
  - Recomendaciones por circuito.
- **Soporte**: X cantidad de días después de entregado.

---

## 🔍 Importancia del Análisis Cualitativo + Cuantitativo

- **Cuantitativo**: 
  - *Métrica clave*: "El circuito B tiene un 45% de mujeres entre 40-60 años."
- **Cualitativo**:
  - *Hallazgo*: "Entrevistas revelan que la seguridad es prioridad en mujeres >40 años."
- **Sinergia**: 
  - Estrategia: Campaña en plazas con enfoque en seguridad laboral (circuito B).

---

**¿Listo para transformar datos en votos? ahre**  

