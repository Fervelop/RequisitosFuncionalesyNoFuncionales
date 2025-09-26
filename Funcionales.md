# REQUISITOS FUNCIONALES - PLATAFORMA DE VIAJES PERSONALIZADOS

## RF-001: GESTIÓN DE CLIENTES Y PERSONALIZACIÓN

### RF-001.1: Registro de Cliente y Validación
**Descripción:** El sistema debe permitir el registro de nuevos clientes (usuarios) con información básica y validación de contacto.  
**Actor:** Cliente nuevo  
**Precondiciones:** Cliente tiene documento de identidad válido (para futuras reservas) y acceso a correo/teléfono.

**Flujo Principal:**
1. Cliente accede a página de registro.
2. Sistema solicita: nombres completos, documento (opcional en registro inicial, obligatorio para reserva), correo, teléfono.
3. Sistema valida formulario y unión de datos (correo/teléfono).
4. Sistema envía código de verificación por SMS/email.
5. Cliente confirma código.
6. Sistema crea cuenta y redirige a perfil.

**Criterios de Aceptación:**
- Validación básica de datos con formato estándar.
- Verificación: SMS / email.
- Tiempo máximo de proceso: 3 minutos.
- Integración futura con servicios de validación de identidad si se requiere (ej. validación con Procuraduría).

### RF-001.2: Perfil de Preferencias y Personalización
**Descripción:** El sistema debe recopilar información sobre las preferencias de viaje, presupuesto, restricciones y necesidades especiales del cliente para ofrecer planes altamente personalizados.  
**Actor:** Cliente registrado, Agente de Viajes  
**Precondiciones:** Cliente tiene cuenta creada y verificada.

**Flujo Principal (Cliente):**
1. Sistema presenta cuestionario de preferencias de viaje (intereses, estilo de viaje, destinos deseados, nivel de actividad).
2. Cliente responde sobre presupuesto estimado, restricciones (alimenticias, salud, movilidad) y necesidades especiales (idioma, asistencia).
3. Sistema guarda el perfil de preferencias.
4. Sistema personaliza recomendaciones y sugerencias de itinerarios/paquetes.
5. Opción de modificar perfil posteriormente.

**Flujo Principal (Agente):**
1. Agente accede al perfil del cliente.
2. Agente puede editar/completar el perfil con información adicional obtenida en interacciones directas.
3. Agente utiliza el perfil para la creación de itinerarios a medida.

**Criterios de Aceptación:**
- Cuestionario máximo 15 preguntas iniciales.
- Almacenamiento de datos clave: Nombre, contacto, intereses, presupuesto, restricciones, necesidades especiales, historial.
- Personalización inmediata del dashboard y recomendaciones.
- Facilidad para agentes de añadir y actualizar información del cliente.

## RF-002: CREACIÓN Y GESTIÓN DE ITINERARIOS Y SERVICIOS

### RF-002.1: Catálogo de Servicios de Viaje
**Descripción:** El sistema debe mostrar y permitir la selección de una amplia gama de servicios de viaje (vuelos, alojamiento, tours, transporte, seguros, experiencias únicas).  
**Actor:** Agente de Viajes  
**Precondiciones:** Catálogo de proveedores y servicios cargado en el sistema.

**Flujo Principal:**
1. Agente accede al módulo de creación de itinerarios.
2. Sistema muestra catálogo de servicios (vuelos, hoteles, tours, traslados, seguros, experiencias).
3. Agente filtra servicios por tipo, destino, fechas, presupuesto, preferencias del cliente.
4. Sistema muestra detalles de cada servicio (descripción, fotos, proveedor, precios base).
5. Agente selecciona servicios para un itinerario.

**Criterios de Aceptación:**
- Clasificación por tipo (Vuelos, Alojamiento, Tours, Transporte, Seguros, Experiencias), proveedor, ubicación y nivel de personalización.
- Facilidad para un administrador de agregar nuevos proveedores y servicios al catálogo sin programación.
- Búsqueda y filtrado eficiente para agentes.

### RF-002.2: Construcción de Itinerarios Personalizados
**Descripción:** El sistema debe permitir a los agentes construir itinerarios día por día de forma intuitiva, combinando servicios y ajustando según las necesidades del cliente.  
**Actor:** Agente de Viajes  
**Precondiciones:** Cliente ha proporcionado información de sus preferencias.

**Flujo Principal:**
1. Agente inicia la creación de un nuevo itinerario para un cliente.
2. Agente define destino(s) y fechas.
3. Agente arrastra y suelta (o selecciona) servicios del catálogo al itinerario, asignándolos a días específicos.
4. Sistema verifica automáticamente la disponibilidad y las tarifas de los servicios seleccionados en tiempo real.
5. Agente personaliza detalles de cada servicio (ej. tipo de habitación, excursión específica).
6. Sistema calcula el costo total del itinerario y permite ajustes.
7. Agente puede añadir notas internas y detalles personalizados.
8. Agente guarda el itinerario como borrador o lo envía para cotización.

**Criterios de Aceptación:**
- Interfaz "drag-and-drop" o similar para agentes.
- Vista de calendario del itinerario.
- Verificación automática de disponibilidad y tarifas.
- Flexibilidad para añadir servicios no estándar.
- Cálculo de coste total y desglose.

### RF-002.3: Gestión de Disponibilidad y Tarifas de Proveedores
**Descripción:** El sistema debe integrarse con proveedores externos para obtener disponibilidad y tarifas en tiempo real y comparar opciones automáticamente.  
**Actor:** Sistema automático, Agente de Viajes  
**Precondiciones:** Integraciones con APIs de proveedores configuradas y activas.

**Flujo Principal:**
1. Agente busca un servicio (ej. vuelo, hotel).
2. Sistema consulta APIs de múltiples proveedores para disponibilidad y tarifas en tiempo real.
3. Sistema compara las opciones (precio, calidad, valor añadido) y las presenta al agente.
4. Agente selecciona la opción preferida.

**Criterios de Aceptación:**
- Sincronización de disponibilidad en tiempo real.
- Motor de comparación con criterios configurables (precio, valoración, etc.).
- Integración mediante APIs (GDS, motores hoteleros, aerolíneas, operadores de tours).

# REQUISITOS NO FUNCIONALES - PLATAFORMA DE VIAJES PERSONALIZADOS

## RNF-003.3: Monitoreo y Alertas
**Descripción**: El sistema debe contar con monitoreo proactivo para identificar y resolver problemas de rendimiento, seguridad y disponibilidad antes de que afecten a los usuarios.

### Métrica Específica:
- Monitoreo 24/7 de métricas críticas (CPU, memoria, latencia, error rate, uso de API de proveedores).
- Alertas automáticas en menos de 5 minutos ante anomalías o fallos críticos.
- Dashboard en tiempo real para equipo técnico y de operaciones.

### Medición:
- Tiempo de detección de incidentes y tiempo de resolución.

### Condiciones de Prueba:
- Simulación de diversos tipos de fallos (ej. lentitud de DB, caída de API de proveedor, error en procesador de pagos).
- Verificación de cadena de notificaciones (equipo de guardia).
- Pruebas de escalación de alertas (si no se resuelve en X tiempo, escalar a nivel superior).

### Criterios de Aceptación:
- Integración con herramientas de comunicación (Slack/Teams) para alertas inmediatas.
- Métricas de uptime, latencia, error rate en tiempo real visibles en dashboard.
- Alertas diferenciadas por severidad: crítica, alta, media, baja.

### Prioridad: 
- SHOULD (Importante)

### Fuente:
- Entrevista GT - "Monitoreo Proactivo"
- Entrevista CTO - "monitoreo constante de amenazas"

---

## RNF-004: ESCALABILIDAD Y CRECIMIENTO

### RNF-004.1: Crecimiento de Base de Usuarios y Planes
**Descripción**: El sistema debe escalar automáticamente para soportar el crecimiento proyectado de clientes y el volumen de planes de viaje gestionados.

### Métrica Específica:
- Capacidad objetivo año 1: 10,000 clientes activos, 5,000 planes de viaje gestionados.
- Crecimiento máximo soportado: 200% en 6 meses (ej. temporada alta).
- Auto-scaling automático basado en métricas de uso de CPU, memoria y tráfico.

### Medición:
- Pruebas de carga progresiva y métricas de escalabilidad en entorno cloud.

### Condiciones de Prueba:
- Simulación de crecimiento exponencial de clientes y creación de itinerarios.
- Pruebas de performance con diferentes volúmenes de datos históricos (clientes, itinerarios).
- Verificación de auto-scaling en la plataforma cloud (AWS/Azure/GCP).

### Criterios de Aceptación:
- Arquitectura de microservicios para escalabilidad independiente de componentes (ej. módulo de cotización, módulo de reservas).
- Base de datos diseñada para escalar horizontalmente (sharding o bases de datos NoSQL/distribuidas).
- CDN global para optimización de contenido estático (imágenes de destinos, videos).

### Prioridad:
- MUST (Crítico)

### Fuente:
- Entrevista GO - "Volumen de planes de viaje anual"
- Entrevista GT - "Arquitectura Orientada a Microservicios", "Bases de Datos Escalables"
- Entrevista CTO - "queremos 100,000 usuarios activos en el primer año" (ajustado a metas realistas de turismo).

---

### RNF-004.2: Volumen de Transacciones y Datos
**Descripción**: El sistema debe procesar volúmenes crecientes de reservas, pagos y datos de clientes sin degradación del rendimiento.

### Métrica Específica:
- Meta año 1: 5,000 reservas confirmadas, 15,000 cotizaciones generadas.
- Capacidad de procesamiento: 100 transacciones de reserva/pago por minuto en picos.
- Crecimiento de datos: 100GB por mes de nuevos datos (perfiles, itinerarios, logs).

### Medición:
- Métricas de throughput y capacidad de procesamiento de los servicios críticos.

### Condiciones de Prueba:
- Simulación de picos de transacciones (ej. lanzamiento de una promoción, temporada alta).
- Pruebas con volúmenes reales de datos (históricos de clientes, proveedores).
- Verificación de performance de consultas sobre grandes volúmenes de datos.

### Criterios de Aceptación:
- Queue management (colas de mensajes) para absorber picos de transacciones (ej. envío masivo de notificaciones, procesamiento de pagos).
- Optimización continua de consultas de base de datos.
- Archivado automático de datos históricos inactivos para mantener el rendimiento.

### Prioridad:
- SHOULD (Importante)

### Fuente:
- Entrevista GO - "Volumen de planes de viaje anual"
- Entrevista GT - "Arquitectura de Eventos/Mensajería", "Bases de Datos Escalables"

---

## RNF-005: USABILIDAD Y EXPERIENCIA DE USUARIO

### RNF-005.1: Facilidad de Uso y Onboarding del Cliente/Agente
**Descripción**: La plataforma debe ser intuitiva y fácil de usar, tanto para los clientes al explorar viajes como para los agentes al crear planes complejos.

### Métrica Específica (Cliente):
- Tiempo de registro completo: máximo 3 minutos.
- Tasa de abandono en registro/perfilado: máximo 10%.
- Usuarios que envían primera solicitud de plan: mínimo 60%.

### Métrica Específica (Agente):
- Tiempo promedio para crear un itinerario básico: máximo 10 minutos.
- Satisfacción del agente con la herramienta: > 80% (medido con encuestas).

### Medición:
- Analytics de comportamiento de usuario, testing de usabilidad, encuestas.

### Condiciones de Prueba:
- Tests de usabilidad con usuarios reales (clientes sin experiencia, agentes nuevos).
- A/B testing de flujos de registro, perfilado y creación de itinerarios.
- Análisis de heat maps y user journeys.

### Criterios de Aceptación:
- Interfaz en español claro y sencillo, adaptado a terminología de viajes.
- Tutoriales interactivos integrados para agentes y para funcionalidades complejas del cliente.
- Tooltips explicativos para elementos de interfaz.

### Prioridad:
- MUST (Crítico)

### Fuente:
- Entrevista GP - "Interfaz intuitiva para agentes", "Diseño limpio y visual para clientes"
- Entrevista GO - "Facilidad de uso"
- Entrevista CTO - "en máximo cinco minutos una persona pueda crear su cuenta" (ajustado a 3 minutos para cliente y a 10 minutos para agente para primera creación de itinerario).

---

### RNF-005.2: Accesibilidad Digital
**Descripción**: La plataforma debe ser accesible para usuarios con diversas capacidades y dispositivos, siguiendo estándares internacionales.

### Métrica Específica:
- Cumplimiento WCAG 2.1 nivel AA.
- Soporte para lectores de pantalla.
- Responsive design para dispositivos móviles, tablets y escritorios.

### Medición:
- Auditorías de accesibilidad automatizadas y manuales.

### Condiciones de Prueba:
- Pruebas con herramientas como JAWS y NVDA.
- Testing en diferentes dispositivos, sistemas operativos y resoluciones de pantalla.
- Verificación de contraste de colores y tamaños de fuente.

### Criterios de Aceptación:
- Alto contraste opcional para usuarios con problemas visuales.
- Navegación completa por teclado.
- Tamaños de fuente ajustables.

### Prioridad:
- SHOULD (Importante)

### Fuente:
- Entrevista GP - "Experiencia de Usuario", Principio de inclusión (implícito en la idea de viajes personalizados para todas las necesidades).

---

### RNF-005.3: Experiencia Móvil Optimizada
**Descripción**: La plataforma (web y/o app móvil) debe proporcionar una experiencia nativa y optimizada para dispositivos móviles.

### Métrica Específica:
- Tiempo de carga inicial de app/PWA: máximo 3 segundos.
- Tamaño de app (si nativa): máximo 50MB.
- Funcionalidades offline para consulta de itinerario/documentos de viaje.

### Medición:
- Métricas de performance móvil y user engagement.

### Condiciones de Prueba:
- Testing en dispositivos Android e iOS de diferentes gamas.
- Pruebas con conexiones 3G, 4G y WiFi.
- Verificación de funcionalidades offline.

### Criterios de Aceptación:
- Push notifications inteligentes (no invasivas) para recordatorios de viaje, actualizaciones.
- Autenticación biométrica (huella, Face ID) para clientes.
- Sincronización automática con versión web.

### Prioridad:
- MUST (Crítico)

### Fuente:
- Entrevista GP - "Responsive"
- Entrevista GT - "Mobile-first design. La mayoría de usuarios accederán desde smartphones" (adaptado de la fuente Fintech original).

---

## RNF-006: CUMPLIMIENTO REGULATORIO Y LEGAL

### RNF-006.1: Cumplimiento Regulatorio del Sector Turismo
**Descripción**: El sistema debe cumplir con todas las regulaciones aplicables al sector turismo en Colombia y en los países destino.

### Métrica Específica:
- 100% cumplimiento regulaciones Ministerio de Comercio, Industria y Turismo (MINCIT) y otras entidades relevantes.
- Reportes obligatorios para autoridades de turismo automáticos y oportunos.
- Compliance con normativas de protección al consumidor turístico.

### Medición:
- Auditorías regulatorias y revisiones de compliance.

### Condiciones de Prueba:
- Simulación de generación de reportes regulatorios.
- Verificación

