# Unidad 3: Administración y gobernanza de Azure

[← Volver al índice](../README.md)

## Costos

**Factores que afectan el costo:** tipo de recurso, consumo, recursos huérfanos (discos o IPs que quedan al borrar una VM), región, tipo de suscripción y licencias de Azure Marketplace.

**Tráfico de red:** la entrada de datos (*ingress*) es **gratis**; la salida (*egress*) se cobra según **zona de facturación** (no confundir con zona de disponibilidad).

| Opción de precio | Compromiso | Ideal para | Ahorro máx. aprox. |
|---|---|---|---|
| Pago por uso | Ninguno | Uso variable | — |
| **Reservas** | 1 o 3 años, recurso específico | Carga estable 24/7 | 72 % |
| **Savings Plan** | 1 o 3 años, gasto por hora | Cómputo estable pero variado | 65 % |
| **Spot** | Ninguno | Cargas que toleran interrupciones | 90 % |

| Herramienta | Momento | Para qué |
|---|---|---|
| **Calculadora de precios** | **Antes** de implementar | Estimar costos |
| **Cost Management** | **Después** de implementar | Analizar gasto, presupuestos y alertas |

**Alertas de Cost Management:** de presupuesto (las configuras tú), de crédito (EA, automáticas al 90 % y 100 %) y de cuota de departamento (EA).

## Etiquetas (*tags*)

- Pares **nombre-valor** para organizar, filtrar y asignar costos.
- **No se heredan** del grupo de recursos o de la suscripción (a diferencia de RBAC, Policy y los bloqueos).
- Se pueden exigir o reasignar automáticamente con **Azure Policy**.

## Gobernanza y cumplimiento

| Herramienta | Qué controla | Palabra clave |
|---|---|---|
| **Azure Policy** | **Propiedades** de los recursos (regiones, SKUs, etiquetas) | "Solo permitir…", "exigir…" |
| **Azure RBAC** | **Personas**: qué acciones pueden hacer | "Quién puede…" |
| **Bloqueos** | Evitar borrado o cambios accidentales | Aplica incluso a Propietarios |
| **Microsoft Purview** | Gobernanza de **datos**: descubrir, clasificar, linaje | "Mapa unificado de datos" |
| **Service Trust Portal** | Cómo **Microsoft** cumple normativas (ISO, SOC) | "Informes de auditoría" |

- **Iniciativa** = grupo de políticas con un objetivo común.
- **Bloqueo Delete:** se puede leer y modificar, **no borrar**.
- **Bloqueo ReadOnly:** solo leer.
- Para modificar un recurso bloqueado: **primero quitar el bloqueo**.

## Herramientas para administrar Azure

- **Azure Portal:** interfaz web gráfica.
- **Azure Cloud Shell:** terminal en el navegador, **sin instalar nada** (Bash o PowerShell).
- **Azure CLI** (comandos `az ...`) y **Azure PowerShell** (cmdlets `New-Az...`): misma funcionalidad, distinta sintaxis; ambos multiplataforma.
- **Copilot en Azure:** asistente de IA; siempre revisa antes de aplicar cambios.
- **Azure Arc:** gestiona desde Azure servidores, Kubernetes y SQL que están **fuera** de Azure. **No migra** recursos.
- **Azure Resource Manager (ARM):** capa por la que pasa **toda** solicitud a Azure.
- **Plantillas ARM (JSON)** y **Bicep** (sintaxis más simple): infraestructura como código, **declarativa** e **idempotente**.

## Monitoreo

| Herramienta | Alcance |
|---|---|
| **Azure Advisor** | Recomienda mejoras en 5 pilares: costo, seguridad, confiabilidad, rendimiento, excelencia operativa. **No aplica cambios solo.** |
| **Azure Status** | Estado **global** de Azure, público |
| **Service Health** | Estado de **tus** servicios y regiones; mantenimientos planificados |
| **Resource Health** | Estado de **un** recurso: ¿falla de Azure o tuya? |
| **Azure Monitor** | Plataforma central de métricas, logs y alertas |
| **Log Analytics** | Consultas sobre logs (KQL) |
| **Application Insights** | Rendimiento y errores de **aplicaciones web** |
