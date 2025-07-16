# Convenciones de Código y Arquitectura Backend en Finova

En Finova seguimos un conjunto de **convenciones y estándares estrictos** para el desarrollo backend que aseguran calidad, seguridad y mantenibilidad del software. A continuación se describen las principales reglas y prácticas que deben cumplirse en nuestros proyectos.

---

## Nomenclatura y Estilo de Código

- **Variables:** Se utiliza el estilo **camelCase**, donde la primera letra es minúscula y cada palabra subsecuente inicia con mayúscula.  
  _Ejemplo:_ `totalAmount`, `userName`, `transactionCount`.

- **Clases:** Se emplea **PascalCase**, con la primera letra mayúscula y la inicial de cada palabra también capitalizada.  
  _Ejemplo:_ `UserController`, `PaymentService`, `OrderRepository`.

Esta diferenciación mejora la legibilidad e identificación rápida de los elementos en el código.

---

## Uso de Clases y Patrones de Diseño

Debido a la complejidad inherente del backend en Finova:

- Se hace **uso intensivo de clases** para fomentar la limpieza, modularidad y reutilización del código.  
- Aplicamos patrones de diseño, como el **Patrón Adaptador** para integrar librerías o servicios externos, asegurando desacople y flexibilidad.  
- Los servicios que dependen de lógica o integraciones externas deben implementarse siguiendo este patrón para facilitar mantenimiento y sustitución.

---

## Arquitectura de APIs

- La API backend estará **modularizada** en **módulos** que contienen:  
  - Rutas (endpoints)  
  - Controladores  
  - Servicios  
  - Middlewares opcionales

- Esta estructura modular mejora la escalabilidad y facilita la organización del código.

- Se promueve la creación de un **repositorio base estándar de Finova** para todas las APIs, que incluirá:  
  - Modularidad base y estructura predefinida  
  - Integración inicial con **WebSockets** (implementación comentada para activar según necesidad)  
  - Configuración de un **ORM** para gestión de base de datos (también comentado hasta activación)

Esto optimiza la velocidad de desarrollo y asegura consistencia entre proyectos.

---

## Documentación de Módulos

- Una vez que un módulo específico haya sido desarrollado y pase todas las pruebas correspondientes, **es obligatorio crear una documentación completa y actualizada de dicho módulo**.  
- Esta documentación debe incluir:  
  - Descripción funcional del módulo  
  - Endpoints que expone con sus parámetros, respuestas esperadas y códigos de estado  
  - Detalles de la lógica de negocio relevante  
  - Dependencias internas y externas  
  - Ejemplos de uso cuando sea aplicable  
- La documentación facilitará la transferencia de conocimiento, mantenimiento y colaboración entre equipos.

---

## Comunicación Backend - Frontend

- La comunicación entre backend y frontend **deberá realizarse siempre utilizando JSON** como formato estándar para solicitudes y respuestas.  
- Se pueden admitir otros formatos, como XML u otros, **solo en casos específicos donde APIs externas o requisitos particulares lo demanden**.  
- Ejemplos comunes de APIs que utilizan XML son integraciones con sistemas bancarios, servicios gubernamentales o SOAP legacy:  
  - Servicios SOAP en algunos sistemas financieros.  
  - APIs de pagos que requieren formatos específicos XML para validación.  
- Sin embargo, para mantener uniformidad y facilitar el desarrollo de frontend, JSON es el estándar recomendado y predeterminado en todos los desarrollos propios.

---

## Gestión de Base de Datos

- Usamos un **ORM (Object-Relational Mapping)** para manejar la base de datos, permitiendo a los desarrolladores interactuar con datos mediante objetos y abstraer detalles SQL.  
- Esto provee una base sólida, consistente y mantiene integridad en la manipulación de datos.

---

## Métricas y Monitorización

- Se implementará una **API específica y aislada para métricas**, que será:  
  - Rigurosamente segura con autenticación y autorización fuertes  
  - Con base de datos propia para almacenamiento histórico y consultas eficientes  
  - Útil para ser consumida desde software administrativo o dashboards internos, facilitando visualización y análisis de KPIs.

- Esta arquitectura permite:  
  - Modularización clara  
  - Mejor seguridad al aislar las métricas del resto de servicios  
  - No afectar la calidad ni desempeño de servicios principales  
  - Integración con sistemas de monitoreo externos cuando sea posible

---

## Seguridad en Backend

- La seguridad es prioritaria y se aplicará mediante:  
  - Uso de **JSON Web Tokens (JWT)** u otros sistemas de autenticación robustos  
  - Validación exhaustiva de entrada de datos  
  - Políticas estrictas de acceso y manejo de credenciales  
  - Auditorías y registros de accesos y acciones críticas

---

## Entorno de Pruebas

- Se crearán dominios y entornos específicos para pruebas, replicando al máximo las condiciones productivas para asegurar que el software funcione correctamente antes del despliegue.  
- El ambiente de pruebas debe estar aislado y separado de producción para evitar impactos en usuarios reales o datos sensibles.  
- Las pruebas incluirán tanto automáticas como manuales y la base de datos utilizada será anonimizada o generada artificialmente para respetar privacidad y normativas vigentes.

---



## Idioma en Nombres y Variables

- En Finova usamos **inglés como idioma estándar para nombrar variables, funciones, clases, archivos y directorios**.  
- Esto facilita la colaboración con equipos internacionales, el uso de librerías externas y busca estandarizar los términos técnicos.  
- Excepcionalmente se puede usar español para variables muy específicas de negocio internas o cuando la nomenclatura en español sea mucho más clara, pero siempre con justificación clara y mínima cantidad.

_**Ejemplos:**_  
Correcto: `userName`, `paymentService`, `orderRepository`  
Evitar: `nombreUsuario`, `servicioDePago`

---

## Arquitectura y Estructura de Código

### Separación de Funciones

- Se recomienda **separar la lógica en dos niveles**:  
  - **Funciones generales o utilitarias**: funciones reutilizables sin dependencia directa de módulos específicos, ubicadas en carpetas tipo `/utils` o `/helpers`.  
    _Ejemplo:_ formateo de fechas, validaciones comunes, manejo de errores genéricos.  
  - **Funciones específicas de módulo**: funciones propias a un módulo concreto, que pertenecen a servicios o controladores y están organizadas dentro del propio módulo.  

### Nombres y Organización de Directorios

- Los directorios deben reflejar claramente su contenido y propósito, e ir en **inglés, singular o plural de forma coherente**. Por ejemplo:  
  - `/routes` – Para definiciones de endpoints.  
  - `/controllers` – Controladores que reciben la petición y la encaminan.  
  - `/services` – Lógica de negocio y comunicación con bases de datos o APIs externas.  
  - `/middlewares` – Funciones middleware de Express u otro framework.  
  - `/models` – Definición de entidades y esquemas de base de datos.  
  - `/utils` o `/helpers` – Funciones auxiliares reutilizables.  

- Cuando se necesite un nuevo directorio o módulo, debe:  
  - Tener una responsabilidad clara y definida.  
  - Ser documentado y versionado igual que el resto del proyecto.  
  - Evitar albergar funciones sin cohesión o genéricas, que deberían ir a `/utils`.

### Ejemplo de Estructura
/src
/controllers
/middlewares
/models
/routes
/services
/utils
/config
/tests

## Manejo de Variables de Entorno

- Se usará un archivo dedicado para la inicialización y validación de variables de entorno, por ejemplo `config/index.js` o `config/env.js`.  
- Todas las variables de entorno necesarias serán marcadas como **requeridas**, es decir, si alguna de ellas no está presente o válida en el entorno de ejecución, **la aplicación no debe arrancar** y debe lanzar un error claro para evitar comportamientos inesperados.  
- Esto permite detectar configuraciones erróneas en etapas tempranas y facilita el despliegue en diferentes ambientes (desarrollo, pruebas, producción).

- Se recomienda usar librerías como [dotenv](https://www.npmjs.com/package/dotenv) para cargar variables en desarrollo, y mecanismos seguros para producción (vaults, servicios de secrets, etc.).

---
## Resumen

| Área                   | Convención / Práctica clave                                             |
|------------------------|------------------------------------------------------------------------|
| **Nomenclatura**       | camelCase para variables y métodos; PascalCase para clases             |
| **Estructura backend** | Modularidad con rutas, controladores, servicios y middlewares          |
| **Patrones**           | Uso obligatorio del patrón adaptador para servicios externos           |
| **Repositorio Base**   | Plantilla estándar con ORM y WebSocket preconfigurados                  |
| **Documentación**      | Documentar módulos finalizados y probados con detalle completo         |
| **Comunicación Frontend-Backend** | Comunicación en JSON por defecto; otros formatos solo casos especiales |
| **Métricas**           | API exclusiva y segura, base de datos propia, consumo desde dashboards  |
| **Seguridad**          | JWT, validaciones estrictas, auditoría y manejo seguro de credenciales |
| **Entorno de pruebas** | Ambiente aislado, datos anonimizados y replicación de producción       |
| **Idioma**                   | Uso de inglés para variables, funciones, clases y directorios (salvo excepciones justificadas) |
| **Separación Funciones**     | Funciones generales en `/utils`, funciones específicas en su módulo         |
| **Directorios**              | Nombres en inglés, estructura clara y modular                              |
| **Variables de entorno**      | Archivo dedicado que valida variables requeridas; si faltan, la app no arranca |

---

Con estas directrices aseguramos mantener un backend robusto, seguro, escalable y alineado con los estándares de calidad que Finova exige.
