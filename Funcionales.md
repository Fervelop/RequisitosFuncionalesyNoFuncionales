1. REQUISITOS FUNCIONALES - PLATAFORMA DE VIAJES PERSONALIZADOS

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
5. Sistema envía código de verificación por email.
6. Cliente confirma código.
7. Sistema crea cuenta y redirige a perfil.

**Criterios de Aceptación:**

- Validación básica de datos con formato estándar.
- Verificación dual:  email.
- Tiempo máximo de proceso: 5 minutos.

**Prioridad:** MUST (Crítico)
**Fuente:** Entrevista Gerente de Operaciones (GO) - "Gestión de Clientes", Entrevista Gerente de Producto (GP) - "Proceso Ideal Cliente"

## RF-002: CREACIÓN Y GESTIÓN DE ITINERARIOS Y SERVICIOS

### RF-002.1A: Creación del Perfil de Preferencias del Cliente

**Descripción:** El sistema debe permitir que el cliente complete un cuestionario inicial para definir su perfil de preferencias de viaje, incluyendo estilo, intereses, presupuesto y restricciones, el cual será utilizado para personalizar automáticamente su experiencia.

**Actor:** Cliente registrado

**Precondiciones:** El cliente ha creado y verificado su cuenta.

**Flujo Principal:**

1. El sistema presenta un cuestionario guiado (estilo asistente o chatbot) con un máximo de 15 preguntas.
2. El cliente responde sobre:
   * Estilo de viaje (lujo, aventura, familiar, etc.).
   * Intereses específicos (gastronomía, naturaleza, cultura...).
   * Nivel de actividad preferido.
   * Presupuesto estimado.
   * Restricciones y necesidades especiales (alimenticias, médicas, de accesibilidad o idioma).
3. El sistema guarda el perfil del cliente.
4. A partir del perfil, el sistema personaliza automáticamente el contenido del dashboard (destinos sugeridos, itinerarios recomendados, mensajes).
5. El cliente puede actualizar su perfil posteriormente desde su cuenta.

**Criterios de Aceptación:**

* El cuestionario no debe superar las 15 preguntas iniciales.
* El sistema debe guardar al menos: nombre, contacto, intereses, presupuesto, restricciones, historial de viajes.
* La personalización debe reflejarse inmediatamente en el dashboard del cliente.
* El cliente puede acceder y editar fácilmente su perfil.

**Prioridad:** MUST (Crítico)

**Fuente:**

* Entrevista GO – "Datos esenciales para perfiles detallados"
* Entrevista GP – "La recolección debe ser gradual y editable por el cliente"
* Entrevista GT – "Base de datos híbrida con esquema flexible y APIs seguras"

---

### RF-002.1B: Gestión del Perfil de Preferencias por el Agente

**Descripción:** El sistema debe permitir a los agentes acceder, completar y modificar el perfil de preferencias del cliente para facilitar la creación de itinerarios personalizados con base en la información recogida directa o indirectamente.

**Actor:** Agente de Viajes

**Precondiciones:** El cliente tiene un perfil registrado en el sistema.

**Flujo Principal:**

1. El agente accede al perfil de un cliente desde el módulo de gestión de clientes.
2. El sistema muestra la información recopilada por el cliente y permite editarla o complementarla.
3. El agente puede:
   * Agregar información adicional obtenida en interacciones (vía chat, llamada, correo).
   * Ajustar preferencias según cambios discutidos con el cliente.
4. El sistema utiliza el perfil actualizado para apoyar al agente en la creación de itinerarios personalizados.

**Criterios de Aceptación:**

* El sistema debe permitir a los agentes visualizar y editar todos los campos del perfil del cliente.
* Las modificaciones deben registrarse con fecha, agente responsable y versión.
* El perfil actualizado debe integrarse directamente en el motor de recomendaciones o reglas de negocio para planificación.
* Debe garantizarse trazabilidad y auditoría de los cambios.

**Prioridad:** MUST (Crítico)

**Fuente:**

* Entrevista GP – "Agente puede editar/completar el perfil con información adicional"
* Entrevista GT – "Permisos granulares para acceso seguro a datos del cliente"
* Entrevista GO – "La información del perfil alimenta la personalización"

### RF-002.1A: Catálogo de Vuelos

**Descripción:** El sistema debe permitir al agente de viajes consultar, filtrar y seleccionar vuelos disponibles desde múltiples proveedores para incluir en itinerarios.

**Actor:** Agente de Viajes

**Precondiciones:** Integraciones con GDS o APIs de aerolíneas configuradas.

**Flujo Principal:**

1. Agente accede al buscador de vuelos en el módulo de itinerarios.
2. Ingresa datos clave: origen, destino, fechas, cantidad de pasajeros, clase.
3. El sistema muestra resultados con:
   * Horarios, aerolínea, duración, escalas, precios, políticas.
4. Agente selecciona el vuelo deseado.
5. El vuelo se añade al itinerario del cliente.

**Criterios de Aceptación:**

* Búsqueda rápida (<5s) con múltiples filtros (precio, escalas, aerolínea).
* Integración funcional con al menos un GDS o API de aerolínea.
* Presentación clara de condiciones de cambio y cancelación.
* Vuelos añadidos se reflejan automáticamente en el itinerario.

---

### RF-002.1B: Catálogo de Alojamiento (Hoteles y similares)

**Descripción:** El sistema debe permitir a los agentes buscar y seleccionar opciones de alojamiento según preferencias del cliente y disponibilidad.

**Actor:** Agente de Viajes

**Precondiciones:** Catálogo de hoteles o integración con agregadores cargado.

**Flujo Principal:**

1. Agente accede al módulo de alojamiento.
2. Elige ubicación, fechas, número de huéspedes, rango de precios.
3. El sistema muestra alojamientos con:
   * Nombre, categoría, fotos, ubicación, precio, servicios incluidos.
4. Agente selecciona la opción adecuada y la añade al itinerario.

**Criterios de Aceptación:**

* Filtrado por estrellas, tipo de habitación, régimen de comidas, ubicación.
* Integración visual (galerías, mapas).
* Verificación de disponibilidad en tiempo real.
* Soporte para múltiples monedas.

---

### RF-002.1C: Catálogo de Tours y Actividades

**Descripción:** El sistema debe permitir buscar y seleccionar actividades, excursiones y experiencias para los clientes según su perfil e intereses.

**Actor:** Agente de Viajes

**Precondiciones:** Base de datos de tours y experiencias cargada o conectada por API.

**Flujo Principal:**

1. Agente busca actividades por destino y fecha.
2. Sistema filtra por tipo (cultural, aventura, gastronómico).
3. Muestra detalles: duración, puntos destacados, idioma, precio, restricciones.
4. Agente selecciona actividad y la añade al itinerario.

**Criterios de Aceptación:**

* Actividades clasificadas por tipo, intensidad, grupo o privado.
* Soporte para visualización multimedia.
* Sistema permite ver disponibilidad en tiempo real.

---

### RF-002.1D: Catálogo de Transportes y Traslados

**Descripción:** El sistema debe permitir seleccionar servicios de transporte terrestre (traslados, alquiler de autos, trenes) según el itinerario del cliente.

**Actor:** Agente de Viajes

**Flujo Principal:**

1. Agente selecciona punto de origen/destino, tipo de transporte.
2. Sistema muestra opciones: vehículos privados, traslados compartidos, trenes.
3. Se detalla el precio, horarios, condiciones y duración.
4. El servicio se añade al itinerario.

**Criterios de Aceptación:**

* Soporte para múltiples proveedores y modalidades (privado, shuttle, público).
* Visualización de horarios y puntos de encuentro.
* Personalización por cantidad de personas y equipaje.

---

### RF-002.1E: Catálogo de Seguros de Viaje

**Descripción:** El sistema debe permitir seleccionar planes de seguro de viaje adaptados al destino, duración y perfil del cliente.

**Actor:** Agente de Viajes

**Flujo Principal:**

1. Agente ingresa datos del viaje (fechas, destinos, edades).
2. Sistema muestra planes de seguro disponibles.
3. Agente compara coberturas (médico, cancelación, equipaje, COVID).
4. Selecciona el plan y lo incluye en el itinerario.

**Criterios de Aceptación:**

* Integración con aseguradoras o carga manual de productos.
* Comparador de coberturas visual e interactivo.
* Asignación por pasajero si es un grupo.

---

### RF-002.1F: Catálogo de Experiencias Únicas

**Descripción:** El sistema debe ofrecer experiencias únicas o personalizadas (eventos especiales, cenas exclusivas, experiencias VIP), destacando el valor agregado.

**Actor:** Agente de Viajes

**Flujo Principal:**

1. Agente accede a sección de experiencias.
2. Filtra por perfil del cliente, destino e intereses.
3. Sistema muestra propuestas personalizadas con fotos y descripciones.
4. Agente añade experiencia al itinerario como valor diferenciador.

**Criterios de Aceptación:**

* Curación manual o con reglas de perfil del cliente.
* Opción de marcar como "experiencia premium" o destacada.
* Asociada a cliente o segmento específico.

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
- Latencia de búsqueda de proveedores: ≤ 3 segundos.

**Prioridad:** MUST (Crítico)
**Fuente:** Entrevista GO - "Disponibilidad y tarifas", Entrevista GT - "Integración con GDS y APIs de Terceros", "Motor de Reglas de Negocio", "Caché Distribuida"

## RF-003: COTIZACIONES Y RESERVAS

### RF-003.1.1: Generación Automática de Cotización (Sistema)

**Descripción:** El sistema debe generar automáticamente una cotización clara, visual y detallada cuando el agente complete un itinerario, sin necesidad de intervención manual.

**Actor:** Sistema (Automatizado)

**Precondiciones:**

* El agente ha finalizado y guardado un itinerario de viaje completo en el sistema.
* Los datos de servicios tienen precios y descripciones disponibles.

#### **Flujo Principal:**

1. El agente guarda el itinerario como “listo para cotizar”.
2. El sistema genera automáticamente una cotización, que incluye:
   * Desglose detallado por servicio (vuelos, hoteles, tours, traslados, seguros, etc.).
   * Precios individuales y totales.
   * Condiciones de cancelación.
   * Imágenes y descripciones breves de los servicios.
   * Opciones adicionales (upgrades, fechas alternativas, extras).
3. El sistema guarda la cotización y la publica en el perfil del cliente.
4. El sistema envía una notificación automática al cliente (correo, push, etc.).

**Criterios de Aceptación:**

* Generación 100% automática sin intervención manual del agente.
* Contenido visualmente atractivo y completo.
* Notificación automática al cliente asociada a la nueva cotización.
* Cotización disponible en el portal del cliente inmediatamente.

---

### RF-003.1.2: Visualización y Gestión de Cotización (Cliente)

**Descripción:** El cliente debe poder visualizar la cotización generada, descargarla en PDF, enviar comentarios y confirmar o rechazarla desde su portal de autoservicio.

**Actor:** Cliente registrado

**Precondiciones:**

* El sistema ha generado y publicado una cotización para el cliente.
* El cliente ha iniciado sesión en su portal personal.

#### **Flujo Principal:**

1. Cliente recibe notificación de que tiene una nueva cotización disponible.
2. Accede a su portal personal de viajes.
3. Visualiza la cotización detallada, incluyendo:
   * Descripción día a día del itinerario.
   * Detalles de servicios y precios.
   * Imágenes, mapas u otros elementos visuales.
4. El cliente puede:
   * Descargar la cotización en formato PDF.
   * Enviar comentarios o solicitar ajustes.
   * Aceptar o rechazar la cotización.
5. El sistema registra la acción del cliente y actualiza el estado de la cotización.

**Criterios de Aceptación:**

* El cliente accede a la cotización desde su portal sin errores.
* Cotización visualmente clara, coherente y descargable.
* Funcionalidad de comentarios disponible (chat, formulario o similar).
* Botones de aceptación/rechazo funcionales y con confirmación.
* Cambios reflejados en el sistema en tiempo real.

### RF-003.2: Flujo de Reserva y Pago

**Descripción:** El sistema debe procesar la reserva de servicios con proveedores y gestionar pagos de clientes de forma segura y eficiente, incluyendo múltiples divisas y métodos de pago.
**Actor:** Cliente, Agente de Viajes, Sistema automático
**Precondiciones:** Cotización aceptada por el cliente y fondos disponibles.

**Flujo Principal:**

1. Cliente aprueba la cotización en su portal.
2. Sistema presenta opciones de pago (PSE, tarjetas, Nequi, Daviplata, transferencia).
3. Cliente selecciona método de pago y procede.
4. Sistema (vía pasarela segura) procesa el pago.
5. Si el pago es exitoso, el sistema confirma la reserva con los proveedores correspondientes vía API.
6. Registra la transacción en el sistema de backoffice.
7. Envía confirmación automática al cliente (correo y/o notificación en portal).
8. Genera documentos necesarios (confirmación de reserva, vouchers, recibo de pago).
9. Si el pago falla el sistema notifica al cliente con mensaje claro y opciones para reintentar o cambiar método.
10. Reserva queda en estado pendiente durante un tiempo configurable (ej. 1 hora) antes de expiración automática.

**Criterios de Aceptación:**

- Integración con pasarela(s) de pago seguras y certificadas.
- Soporte para pagos en COP y otras divisas según destino.
- Manejo seguro de datos financieros (cumplimiento PCI-DSS).
- Confirmación automática al cliente y reflejo en dashboard del agente.
- Manejo de errores claro y fluido (reintento, expiración, contacto con soporte).
- Registro completo de transacciones con trazabilidad.

**Prioridad:** MUST (Crítico)
**Fuente:** Entrevista GO - "Reserva y pago", Entrevista GT - "Integración con pasarelas", Entrevista CTO - "Confirmación automática tras pago exitoso"
