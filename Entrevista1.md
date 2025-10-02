# Entrevista 1: Gerente de Operaciones de Viajes

**Entrevistador**: Hola [Nombre del Gerente de Operaciones], gracias por tu tiempo. Estamos comenzando el diseño de nuestra nueva plataforma de viajes personalizada y tu perspectiva sobre las operaciones diarias es crucial.  
**Gerente de Operaciones**: Un placer. Estoy emocionado con la idea; necesitamos una solución que realmente optimice nuestro trabajo.

---

## I. Requisitos Funcionales

### A. Gestión de Clientes y Personalización

**Entrevistador**: ¿Cómo gestionamos actualmente la información de los clientes y cuáles son los datos esenciales para crear perfiles detallados y altamente personalizados?

**Gerente de Operaciones**:
Actualmente, es una mezcla de CRM heredado y muchas hojas de cálculo, lo que es ineficiente. Necesitamos un CRM robusto dentro del nuevo sistema. Los datos esenciales son:

- **Básicos**: Nombre, contacto, historial de viajes.
- **Preferencias**: Destinos deseados, tipo de viaje (aventura, relax, cultural), intereses específicos (gastronomía, arte, historia).
- **Presupuesto**: Rango de gasto para diferentes componentes.
- **Restricciones**: Dietéticas, movilidad, médicas.
- **Necesidades especiales**: Equipamiento, asistencia en aeropuertos, etc.
- **Documentación**: Copias de pasaportes, visas (para recordatorios y agilización).

---

### B. Creación de Itinerarios y Servicios

**Entrevistador**: ¿Cuáles son los pasos fundamentales y la información mínima necesaria para que un agente cree un plan de viaje, tanto nacional como internacional?

**Gerente de Operaciones**:

1. **Recepción de Solicitud**: Entender la solicitud inicial del cliente.
2. **Definición de Parámetros**: Destino(s), fechas, número de viajeros, presupuesto general.
3. **Selección de Servicios**: Vuelos, hoteles, tours, traslados (con flexibilidad para agregar otros).
4. **Configuración de Detalles**: Personalización de servicios (ej. tipo de habitación).
5. **Añadir Experiencias Únicas**: Recomendaciones o actividades locales especiales.
6. **Cálculo y Ajuste**: Coste total con posibilidad de ajuste.

**Información mínima por servicio**:

- Nombre
- Descripción
- Fechas y horarios
- Proveedores
- Coste
- Condiciones

**Tipos de servicios a gestionar y personalizar**:

- **Transporte**: Vuelos, trenes, buses, alquiler de coches, traslados.
- **Alojamiento**: Hoteles, resorts, apartamentos, glamping.
- **Actividades/Tours**: Excursiones, eventos, clases, aventuras.
- **Paquetes**: Prediseñados pero modificables.
- **Seguros**: De viaje, de cancelación.
- **Servicios adicionales**: Visas, asistencia en destino, comidas especiales.

**Clasificación**: Por tipo de servicio y por destino.

**Gestión de disponibilidad y tarifas**:

- Integración con **GDS** para vuelos y **APIs** para hoteles y operadores.
- Motor de comparación para mostrar las mejores ofertas según criterios del cliente.
- Priorización por precio, disponibilidad o valoración del proveedor.

---

### C. Cotizaciones y Reservas

**Entrevistador**: ¿Cómo generamos una cotización detallada y qué elementos debe incluir?

**Gerente de Operaciones**:

**Cotización** debe incluir:

- **Resumen General**: Destino, fechas, número de viajeros, precio total.
- **Desglose por Día/Segmento**: Actividades diarias y alojamientos.
- **Detalle de Servicios**: Hoteles, vuelos, tours.
- **Costes Detallados**: Precio por persona, impuestos, tasas, descuentos.
- **Condiciones**: Cancelación, pagos, seguros.
- **Opciones Adicionales**: Alternativas o mejoras sugeridas.

**Flujo de trabajo tras la aceptación del cliente**:

1. **Confirmación del Cliente** (portal de autoservicio).
2. **Generación de Órdenes** para cada proveedor.
3. **Integración Automática/Manual** con proveedores.
4. **Gestión de Pagos**: Multidivisa, múltiples métodos, registro de pagos.
5. **Confirmación de Proveedores**: Documentación adjunta.

---

### D. Gestión Post-Reserva y Soporte

**Entrevistador**: ¿Cómo manejar las comunicaciones con clientes y la gestión de cambios o incidencias?

**Gerente de Operaciones**:

- **Comunicaciones Automáticas**: Confirmaciones, recordatorios, notificaciones post-viaje.
- **Portal del Cliente**: Itinerario, documentación, contacto con agente.
- **Gestión de Cambios**: Módulo para registrar y procesar cambios.
- **Gestión de Incidencias**: Sistema de tickets o chat en vivo.

---

### E. Informes y Análisis

**Entrevistador**: ¿Qué informes y métricas clave necesitamos?

**Gerente de Operaciones**:

- **Ventas**: Por destino, agente, paquete, periodo.
- **Rentabilidad**: Por viaje, proveedor, servicio.
- **Rendimiento de Proveedores**: Calidad, fiabilidad, costes.
- **Preferencias de Clientes**: Tipos de viajes, destinos, servicios populares.
- **Análisis de Descuentos/Promociones**.
- **Cierre de Ventas**: Ratio cotizaciones vs reservas.

---

## II. Requisitos No Funcionales y Restricciones

### A. Seguridad y Privacidad

**Entrevistador**: ¿Cómo garantizamos la seguridad de datos y el cumplimiento de GDPR?

**Gerente de Operaciones**:

- **Encriptación**: En tránsito y en reposo.
- **Autenticación de doble factor**.
- **Restricciones de acceso** por rol.
- **Cumplimiento de GDPR**: Consentimiento, derecho al olvido, portabilidad de datos.

**Niveles de acceso**:

- **Administrador**: Acceso total, configuración.
- **Gerente**: Informes, proveedores, supervisión.
- **Agente de Ventas**: Gestión de viajes y clientes.
- **Soporte al Cliente**: Itinerarios, incidencias.
- **Contabilidad**: Información financiera y pagos.

---

### B. Rendimiento y Escalabilidad

**Entrevistador**: ¿Cuántos usuarios concurrentes y qué volumen esperamos?

**Gerente de Operaciones**:

- **Usuarios concurrentes pico**: 50 agentes, 500-1000 clientes.
- **Planes anuales**: 3,000–5,000 inicialmente, hasta 10,000+ a 3-5 años.
- **Tiempo de carga**:
  - Páginas: ≤ 2-3 segundos.
  - Cotizaciones complejas: ≤ 5-10 segundos.

---

### C. Integración y Flexibilidad

**Entrevistador**: ¿Con qué sistemas debemos integrarnos?

**Gerente de Operaciones**:

- **Sistemas existentes**: Xero, SAP B1, CRM heredado.
- **APIs externas**:
  - GDS (Amadeus, Sabre, Travelport)
  - Pasarelas de pago (Stripe, PayPal)
  - APIs de hoteles (Hilton, Marriott)
  - Aerolíneas, seguros, Google Maps

**Adaptabilidad del sistema**:

- Alta flexibilidad. Agregar destinos, proveedores o nuevos servicios debe ser **configurable sin desarrollo**.

---

### D. Fiabilidad y Disponibilidad

**Entrevistador**: ¿Cuál es la tolerancia a caídas?

**Gerente de Operaciones**:

- **Disponibilidad requerida**: 99.9%
- **Tolerancia máxima a caídas**: ≤ 30 minutos. Más de unas horas, inaceptable.

---

### F. Restricciones y Limitaciones

**Entrevistador**: ¿Hay presupuesto o plazo definido?

**Gerente de Operaciones**:

- Presupuesto inicial: [X cantidad]
- Fecha objetivo: Antes de la temporada alta de reservas del próximo año.

**Restricciones legales o culturales**:

- Sensibilidad a:
  - **Normativas de visado**
  - **Costumbres culturales** (idioma, vestimenta, festividades)
  - **Restricciones legales locales** (alcohol, conducta)
- El sistema debe:
  - Mostrar esta información a agentes/clientes
  - Almacenar preferencias de idioma
