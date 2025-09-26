# Requisitos Funcionales y No Funcionales
# REQUISITOS FUNCIONALES - PLATAFORMA DE VIAJES PERSONALIZADOS

## RF-001: GESTIÓN DE CLIENTES Y PERSONALIZACIÓN

### RF-001.1: Registro de Cliente y Validación
**Descripción:** El sistema debe permitir el registro de nuevos clientes (usuarios) con información básica y validación de contacto.  
**Actor:** Cliente nuevo  
**Precondiciones:** Cliente tiene documento de identidad válido (para futuras reservas) y acceso a correo/teléfono.

**Flujo Principal:**
1. Cliente accede a página de registro (web o app).
2. Sistema solicita: nombres completos, documento (opcional en registro inicial, obligatorio para reserva), correo, teléfono.
3. Cliente proporciona información requerida.
4. Sistema valida formato y unicidad de datos (correo/teléfono).
5. Sistema envía código de verificación por SMS/email.
6. Cliente confirma código.
7. Sistema crea cuenta y redirige a perfil.

**Criterios de Aceptación:**
- Validación básica de datos con formato estándar.
- Verificación dual: SMS + email.
- Tiempo máximo de proceso: 5 minutos.
- Integración futura con servicios de validación de identidad si se requiere (ej. identificación digital).

**Prioridad:** MUST (Crítico)  
**Fuente:** Entrevista Gerente de Operaciones (GO) - "Gestión de Clientes", Entrevista Gerente de Producto (GP) - "Proceso Ideal Cliente"

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

**Prioridad:** MUST (Crítico)  
**Fuente:** Entrevista GO - "Datos esenciales para perfiles detallados", Entrevista GP - "Información esencial para perfiles", Entrevista GT - "Base de Datos NoSQL/Relacional Híbrida"

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

**Prioridad:** MUST (Crítico)  
**Fuente:** Entrevista GO - "Tipos de servicios", "Adaptar el sistema", Entrevista GT - "Esquema Flexible", "Extensibilidad y Patrones de Diseño"

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

**Prioridad:** MUST (Crítico)  
**Fuente:** Entrevista GO - "Pasos fundamentales", Entrevista GP - "Interfaz intuitiva para agentes", Entrevista GT - "Motor de Reglas de Negocio", "API Gateway"

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
- Latencia de búsqueda de proveedores: ≤ 5 segundos.

**Prioridad:** MUST (Crítico)  
**Fuente:** Entrevista GO - "Disponibilidad y tarifas", Entrevista GT - "Integración con GDS y APIs de Terceros", "Motor de Reglas de Negocio", "Caché Distribuida"

## RF-003: COTIZACIONES Y RESERVAS

### RF-003.1: Generación y Envío de Cotizaciones Detalladas
**Descripción:** El sistema debe generar cotizaciones claras, visualmente atractivas y detalladas para el cliente, con opciones de revisión y aprobación.  
**Actor:** Agente de Viajes, Cliente  
**Precondiciones:** Itinerario creado por el agente.

**Flujo Principal:**
1. Agente finaliza un itinerario y solicita una cotización.
2. Sistema genera una cotización con:
   - Desglose de servicios y precios (por persona y total).
   - Condiciones de cancelación.
   - Fotos y descripciones breves de cada servicio.
   - Opciones adicionales (upgrades, fechas alternativas, servicios extra).
3. Agente envía la cotización al cliente (vía email, portal).
4. Cliente recibe notificación y accede a la cotización en su portal de autoservicio.
5. Cliente puede revisar, hacer comentarios, solicitar cambios, o aceptar/rechazar.

**Criterios de Aceptación:**
- Cotización clara, visualmente atractiva, descargable en PDF.
- Desglose de costes transparente.
- Portal del cliente con opción de comentarios y aprobación.
- Notificaciones automáticas al cliente sobre nuevas cotizaciones.

**Prioridad:** MUST (Crítico)  
**Fuente:** Entrevista GO - "Cotización detallada", Entrevista GP - "Portal del Cliente"

### RF-003.2: Flujo de Reserva y Pago
**Descripción:** El sistema debe procesar la reserva de servicios con proveedores y gestionar pagos de clientes de forma segura y eficiente, incluyendo múltiples divisas y métodos de pago.  
**Actor:** Cliente, Agente de Viajes, Sistema automático  
**Precondiciones:** Cotización aceptada por el cliente y fondos disponibles.

**Flujo Principal:**
1. Cliente aprueba la cotización en su portal.
2. Sistema presenta opciones de pago (PSE, tarjetas, Nequi, Daviplata, transferencia).
3. Cliente selecciona método de pago y procede.
4. Sistema (vía pasarela segura) procesa el pago.
5. Si el pago es exitoso, el sistema env
