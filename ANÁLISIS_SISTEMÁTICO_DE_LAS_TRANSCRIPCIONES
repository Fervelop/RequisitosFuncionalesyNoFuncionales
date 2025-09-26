# 📊 ESTRATEGIA PASO A PASO PARA IDENTIFICACIÓN DE REQUISITOS

Aquí se explica cómo se extrajeron sistemáticamente los requisitos funcionales y no funcionales de las entrevistas proporcionadas:

---

## Estrategia de Identificación de Requisitos

### 🔍 PASO 1: ANÁLISIS SISTEMÁTICO DE LAS TRANSCRIPCIONES

Para identificar requisitos de manera eficiente, se utilizó un sistema de codificación conceptual:

- 🟢 **Verde:** Verbos de acción que indican funcionalidades.
- 🔵 **Azul:** Números, métricas y restricciones cuantificables.
- 🟡 **Amarillo:** Actores y roles del sistema.
- 🔴 **Rojo:** Restricciones, limitaciones y reglas de negocio.
- 🟣 **Morado:** Integraciones y sistemas externos.

---

## Análisis de la Entrevista #1 (Gerente de Operaciones) y Entrevista (Transcripción Inicial)

### 🟢 Requisitos Funcionales Clave

**Gestión de Clientes y Personalización (CRM):**

- Implementar un CRM inteligente que permita la personalización basada en datos.
- Recolectar y centralizar datos clave como intereses de viaje, presupuesto estimado, restricciones y necesidades especiales.
- Ofrecer un portal de autoservicio para que los Clientes soliciten planes, revisen cotizaciones y confirmen itinerarios.

**Creación y Gestión de Itinerarios y Servicios:**

- Permitir al Agente buscar vuelos, hoteles, tours y seguros según intereses y presupuesto.
- Construir el itinerario día por día.
- El sistema debe gestionar y clasificar servicios como Vuelos, Alojamiento, Tours guiados, Transporte terrestre, Seguros de viaje y Experiencias únicas.
- Implementar un motor de comparación de disponibilidad y tarifas para optimizar ofertas, priorizando por precio, disponibilidad o valoración del proveedor.

**Cotizaciones y Reservas:**

- Generar cotizaciones claras y visualmente atractivas.
- Incluir desglose de servicios y precios, condiciones de cancelación, fotos, descripciones.
- Permitir descarga en PDF y envío por email.
- El sistema debe procesar el pago y enviar solicitudes/reservas automáticas a proveedores tras la aprobación del cliente.

**Gestión Post-Reserva y Soporte:**

- Implementar Notificaciones automáticas por email, WhatsApp o app (pagos, recordatorios, check-in).
- Ofrecer un Chat con agente o asistente virtual IA para dudas rápidas.
- Se requiere un Sistema para solicitudes de cambio o cancelación con trazabilidad de versiones.

**Informes y Análisis:**

- Generar informes de Ventas (por destino, agente, temporada) y Rentabilidad (por cliente, proveedor, viaje).
- Medir Índices de satisfacción y tendencias de clientes.

---

### 🔵 Requisitos No Funcionales (Rendimiento y Escalabilidad)

- Usuarios Concurrentes (Estimado): Entre 50 a 100 usuarios concurrentes.
- Volumen de Planes: Gestionar un gran número de planes de viaje anuales, proyectando 3,000-5,000 planes inicialmente, con potencial de crecimiento a 10,000+ en 3-5 años.
- Tiempo de Carga de Páginas: < 2 segundos (Gerente de Tecnología) y 2-3 segundos (Gerente de Operaciones).
- Tiempo de Búsqueda y Cotización: < 5 segundos (Gerente de Tecnología) y 5-10 segundos (Gerente de Operaciones).
- Disponibilidad: 99.9% (24/7).
- Tolerancia a Interrupciones: Mínima (máx. 1 hora/mes), idealmente no más de 30 minutos.

---

### 🔴 Restricciones y Limitaciones

- Plazo y Metodología: Plazo inicial de 6 meses para la versión funcional (MVP). Preferencia por desarrollo ágil en sprints.
- Infraestructura: Preferencia por solución en la nube (AWS, Azure, GCP).
- Legales/Regulatorias: Cumplimiento con GDPR, Ley de Protección de Datos local y regulaciones de países destino.
- Usabilidad: Interfaz drag-and-drop para agentes y panel de cliente visual y amigable.

---

### 🟡 Roles y Permisos (RBAC)

| Rol               | Acceso Principal                                               |
|-------------------|---------------------------------------------------------------|
| Administradores   | Acceso completo, configuración del sistema y gestión de usuarios. |
| Gerencia          | Solo lectura de reportes, métricas, datos financieros y supervisión de agentes. |
| Agentes de Ventas | Crear/editar itinerarios, ver/gestionar clientes asignados, cotizar y reservar. |
| Soporte al Cliente| Acceso a itinerarios y datos de contacto durante el viaje, gestión de incidencias. |
| Clientes          | Acceso solo a su perfil, itinerarios y cotizaciones.          |
| Contabilidad      | Acceso a información financiera y de pagos.                   |

---

## Análisis de la Entrevista #3 (Gerente de Tecnología y Ciberseguridad)

### 🟣 Requisitos de Integración y Arquitectura Técnica

**Arquitectura General:**

- Cloud-Native y Arquitectura Orientada a Microservicios (para escalabilidad y resiliencia).
- Uso de servicios en la nube (AWS Lambda, Kubernetes).

**Base de Datos y Datos:**

- Uso de Base de Datos NoSQL/Relacional Híbrida para manejar información estructurada y flexible.
- Necesidad de Esquema Flexible para añadir nuevos campos de personalización.
- Uso de Caché Distribuida (Redis o Memcached) para mejorar rendimiento en búsquedas.

**Integraciones Críticas:**

- Integración con GDS (Amadeus, Sabre, Travelport) y APIs de aerolíneas/hoteleras/agregadores (vía APIs RESTful o SOAP).
- Integración con Pasarelas de Pago (Stripe, PayPal, Adyen).
- Integración con software contable (ej. QuickBooks, SAP) y CRM.
- Integración con APIs de Mapas y Clima.

**Flujo de Reserva y Pagos:**

- Arquitectura de Eventos/Mensajería (Kafka, RabbitMQ) para orquestar la reserva de forma asíncrona y robusta.
- Motor de Reglas de Negocio configurable para la lógica de comparación y optimización de ofertas.
- Implementar patrones de Transacciones Distribuidas (Sagas) para garantizar la integridad en reservas multiproveedor.
- Servicio de Conversión de Divisas específico.

**Fiabilidad y Disponibilidad:**

- Despliegue en múltiples zonas de disponibilidad y regiones.
- Estrategias de Backup y Recuperación de Desastres (DR) con pruebas periódicas.
- Monitoreo Proactivo (SIEM, APM) para detectar problemas antes de que afecten a los usuarios.

---

### Seguridad y Privacidad (Requisitos No Funcionales)

- **Cifrado:** Cifrado Robusto de datos sensibles en tránsito (TLS 1.2+) y en reposo.
- **Autenticación:** Gestión de Identidades y Accesos (IAM) con Autenticación Multifactorial (MFA) obligatoria para empleados.
- **Cumplimiento Legal:** Diseño para ser compliant con GDPR, CCPA y otras regulaciones. Esto incluye gestión de consentimientos y derecho al olvido.
- **Datos Sensibles:** Considerar Tokenización/Anonimización para datos médicos y aplicar anonimización/pseudonimización para análisis de datos.
- **PCI DSS:** Cumplimiento PCI DSS si se manejan tarjetas de crédito.
- **Auditoría:** Monitoreo y Pruebas de Penetración periódicas.
- **Almacenamiento:** Almacenamiento de Datos Geográfico para cumplir con regulaciones de residencia de datos.

