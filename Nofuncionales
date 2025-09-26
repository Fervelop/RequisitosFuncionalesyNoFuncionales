# REQUISITOS NO FUNCIONALES - PLATAFORMA DE VIAJES PERSONALIZADOS

## RNF-001: RENDIMIENTO Y CAPACIDAD

### RNF-001.1: Tiempo de Respuesta de Interfaz
**Descripción:**  
El sistema debe garantizar tiempos de respuesta óptimos para todas las operaciones críticas, tanto para clientes como para agentes.

**Métrica Específica:**  
- Operaciones críticas (creación/edición itinerario, búsqueda proveedores, generación cotización): ≤ 5 segundos  
- Operaciones estándar (navegación, consulta perfiles): ≤ 2 segundos  
- Operaciones simples (login, carga páginas iniciales, aceptación cotización): ≤ 1 segundo  

**Medición:**  
Tiempo desde clic del usuario hasta renderizado completo de respuesta.

**Condiciones de Prueba:**  
- Red estándar 4G (10 Mbps) / Conexión de oficina para agentes.  
- Horario pico (ej. mañanas, inicio de temporada alta).  
- Base de datos con mínimo 50,000 registros de clientes y 10,000 itinerarios.

**Criterios de Aceptación:**  
- 95% de las operaciones deben cumplir el tiempo objetivo.  
- Máximo 1% de operaciones pueden exceder el doble del tiempo objetivo.  
- Implementación de loading states para operaciones >2 segundos.

**Prioridad:** MUST (Crítico)

**Fuente:**  
Entrevista GO - "Tiempo máximo aceptable", Entrevista GP - "Velocidad de carga de página", Entrevista CTO - "Los tiempos de carga no pueden superar los 3 segundos" (ajustado a 5s para operaciones complejas de agente).

---

### RNF-001.2: Latencia de API Backend
**Descripción:**  
Las APIs del backend deben responder con latencia mínima para garantizar experiencia fluida, especialmente con integraciones de proveedores.

**Métrica Específica:**  
- Latencia promedio de APIs internas y de proveedores críticos: ≤ 250ms (ajustado por posibles latencias de APIs externas).  
- Latencia percentil 95: ≤ 600ms.  
- Latencia máxima tolerada: ≤ 1200ms.

**Medición:**  
Tiempo desde recepción de request hasta envío de response.

**Condiciones de Prueba:**  
- Carga concurrente de 50 agentes y 1000 clientes activos.  
- Base de datos con datos de producción.  
- Medición durante 24 horas continuas.

**Criterios de Aceptación:**  
- Monitoreo continuo con alertas automáticas.  
- Degradación gradual bajo alta carga (no cortes abruptos).  
- Caché implementado para consultas frecuentes (ej. tarifas estáticas, información de destinos).

**Prioridad:** MUST (Crítico)

**Fuente:**  
Entrevista GT - "Optimización de Consultas", "Caché en Múltiples Niveles", Entrevista CTO - "menos de 200ms de latencia promedio" (ajustado por complejidad de integraciones de viaje).

---

### RNF-001.3: Capacidad de Usuarios Concurrentes
**Descripción:**  
El sistema debe soportar múltiples usuarios simultáneos (clientes y agentes) sin degradación significativa.

**Métrica Específica:**  
- Usuarios concurrentes objetivo: 50 agentes, 1,000 clientes.  
- Usuarios concurrentes máximo: 100 agentes, 2,500 clientes (con degradación controlada).  
- Transacciones por segundo (TPS): mínimo 100 TPS (consultas, reservas, modificaciones).

**Medición:**  
Pruebas de carga con herramientas como JMeter o LoadRunner.

**Condiciones de Prueba:**  
- Simulación de comportamiento real de usuarios (mix: 60% consultas, 30% operaciones de agente, 10% transacciones de cliente).  
- Duración mínima de prueba: 2 horas sostenidas.

**Criterios de Aceptación:**  
- Auto-scaling automático cuando se supera 80% de capacidad.  
- Balanceadores de carga distribuyen tráfico equitativamente.  
- Tiempo de respuesta no aumenta más del 50% bajo máxima carga.

**Prioridad:** MUST (Crítico)

**Fuente:**  
Entrevista GO - "Usuarios concurrentes", Entrevista GT - "Cloud-Native", "Balanceo de Carga y Autoescalado", Entrevista CTO - "10,000 usuarios concurrentes" (ajustado al volumen de un operador turístico).

---

## RNF-002: SEGURIDAD Y PROTECCIÓN DE DATOS

### RNF-002.1: Encriptación de Datos Sensibles
**Descripción:**  
Toda la información sensible (datos personales del cliente, detalles de pago, información de pasaportes) debe estar protegida con encriptación robusta.

**Métrica Específica:**  
- Datos en reposo: Encriptación AES-256.  
- Datos en tránsito: TLS 1.3 mínimo.  
- Claves de encriptación: Rotación automática cada 90 días.

**Medición:**  
Auditorías de seguridad automatizadas y penetration testing.

**Condiciones de Prueba:**  
- Escaneo de vulnerabilidades mensual.  
- Pruebas de penetración trimestrales por terceros.  
- Verificación de cumplimiento PCI DSS para manejo de pagos.

**Criterios de Aceptación:**  
- Zero almacenamiento de datos de tarjetas en servidores propios (usar tokenización de pasarelas).  
- Hash SHA-256 para contraseñas con salt único.  
- Tokenización para datos personales sensibles (ej. ID de pasaporte).

**Prioridad:** MUST (Crítico)

**Fuente:**  
Entrevista GO - "Seguridad y privacidad", Entrevista GT - "Cifrado Robusto", Entrevista CTO - "encriptación AES-256 para datos sensibles en reposo".

---

### RNF-002.2: Autenticación y Control de Acceso
**Descripción:**  
El sistema debe implementar autenticación robusta y control granular de permisos para clientes y agentes.

**Métrica Específica:**  
- Autenticación multifactor obligatoria para agentes y operaciones sensibles del cliente (ej. cambio de datos personales, solicitud de retiro de fondos si aplica).  
- Tokens JWT con expiración máxima 24 horas (revalidación periódica para agentes).  
- Bloqueo de cuenta tras 5 intentos fallidos consecutivos.

**Medición:**  
Logs de seguridad y métricas de intentos de acceso no autorizado.

**Condiciones de Prueba:**  
- Simulación de ataques de fuerza bruta.  
- Pruebas de bypass de autenticación.  
- Verificación de expiración de tokens.

**Criterios de Aceptación:**  
- Implementación OAuth 2.0 con refresh tokens.  
- Biometría opcional en aplicaciones móviles.  
- Notificación inmediata por login desde nuevo dispositivo/ubicación inusual.

**Prioridad:** MUST (Crítico)

**Fuente:**  
Entrevista GO - "Niveles de acceso y permisos", Entrevista GT - "Gestión de Identidades y Accesos (IAM)", Entrevista CTO - "OAuth 2.0 con JWT para autenticación".

---

### RNF-002.3: Auditoría y Trazabilidad de Seguridad
**Descripción:**  
El sistema debe registrar todas las actividades de seguridad y operativas para auditoría y detección de amenazas.

**Métrica Específica:**  
- 100% de operaciones de cliente y agente loggeadas.  
- Retención de logs de seguridad y actividad: mínimo 7 años.  
- Detección de anomalías en tiempo real.

**Medición:**  
Auditorías internas y verificación de logs de seguridad.

**Condiciones de Prueba:**  
- Simulación de actividades sospechosas (ej. acceso no autorizado a perfil de cliente).  
- Verificación de alertas automáticas.  
- Pruebas de integridad de logs.

**Criterios de Aceptación:**  
- Logs inmutables con firma digital.  
- SIEM (Security Information and Event Management) implementado.  
- Alertas automáticas por patrones anómalos de acceso o actividad.

**Prioridad:** MUST (Crítico)

**Fuente:**  
Entrevista GO - "Auditoría y Trazabilidad", Entrevista GT - "Auditoría y Monitoreo", Entrevista CTO - "auditoría completa de todas las acciones".

---

## RNF-003: DISPONIBILIDAD Y CONFIABILIDAD

### RNF-003.1: Disponibilidad del Sistema
**Descripción:**  
La plataforma debe estar operativa de manera continua con mínimas interrupciones planificadas.

**Métrica Específica:**  
- Disponibilidad objetivo: 99.9% (máximo 8.77 horas de downtime anual).  
- Mantenimientos programados: máximo 4 horas mensuales (en ventana de bajo uso).  
- Recovery Time Objective (RTO): 4 horas máximo.

**Medición:**  
Monitoreo continuo con herramientas de APM (ej. New Relic, DataDog).

**Condiciones de Prueba:**  
- Simulación de fallos de infraestructura.  
- Pruebas de disaster recovery trimestrales.  
- Monitoreo desde múltiples ubicaciones geográficas.

**Criterios de Aceptación:**  
- Infraestructura redundante en múltiples zonas de disponibilidad.  
- Failover automático sin intervención manual.  
- Página de estado público para comunicar incidencias.

**Prioridad:** MUST (Crítico)

**Fuente:**  
Entrevista GO - "Porcentaje de tiempo operativo", Entrevista GT - "Alta Dispon

