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

