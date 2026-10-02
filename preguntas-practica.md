# Preguntas de práctica

[← Volver al índice](README.md)

Preguntas propias enfocadas en mis [puntos débiles](debilidades.md). Intenta responder antes de abrir la solución.

## Bases de datos

**1.** Una empresa quiere migrar su SQL Server local a Azure. Usa trabajos programados con SQL Agent y no quiere administrar el sistema operativo. ¿Qué servicio elige?

<details><summary>Respuesta</summary>

**Azure SQL Managed Instance.** Es compatible con SQL Agent y Microsoft administra el SO. SQL Database no ofrece SQL Agent, y una VM obligaría a administrar el SO.
</details>

**2.** Un equipo crea una app móvil global que necesita latencia de milisegundos y usa la API de MongoDB. ¿Qué servicio corresponde?

<details><summary>Respuesta</summary>

**Azure Cosmos DB.** Es NoSQL, se distribuye globalmente y tiene API compatible con MongoDB.
</details>

**3.** Una aplicación heredada requiere una versión antigua de SQL Server y acceso administrativo al sistema operativo. ¿Qué opción corresponde?

<details><summary>Respuesta</summary>

**SQL Server en una máquina virtual de Azure (IaaS).** Es la única opción que da acceso al SO.
</details>

## Redundancia

**4.** Se necesita que los datos sobrevivan a la pérdida de un centro de datos completo, pero sin salir de la región. ¿Qué redundancia es la mínima que lo cumple?

<details><summary>Respuesta</summary>

**ZRS.** Copia los datos en 3 zonas de disponibilidad de la misma región. LRS no sobrevive a la pérdida del centro de datos, y GRS o GZRS agregan otra región, que no se pidió.
</details>

**5.** ¿Cuántas copias de los datos mantiene GRS y cómo se distribuyen?

<details><summary>Respuesta</summary>

**6 copias:** 3 en la región primaria (LRS) y 3 en la región secundaria (LRS).
</details>

**6.** Una app necesita **leer** desde la región secundaria en cualquier momento, sin esperar a un *failover*. ¿Qué opción se agrega?

<details><summary>Respuesta</summary>

**RA-GRS o RA-GZRS** (acceso de lectura en la secundaria).
</details>

**7.** Verdadero o falso: en GZRS, la región secundaria también replica entre zonas de disponibilidad.

<details><summary>Respuesta</summary>

**Falso.** En la secundaria los datos siempre se guardan con LRS. La "Z" aplica solo a la región primaria.
</details>

## Diagnóstico y monitoreo

**8.** Una VM dejó de responder. Necesitas saber si el problema fue de la plataforma de Azure o de tu configuración. ¿Qué usas?

<details><summary>Respuesta</summary>

**Azure Resource Health.**
</details>

**9.** Quieres recibir avisos sobre mantenimientos planificados que afectarán a las regiones que usa tu suscripción. ¿Qué usas?

<details><summary>Respuesta</summary>

**Azure Service Health.** Azure Status es global y no está personalizado para tu suscripción.
</details>

**10.** ¿Qué herramienta recomienda redimensionar una VM infrautilizada para ahorrar costos?

<details><summary>Respuesta</summary>

**Azure Advisor** (categoría Costo). Advisor recomienda, pero no aplica cambios por su cuenta.
</details>

**11.** Un desarrollador necesita medir tiempos de respuesta HTTP y excepciones de su app web. ¿Qué usa?

<details><summary>Respuesta</summary>

**Application Insights** (parte de Azure Monitor).
</details>

## Regiones y zonas

**12.** Verdadero o falso: todas las regiones de Azure tienen zonas de disponibilidad.

<details><summary>Respuesta</summary>

**Falso.** Solo algunas regiones las tienen.
</details>

**13.** ¿Qué característica garantiza que Microsoft no aplique actualizaciones de plataforma a dos regiones relacionadas al mismo tiempo?

<details><summary>Respuesta</summary>

**Los pares de regiones.**
</details>

**14.** Una pregunta menciona "zonas" al hablar de costos de transferencia de datos salientes. ¿A qué se refiere?

<details><summary>Respuesta</summary>

A las **zonas de facturación**, que agrupan regiones para tarificar el tráfico saliente. No son zonas de disponibilidad.
</details>

## Mezcla

**15.** Quieres impedir que se creen recursos fuera de las regiones de Sudamérica. ¿RBAC o Azure Policy?

<details><summary>Respuesta</summary>

**Azure Policy.** Controla las propiedades de los recursos. RBAC controla qué puede hacer cada persona.
</details>

**16.** Un usuario con rol de Propietario intenta borrar un grupo de recursos que tiene un bloqueo Delete. ¿Qué pasa?

<details><summary>Respuesta</summary>

**No puede borrarlo.** Los bloqueos aplican a todos, incluso a los Propietarios. Primero debe quitar el bloqueo.
</details>

**17.** Verdadero o falso: una etiqueta aplicada a un grupo de recursos se aplica automáticamente a los recursos que contiene.

<details><summary>Respuesta</summary>

**Falso.** Las etiquetas no se heredan. Para propagarlas se usa Azure Policy.
</details>
