# Unidad 1: Conceptos de la nube

[← Volver al índice](../README.md)

## ¿Qué es la informática en la nube?

Entrega de servicios de computación (servidores, almacenamiento, redes, bases de datos, IA, IoT) **bajo demanda a través de Internet**, con un modelo de **pago por uso**.

| Característica | Centro de datos local (*on-premises*) | Nube (Azure) |
|---|---|---|
| Aprovisionamiento | Semanas o meses | Minutos (**a petición**) |
| Flexibilidad | Limitada al hardware comprado | **Elástica**: crece y se reduce según la demanda |
| Alcance | Instalaciones propias | **Global** |
| Capacidad | Se compra para el pico (recursos ociosos) | Se escala en el pico y se libera después |

## Modelo de responsabilidad compartida

**Siempre del cliente** (en IaaS, PaaS y SaaS):
1. Datos e información
2. Dispositivos
3. Cuentas e identidades

**Siempre de Microsoft:** seguridad física del centro de datos, energía y refrigeración, red física y hosts.

| Capa | IaaS | PaaS | SaaS |
|---|---|---|---|
| Datos, dispositivos, cuentas | Cliente | Cliente | Cliente |
| Identidad e infraestructura de acceso | Cliente | Compartido | Compartido |
| Aplicaciones | Cliente | Compartido | Microsoft |
| Controles de red | Cliente | Compartido | Microsoft |
| Sistema operativo | **Cliente** | Microsoft | Microsoft |
| Virtualización, hosts, centro de datos | Microsoft | Microsoft | Microsoft |

> **Trampa típica:** en una VM (IaaS), **parchar el sistema operativo es responsabilidad del cliente**. En Azure SQL Database o App Service (PaaS), lo hace Microsoft.

## Modelos de implementación

| Modelo | Idea clave | Costo |
|---|---|---|
| **Pública** | Infraestructura del proveedor, compartida | OpEx (pago por uso) |
| **Privada** | Uso exclusivo de una organización, control total | CapEx alto |
| **Híbrida** | Pública + privada interconectadas | Mezcla de CapEx y OpEx |

- **Multinube:** usar dos o más proveedores públicos (Azure + AWS, por ejemplo).
- **Azure Arc:** administra desde Azure recursos que están fuera de Azure (local u otras nubes).
- **Azure VMware Solution:** ejecuta cargas de VMware en Azure.
- **Cloud bursting:** desbordar a la nube pública en picos, manteniendo lo crítico en local → **híbrida**.

## CapEx vs. OpEx

| | CapEx | OpEx |
|---|---|---|
| Qué es | Inversión inicial en activos físicos | Gasto recurrente según uso |
| Ejemplo | Servidores, switches, centro de datos | Suscripción a Azure |
| Entorno | Local / nube privada | Nube pública |

Azure es **OpEx** con **modelo basado en el consumo**: sin inversión inicial, sin capacidad ociosa y con el costo alineado a la demanda.

## Beneficios de la nube

| Beneficio | Palabras clave en el examen |
|---|---|
| **Alta disponibilidad** | Funcionamiento continuo; garantizado por un **SLA** (99,9 %, 99,95 %, 99,99 %) |
| **Escalabilidad vertical** (*scale up/down*) | Más CPU o RAM a la **misma** VM |
| **Escalabilidad horizontal** (*scale out/in*) | **Más instancias**; *VM Scale Sets* |
| **Confiabilidad** | Recuperarse de fallos; resiliencia; *failover* entre regiones |
| **Previsibilidad de rendimiento** | Autoescalado, balanceo de carga |
| **Previsibilidad de costos** | Calculadora de precios, seguimiento del gasto |
| **Seguridad** | Protección DDoS; parches automáticos en PaaS/SaaS |
| **Gobernanza** | Plantillas estandarizadas, auditoría de cumplimiento |
| **Administración DE la nube** | Autoescalado, alertas, autorreparación, IaC |
| **Administración EN la nube** | Portal, CLI, PowerShell, API REST |

## Tipos de servicio

| | IaaS | PaaS | SaaS |
|---|---|---|---|
| Control del cliente | **Máximo** | Medio (app y datos) | Mínimo |
| Carga de administración | Alta | Baja | Mínima |
| Ejemplos | Azure VMs, VNet, discos | App Service, Azure SQL Database, Functions | Microsoft 365, Teams, Dynamics 365 |
| Caso típico | *Lift-and-shift*, máximo control del SO | Desarrollar sin administrar servidores | Software listo para usar |
