# Convenciones y Normas para el Frontend en Finova

En Finova, el equipo de desarrollo frontend sigue un conjunto de **estándares y buenas prácticas** que aseguran calidad, consistencia y mantenibilidad en nuestras aplicaciones. A continuación, se detallan los lineamientos clave para el desarrollo frontend.

---

## Uso de TypeScript y Tipado

- Todos los desarrolladores deben trabajar sobre bases en **TypeScript**, aprovechando su tipado estático para minimizar errores en tiempo de desarrollo.  
- Es obligatorio que las **interfaces estén bien definidas y documentadas** para cada dato y componente.  
- Se debe **evitar el uso del tipo `any`** tanto como sea posible para preservar la seguridad de tipos.  
- Únicamente se permitirá `any` en casos muy específicos derivados de restricciones de tiempo o variables particulares, y siempre con justificación clara y controlada.  
- Es recomendado usar herramientas de validación y librerías como [Zod](https://github.com/colinhacks/zod) para reforzar la validación de datos.

---

## Arquitectura y Uso de Clases y Funciones

- En frontend utilizamos una combinación de **clases y funciones**, según las necesidades:  
  - **Clases:** Para modelar entidades y servicios complejos, manteniendo consistencia con backend y reforzando la estructura orientada a objetos donde aplique.  
  - **Funciones:** Especialmente para componentes funcionales de React y hooks, aprovechando la interactividad y reactividad propias del framework.  

- React es el framework estándar para la mayoría de proyectos, usando:  
  - **Vite** como entorno de desarrollo predeterminado por su rapidez y simplicidad.  
  - **Next.js** en casos específicos que requieran renderizado del lado servidor (SSR) o por requerimientos especiales del proyecto, decisión tomada por el arquitecto.  

---

## Comunicación con Backend y APIs

- Toda comunicación con el backend **se hará en formato JSON**, que es el estándar para interoperabilidad, legibilidad y compatibilidad.  
- Solo en casos especiales, por ejemplo, integraciones con APIs legacy o servicios externos, se permitirá el consumo de otros formatos como XML o SOAP.  
  - Ejemplo: integración con sistemas bancarios que usan SOAP/XML.  
- El consumo de APIs se hará preferentemente con **Axios**, utilizando el **Patrón Adaptador** para desacoplar la implementación y facilitar el cambio o actualización de librerías.  

---

## Estilo Visual y Librerías para UI/UX

- Para animaciones y consistencia visual entre productos, se usarán librerías estándar como:  
  - **Framer Motion**  
  - **GSAP**  

- Para componentes 3D o experiencias avanzadas, se integrarán librerías como **three.js**.  

- El estilo visual será definido de acuerdo a las necesidades del proyecto, pero se fomentará la adopción del **diseño atómico** y la **reutilización extensiva de componentes** para garantizar mantenibilidad y coherencia.  

- Se dará prioridad al uso de librerías como **shadcn UI** para acelerar el desarrollo y mantener una interfaz moderna y accesible.

---

## Gestión de Estado

- El manejo del estado global o compartido se realizará preferentemente con la librería **Zustand**, que ofrece un enfoque eficiente y sencillo para evitar exponer datos sensibles en el almacenamiento local (localStorage).  

---

## Estructura y Organización del Proyecto

- El código será organizado en carpetas claras y modulares, separando componentes, hooks, servicios, utilidades y estilos.  
- Se promoverán buenas prácticas de separación de responsabilidades, facilitando la escalabilidad.  

## Nomenclatura y Estilo de Código

- La **nomenclatura en frontend seguirá los mismos estándares que en backend** para asegurar coherencia entre ambos equipos:  
  - **camelCase** para variables, propiedades y funciones.  
  - **PascalCase** para nombres de clases y componentes React.  

- Esto facilita la lectura y comprensión cuando se trabaja fullstack y mantiene la uniformidad en el ecosistema Finova.

---

## Documentación y Módulos Aprobados

- Todo **módulo o funcionalidad específica desarrollada deberá contar con documentación completa y vigente una vez aprobada y que haya pasado las pruebas correspondientes**.  
- La documentación debe incluir:  
  - Descripción funcional clara del módulo.  
  - Listado detallado de las interfaces e **interfaces TypeScript** involucradas, documentando tipos de datos y estructuras.  
  - **Ejemplos concretos de las peticiones HTTP que realiza el frontend a las APIs del backend**, incluyendo:  
    - Método HTTP  
    - Endpoint  
    - Parámetros o cuerpo de la solicitud  
    - Respuesta esperada (incluyendo estructura JSON)  
  - Consideraciones especiales en el consumo de datos o manejo de estados relacionados.

---

## Ejemplo de Petición del Frontend a Backend

// Ejemplo usando Axios con patrón adaptador en frontend

import axios from 'axios';

interface User {
id: string;
name: string;
email: string;
}

// Función que obtiene usuarios desde backend
async function fetchUsers(): Promise<User[]> {
const response = await axios.get<User[]>('/api/users');
return response.data;
}

text

---

## Diagramas de Flujo

- Se **recomienda ampliamente el uso de diagramas de flujo tanto para frontend como para backend** para documentar y visualizar los procesos, flujos de datos y la interacción entre sistemas.  
- Los diagramas de flujo ayudan a:  
  - Entender claramente la lógica del sistema.  
  - Mostrar cómo se comunican frontend y backend mediante APIs.  
  - Facilitar la colaboración entre equipos y disminuir malentendidos.  
- Se pueden utilizar herramientas como **Diagram.net, Microsoft Visio, or ProcessOn** para crear diagramas claros y reutilizables.  
- Es buena práctica que cada módulo clave tenga un diagrama que refleje su comportamiento y flujo de datos.

---


---

## Resumen

| Área                         | Convención / Práctica clave                                             |
|------------------------------|------------------------------------------------------------------------|
| **Lenguaje**                 | Uso obligatorio de TypeScript con interfaces bien definidas            |
| **Tipado**                   | Evitar `any`, usar tipos explícitos y librerías de validación          |
| **Arquitectura React**       | Combinación de clases y funciones; Vite preferido, Next.js cuando aplique|
| **APIs y Comunicación**      | Formato JSON por defecto, uso de Axios con patrón adaptador             |
| **UI/UX**                   | Animaciones con Framer Motion y GSAP; 3D con three.js; diseño atómico y componentes reutilizables; uso de shadcn UI |
| **Estado Global**            | Uso de Zustand para manejo de estado seguro y sencillo                  |
| **Organización del Código**  | Modular, con separación clara de responsabilidades                      |
| **Nomenclatura**       | camelCase para variables y funciones; PascalCase para clases y componentes |
| **Documentación Módulos** | Documentación completa con ejemplos de peticiones HTTP a backend |
| **Comunicación APIs**  | Uso estándar de JSON en peticiones y respuestas                   |
| **Diagramas de flujo** | Uso obligatorio para módulos clave en frontend y backend          |

---

Con estos lineamientos, Finova busca desarrollar interfaces frontend robustas, eficientes y agradables, que mantengan una experiencia de usuario consistente y faciliten el trabajo colaborativo y la escalabilidad del software.

# Anexo: Uso de JSON Web Tokens (JWT) en las Peticiones

En Finova, para garantizar la seguridad y autenticación en la comunicación entre frontend y backend, se aplicará el uso de **JSON Web Tokens (JWT)** como mecanismo estándar para proteger las APIs.

---

## Proceso General de Uso de JWT

1. **Generación del token:**  
   - Cuando un usuario inicia sesión, el backend valida sus credenciales y, si son correctas, genera un token JWT firmado con una clave secreta.  
   - Este token contiene información necesaria para identificar al usuario (payload) sin exponer datos sensibles.

2. **Entrega y almacenamiento seguro:**  
   - El backend envía el JWT al cliente como respuesta a la solicitud de login.  
   - El frontend debe almacenar este token de forma segura, preferentemente en **memoria o en cookies con flag HttpOnly y Secure**, para minimizar riesgos XSS.  
   - Evitar guardar JWT en localStorage si es posible, para mejorar la seguridad.

3. **Envío del token en solicitudes protegidas:**  
   - Para acceder a rutas o servicios protegidos, el frontend incluye el JWT en el header `Authorization` de cada petición usando el esquema `Bearer`.  
   - Ejemplo:  
     ```
     Authorization: Bearer <token_jwt>
     ```

4. **Validación en el backend:**  
   - El backend valida el JWT en cada petición protegida, verificando firma, expiración y permisos.  
   - Si el token es válido, permite el acceso y procesa la solicitud; si no, devuelve un error de autorización.

5. **Renovación de tokens:**  
   - El JWT suele tener una vida corta (ej. minutos). Para sesiones prolongadas, se utiliza un **refresh token** con vida más larga para obtener nuevos tokens de acceso sin pedir credenciales nuevamente.  
   - El frontend debe implementar la lógica para detectar expiración y solicitar renovación segura al backend.

---

## Ejemplo de Implementación en Frontend con Axios

import axios from 'axios';

// Función para configurar Axios con token JWT
function setupAxios(token: string) {
axios.defaults.headers.common['Authorization'] = Bearer ${token};
}

// Ejemplo de petición GET con token incluido
async function fetchUserProfile() {
const response = await axios.get('/api/user/profile');
return response.data;
}

text

---

## Buenas Prácticas sobre JWT en Finova

- Siempre usar **HTTPS** para evitar la interceptación del token.  
- No almacenar tokens en lugares accesibles por scripts no confiables (evitar localStorage si es posible).  
- Implementar mecanismos para la **revocación de tokens** y control de sesión en backend.  
- Definir correctamente los tiempos de expiración del token de acceso y refresh tokens para balancear seguridad y usabilidad.  
- Registrar y monitorear intentos fallidos de validación para detectar posibles ataques.

---

Esta integración de JWT asegura que nuestras APIs y aplicaciones gestionen usuarios y permisos de manera segura, alineada con las mejores prácticas y estándares modernos.

---

Referencias:

- [Implementar JWT simple con Express](https://4geeks.com/es/lesson/comprendiendo-jwt-y-como-implementar-un-jwt-simple-con-express)  
- [Cómo almacenar correctamente JWT en frontend](https://secture.com/como-almacenar-correctamente-tokens-jwt-en-el-front/)  
- [Qué es JWT y cómo funciona](https://openwebinars.net/blog/que-es-json-web-token-y-como-funciona/)
