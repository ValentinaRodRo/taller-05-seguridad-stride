# Informe Técnico – Taller 5: Evaluación de Seguridad con STRIDE

## 🎯 Introducción
El presente informe documenta la aplicación del marco **STRIDE** sobre dos casos:
1. **Caso base (EdukIT – clase):** procesamiento de pagos en una plataforma educativa.
2. **Caso real (Compulens – cliente):** flujo de pedidos y producción de lentes.

El objetivo fue identificar amenazas de seguridad, su impacto y controles de mitigación, alineados con los principios de **confidencialidad, integridad, disponibilidad, autenticación y autorización**:contentReference[oaicite:0]{index=0}.

---

## 🧪 Metodología
Se utilizó el marco STRIDE (Spoofing, Tampering, Repudiation, Information Disclosure, Denial of Service, Elevation of Privilege) siguiendo los pasos:
- Selección de flujos críticos en cada sistema.
- Identificación de amenazas en cada punto del proceso.
- Registro en tablas STRIDE (Excel).
- Propuesta de estrategias de mitigación y priorización.

---

## 📊 Resultados

### Caso base: EdukIT
Flujo analizado: **Procesamiento de pagos con terceros**.
- Principales riesgos: suplantación de identidad, manipulación de órdenes de pago, fuga de datos de tarjetas, ataques DoS a la pasarela.
- Controles clave: autenticación multifactor, cifrado en tránsito y reposo, rate limiting, auditoría y trazabilidad.

### Caso real: Compulens
Flujo analizado: **Gestión de pedidos y producción de lentes**.
- Amenazas detectadas en:
  - **Cliente y Jefe Administrativo:** riesgo de suplantación y manipulación de pedidos.
  - **ERP Ocular y Base de Datos:** múltiples amenazas STRIDE, puntos más críticos.
  - **Producción y Mensajero:** riesgos de manipulación y repudio.
- Controles clave: digitalización de registros manuales con firma electrónica, control de roles y privilegios mínimos en ERP, cifrado de base de datos y backups, redundancia de infraestructura, seguridad física en producción.

---

## 🔒 Controles recomendados
- **Security by Design** desde la concepción de procesos:contentReference[oaicite:1]{index=1}.
- **Zero Trust:** validar identidad en cada acceso.
- **Auditoría y trazabilidad:** para evitar repudio.
- **Cifrado en tránsito (TLS 1.3) y en reposo (AES-256)**.
- **Segmentación de roles y accesos** en ERP y BD.
- **Redundancia y tolerancia a fallos** en sistemas críticos:contentReference[oaicite:2]{index=2}.

---

## 📌 Conclusiones
- En **EdukIT**, el riesgo más crítico está en la **pasarela de pagos**.  
- En **Compulens**, los puntos más vulnerables son el **ERP Ocular** y la **Base de Datos**, por concentrar información sensible y múltiples amenazas STRIDE.  
- La implementación de prácticas como **MFA, cifrado, segmentación de roles y monitoreo activo** es esencial para mejorar la seguridad.  

