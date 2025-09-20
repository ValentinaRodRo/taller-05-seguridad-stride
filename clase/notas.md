# 📝 Notas – Taller 5: STRIDE (Parte 1 – Caso en Clase)

## 🎯 Objetivo
Aplicar el marco **STRIDE** sobre un flujo crítico del sistema de logística (caso EdukIT/RedExpress) para identificar amenazas de seguridad, su impacto potencial y controles de mitigación.

---

## 🔄 Flujo analizado
El flujo seleccionado fue el de la **gestión de pedidos y logística** que involucra:
- Cliente Web / App / Mensajero
- Balanceador de Carga
- API Gateway
- Gestión de Usuarios
- Rastreo de Paquetes
- Procesamiento de Rutas
- BD Logística Centralizada
- Centro de Distribución
- Monitoreo y Alertas

---

## 🧪 Resultados del análisis STRIDE
A continuación, los principales hallazgos:

- **Cliente Web/App/Mensajero**
  - Riesgo de **suplantación** por robo de credenciales.
  - Ataques de **fuerza bruta** en login.
  - Posible **escalamiento de rol** (ej: cliente → administrador).

- **Balanceador de Carga**
  - Riesgo de **IP spoofing**.
  - Vulnerable a ataques **DDoS** que afectan la disponibilidad.

- **API Gateway**
  - Punto crítico con casi todas las categorías STRIDE.
  - Riesgos: **tokens falsos, manipulación de requests, denegación de servicio** y **abuso de configuración**.

- **Gestión de Usuarios**
  - Creación de **cuentas falsas**.
  - **Manipulación de roles** para escalar privilegios.
  - Exposición de datos sensibles.

- **Rastreo de Paquetes**
  - Posible manipulación de estados de entrega.
  - Riesgo de filtración de datos de ubicación en tiempo real.

- **Procesamiento de Rutas**
  - Manipulación de rutas para desviar pedidos.
  - Riesgo de fuga de información logística (destinos, horarios).

- **BD Logística Centralizada**
  - **Punto único de falla** del sistema.
  - Amenazas: robo de credenciales, manipulación de datos, fuga masiva de información y DoS contra la base.

- **Centro de Distribución**
  - Riesgo de acceso físico no autorizado.
  - Manipulación de inventario y fuga de datos de stock.

- **Monitoreo y Alertas**
  - Posible manipulación de métricas.
  - Riesgo de saturación → sin alertas activas.
  - Elevación de privilegios para borrar registros.

---

## 🔒 Controles de mitigación recomendados
- Autenticación multifactor (MFA) para usuarios y mensajeros.
- Cifrado TLS en tránsito y AES-256 en reposo.
- Tokenización de datos sensibles.
- Rate limiting y WAF en balanceador / gateway.
- Principio de privilegios mínimos en gestión de usuarios.
- Auditoría y trazabilidad para evitar repudio.
- Redundancia y réplicas para la BD logística.
- Seguridad física en el centro de distribución.
- Autenticación segura en Prometheus + Grafana.

---

## 📌 Reflexión
- Los **puntos más críticos** detectados son el **API Gateway** y la **BD Logística Centralizada**, porque concentran amenazas múltiples y de alto impacto.
- La arquitectura debe evolucionar hacia un esquema más **resiliente y distribuido** para reducir el riesgo de fallas únicas.
- La adopción de prácticas como **Zero Trust** y **Security by Design** serían clave para mejorar la seguridad en este flujo.

