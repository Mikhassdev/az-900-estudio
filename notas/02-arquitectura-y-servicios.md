# Unidad 2: Arquitectura y servicios de Azure

[← Volver al índice](../README.md)

## Infraestructura física

| Concepto | Definición | Detalle clave |
|---|---|---|
| **Región** | Conjunto de centros de datos en un perímetro de baja latencia | No todas tienen zonas de disponibilidad |
| **Zona de disponibilidad** | Centros de datos independientes dentro de una región (energía, refrigeración y red propias) | Normalmente 3 por región habilitada |
| **Par de regiones** | Dos regiones de la misma geografía, en general a 300+ millas | Actualizaciones de plataforma secuenciales; prioridad de recuperación |
| **Regiones soberanas** | Azure Government (EE. UU.), Azure China (21Vianet) | Aisladas del resto de Azure |

## Jerarquía lógica

`Grupos de administración → Suscripciones → Grupos de recursos → Recursos`

- Un recurso pertenece a **un solo** grupo de recursos.
- Los recursos de un grupo pueden estar en **regiones distintas**.
- Eliminar un grupo de recursos **elimina todo su contenido**.
- Lo que se aplica a un grupo (permisos, políticas) afecta a los recursos **actuales y futuros**.

## Cuentas para practicar

| Opción | Crédito | Tarjeta |
|---|---|---|
| Cuenta gratuita | USD 200 por 30 días + servicios gratis por 12 meses | Sí (validación) |
| Azure for Students | USD 100 por 12 meses | No (correo educativo) |
| Sandbox de Microsoft Learn | Sin costo, temporal | No |

## Cómputo

| Servicio | Tipo | Cuándo |
|---|---|---|
| **Virtual Machines** | IaaS | Control total del SO; *lift-and-shift*; software heredado |
| **VM Scale Sets** | IaaS | Grupo de VMs idénticas con escalado horizontal automático |
| **Availability Sets** | — | Alta disponibilidad con dominios de **actualización** y de **error** |
| **Azure Virtual Desktop** | DaaS | Escritorios Windows en la nube; **multisesión** |
| **Container Instances (ACI)** | PaaS | Un contenedor rápido, sin orquestación |
| **Kubernetes Service (AKS)** | PaaS | Orquestar muchos contenedores (microservicios) |
| **Azure Functions** | Serverless | Código por **eventos**; pagas solo mientras se ejecuta |
| **App Service** | PaaS | Webs, APIs, WebJobs y backends móviles sin administrar el SO |

**VM vs. contenedor:** la VM virtualiza el hardware con un SO completo; el contenedor comparte el kernel del host, inicia en segundos y pesa megabytes.

## IA e IoT

- **Azure AI Services:** APIs ya entrenadas (visión, voz, lenguaje). No entrenas nada.
- **Azure OpenAI:** modelos generativos con seguridad de Azure.
- **Azure Machine Learning:** entrenar e implementar modelos **propios**.
- **IoT Hub** (PaaS, comunicación con dispositivos) · **IoT Central** (SaaS, listo para usar) · **IoT Edge** (procesamiento en el propio dispositivo).

## Redes

- **VNet:** red privada en Azure; se divide en **subredes**.
- **VNet Peering:** une redes virtuales por la red troncal de Microsoft (también entre regiones).
- **NSG:** reglas de entrada y salida por IP, puerto y protocolo; se evalúan por prioridad.
- **Service Endpoints:** acceso privado a servicios PaaS desde la VNet.
- **VPN Gateway:** conexión cifrada **por Internet**. Para multisitio, la de tipo **basada en rutas**.
- **ExpressRoute:** conexión **privada** y dedicada que **no pasa por Internet**; más predecible.
- **Azure DNS:** hospeda zonas DNS (**no vende dominios**); registros de alias hacia recursos de Azure.

## Almacenamiento

Nombre de cuenta: único a nivel global, 3–24 caracteres, solo minúsculas y números.

| Servicio | Uso |
|---|---|
| **Blobs** | Objetos no estructurados; base de Data Lake Gen2 |
| **Files** | Recursos compartidos SMB/NFS |
| **Queues** | Mensajes entre componentes (hasta 64 KB) |
| **Tables** | NoSQL clave-valor |
| **Disks** | Discos de VM |

**Niveles de acceso de Blob:** Hot → Cool (30 días mín.) → Cold (90 días) → Archive (180 días, **fuera de línea**, requiere rehidratación).

**Redundancia:** ver la matriz completa en [debilidades.md](../debilidades.md#2-redundancia-de-almacenamiento).

**Migración y movimiento de datos:**
- **Azure Migrate:** evaluar y migrar servidores, bases de datos y apps por la red.
- **Azure Data Box:** dispositivo físico para mover grandes volúmenes sin buen ancho de banda.
- **AzCopy:** línea de comandos, copia **unidireccional**.
- **Storage Explorer:** interfaz gráfica (usa AzCopy por debajo).
- **Azure File Sync:** sincronización **bidireccional** entre Windows Server local y Azure Files.

## Identidad y seguridad

- **Microsoft Entra ID:** identidad en la nube (SSO, MFA, SSPR).
- **Microsoft Entra Connect:** sincroniza identidades de Active Directory local con Entra ID.
- **Microsoft Entra Domain Services:** dominio administrado (Kerberos, NTLM, LDAP) para apps heredadas.
- **Factores de autenticación:** algo que sabes, algo que tienes, algo que eres.
- **Sin contraseña:** Windows Hello, Microsoft Authenticator, llaves FIDO2.
- **External ID:** B2B (invitados) y clientes (antes Azure AD B2C).
- **Acceso condicional:** decide según señales (usuario, ubicación, dispositivo) si permite, exige MFA o bloquea.
- **Azure RBAC:** **quién** puede hacer **qué**. Lector · Colaborador (no asigna permisos) · Propietario. Los roles **se suman**.
- **Zero Trust:** verificar explícitamente, privilegio mínimo, asumir la brecha.
- **Defensa en profundidad:** física → identidad → perímetro → red → cómputo → aplicación → **datos**.
- **Key Vault:** secretos, claves y certificados.
- **Defender for Cloud:** postura de seguridad (Secure Score) y protección; también híbrido y multinube.
