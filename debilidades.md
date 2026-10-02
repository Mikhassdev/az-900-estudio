# Puntos débiles

[← Volver al índice](README.md)

Temas donde más me equivoqué en las prácticas. Los repaso antes que todo lo demás.

## 1. Bases de datos en Azure

| Servicio | Modelo | Tipo | Elegir cuando la pregunta dice… |
|---|---|---|---|
| SQL Server en VM | IaaS | Relacional | Acceso al **sistema operativo**, versiones antiguas de SQL |
| Azure SQL Managed Instance | PaaS | Relacional | Migrar SQL Server tradicional con **SQL Agent**, consultas entre bases de datos, sin tocar el SO |
| Azure SQL Database | PaaS | Relacional | App **nueva** en la nube, mínima administración, serverless |
| Azure Cosmos DB | PaaS | **NoSQL** | Latencia de **milisegundos**, distribución global, API de MongoDB o Cassandra |
| Azure Database for MySQL / PostgreSQL | PaaS | Relacional | **Código abierto** administrado |

**Regla rápida:** "SQL Agent" → Managed Instance · "app moderna desde cero" → SQL Database · "NoSQL" o "milisegundos" → Cosmos DB.

## 2. Redundancia de almacenamiento

| Sigla | Copias | Dónde | Protege contra |
|---|---|---|---|
| **LRS** | 3 | 1 centro de datos | Falla de disco o rack. **No** sobrevive a la pérdida del edificio |
| **ZRS** | 3 | 3 zonas de disponibilidad | Pérdida de un centro de datos completo |
| **GRS** | 6 | 3 (LRS) en región primaria + 3 (LRS) en secundaria | Desastre regional |
| **GZRS** | 6 | 3 (ZRS) en primaria + 3 (LRS) en secundaria | Lo anterior combinado: máxima protección |
| **RA-** | — | Agrega **lectura** en la secundaria | Leer sin esperar a que se declare *failover* |

**Truco:** la "Z" indica zonas en la región primaria; la "G" indica una copia en otra región. La región secundaria **siempre** es LRS.

## 3. Herramientas de diagnóstico y monitoreo

| Pregunta | Respuesta |
|---|---|
| ¿Azure está caído a nivel mundial? (sin iniciar sesión) | **Azure Status** |
| ¿Hay mantenimiento planificado que afecte **mis** servicios? | **Service Health** |
| ¿Mi VM falló por Azure o por mi culpa? | **Resource Health** |
| ¿Por qué mi app web responde lento o lanza excepciones? | **Application Insights** |
| ¿Cómo ahorro o mejoro la seguridad? (recomendaciones) | **Azure Advisor** |
| ¿Dónde centralizo métricas, logs y alertas? | **Azure Monitor** |

## 4. Regiones y zonas de disponibilidad

- **Región:** conjunto de centros de datos conectados por una red de baja latencia.
- **Zona de disponibilidad:** centro(s) de datos independiente(s) **dentro** de una región.
- **Par de regiones:** dos regiones de la misma geografía; las actualizaciones nunca se aplican a ambas a la vez.
- **Trampa:** **no todas** las regiones tienen zonas de disponibilidad.
- **Trampa:** zona de **facturación** ≠ zona de **disponibilidad**.

## Pendiente de agregar

- [ ] Errores que salgan en las evaluaciones de práctica oficiales.
