# Dashboard para un Service desk

Un panel interactivo diseñado en Power bi para monitorear, analizar y optimizar la gestión de tickets de soporte técnico e incidentes TI. Este proyecto abarca desde el tratamiento de datos y modelado dimensional hasta la creación de métricas clave (KPIs) e indicadores de cumplimiento de acuerdos de nivel de servicio (SLA).

---

##  Vista Previa del Dashboard

![Vista previa](docs/dashboard_preview.png)

---

## Objetivos del Proyecto

* **Monitoreo de SLAs:** Evaluar el porcentaje de cumplimiento de SLA en la atención de solicitudes de TI.
* **Análisis de Volumetría:** Identificar la carga de trabajo por categorías y nivel de prioridad.
* **Eficiencia Operativa:** Analizar los tiempos promedio de resolución de tickets para identificar cuellos de botella en la atención.
* **Tendencia Temporal:** Evaluar la evolución mensual del volumen de incidentes e indicadores de soporte.

---

## Tecnologías y Herramientas

* **Power BI Desktop**
* **Power Query (M)**
* **DAX (Data Analysis Expressions)**
* **Python (Opcional)**


---

## Medidas Clave (DAX)

Métricas principales desarrolladas para el panel:

* **Total Tickets:**
  ```dax
  Total Tickets = COUNT(servicedesk_tickets[TicketID])
% Cumplimiento SLA = 
DIVIDE(
    CALCULATE(
        COUNT(servicedesk_tickets[TicketID]), 
        servicedesk_tickets[EstadoSLA] = "Cumplido"
    ),
    [Total Tickets],
    0
)
Tiempo Prom_Resolucion = AVERAGE(servicedesk_tickets[TiempoResolucion_Horas])
