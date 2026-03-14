# Dashboard RRHH — IBM HR Analytics

## Descripción

Dashboard interactivo de 3 páginas construido en Power BI para analizar la rotación de empleados y la composición del personal. El objetivo es ayudar a RRHH a identificar **quiénes se van, por qué se van** y qué acciones tomar para retener talento.

**Dataset:** IBM HR Analytics — Employee Attrition & Performance  
**Registros:** 1,470 empleados | 31 columnas (tras limpieza)  
**Herramientas:** Power BI Desktop | DAX | Power Query

---

## Páginas del Dashboard

### Página 1 — Resumen General RRHH

Vista ejecutiva con KPIs principales: Total Empleados (1,470), Empleados Activos (1,233), Ingreso Promedio ($6,500), Antigüedad Promedio (7.01 años), Empleados Inactivos (237) y Tasa de Rotación (16.12%). Incluye donut de retención de talento, bajas por departamento y top roles con mayor rotación.

![Resumen General RRHH](image/pagina1_resumen_general.png)

### Página 2 — Análisis de Rotación

Página estrella del proyecto. Analiza los factores asociados a la rotación usando **tasas porcentuales** para comparaciones justas entre grupos de diferente tamaño. Incluye filtros por Género y Departamento.

![Análisis de Rotación](image/pagina2_analisis_rotacion.png)

### Página 3 — Demografía y Salarios

Composición del personal por edad y género, nivel de educación y estado marital. Estructura salarial por rol, educación y departamento. Incluye filtros por Departamento, Attrition y Estado Marital, además de tooltip personalizado con distribución de ingreso por género.

![Demografía y Salarios](image/pagina3_demografia_salarios.png)

---

## Hallazgos Clave

### Rotación

- **OverTime es el factor #1 de rotación:** los empleados con horas extra tienen una tasa de ~30% vs ~10% sin horas extra.
- **Los menores de 25 años** presentan la tasa más alta (~38%), muy por encima del resto de grupos etarios.
- **Los empleados nuevos (0-2 años)** tienen ~36% de rotación, lo que indica un problema crítico en la retención temprana.
- **La satisfacción laboral baja** se asocia con mayor rotación (~22%), aunque la diferencia entre niveles no es tan marcada como el overtime.
- **El balance vida-trabajo bajo** muestra la tasa más alta (~30%), reforzando que las condiciones laborales impactan directamente en la retención.

### Top Roles con Mayor Rotación

- Laboratory Technician y Sales Executive lideran en cantidad de bajas (~60 cada uno).
- Research Scientist y Sales Representative también presentan números significativos.

### Composición del Personal

- El grupo de **25-34 años** es el más grande de la empresa, con predominancia masculina.
- **Licenciatura** es el nivel educativo más común (38.91%), seguido de Maestría (19.18%).
- **Casados** representan el 45.78% del personal, seguidos de Solteros (31.97%) y Divorciados (22.24%).

### Salarios

- **Manager y Research Director** son los roles mejor pagados (más de $15,000 mensuales).
- El ingreso promedio aumenta progresivamente con el nivel educativo: desde ~$4,500 (Menor a Universidad) hasta ~$8,000 (Doctorado).
- La tabla por departamento y educación muestra que **Research & Development** y **Sales** ofrecen salarios competitivos en niveles de Maestría y Doctorado.

---

## Modelo de Datos

- **Tabla principal:** WA_Fn-UseC_-HR-Employee-Attrition (1,470 filas, 31 columnas)
- **Tablas de dimensión:** Dim_Educacion, Dim_Satisfaccion, Dim_Balance, Dim_Ambiente (role-playing dimensions)
- **Tabla de medidas:** Total Empleados, Empleados Activos, Empleados Inactivos, Tasa de Rotación, Ingreso Promedio, Satisfacción Promedio, Antigüedad Promedio

## Transformaciones Aplicadas (Power Query)

- Eliminación de 4 columnas constantes (EmployeeCount, StandardHours, Over18, EmployeeNumber)
- Mapeo de Education a texto en español (Menor a Universidad, Universidad, Licenciatura, Maestría, Doctorado)
- Mapeo de escalas de satisfacción a texto (Bajo, Medio, Alto, Muy Alto) mediante role-playing dimensions
- Creación de columnas agrupadas: Grupo_Edad, Grupo_Distancia, Grupo_Antiguedad

---

## Estructura del Repositorio

```
├── README.md
├── Dashboard_RRHH.pbix
├── datos/
│   └── WA_Fn-UseC_-HR-Employee-Attrition.csv
└── imagenes/
    ├── pagina1_resumen_general.png
    ├── pagina2_analisis_rotacion.png
    └── pagina3_demografia_salarios.png
```

---

## Autor

Proyecto desarrollado como parte de un programa de aprendizaje en Power BI.
