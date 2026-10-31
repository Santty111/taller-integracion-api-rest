# taller-integracion-api-rest
# Integración de Sistemas: Consumo de API REST con GoRest

Proyecto práctico correspondiente a la asignatura **Integración de Sistemas (ISWZ3104)** - Universidad de Las Américas (UDLA).

## Descripción del Proyecto
Implementación de una solución de integración basada en el patrón arquitectural **Remote Procedure Invocation (RPI)** que interactúa con la API REST de GoRest (`https://gorest.co.in/public/v2`). El flujo implementa operaciones CRUD completas, auditoría de eventos en logs, validación previa de datos (Defensive Programming) y gestión de recursos dependientes.

## Funcionalidades Implementadas
1. **Paginación:** Consulta de listados controlados mediante parámetros `page` y `per_page` (GET).
2. **Ciclo de Vida del Recurso:**
   - Alta de cliente con correo único corporativo (POST `201 Created`).
   - Verificación de persistencia en base de datos (GET `200 OK`).
   - Reemplazo completo de atributos (PUT `200 OK`).
   - Modificación atómica de estado a inactivo (PATCH `200 OK`).
   - Gestión de tareas vinculadas (POST `/users/{id}/todos` y PATCH `/todos/{id}`).
   - Baja física del cliente (DELETE `204 No Content`).
   - Comprobación de recurso inexistente (GET `404 Not Found`).
3. **Auditoría:** Registro estructurado de cada petición en el archivo `integracion.log` (fecha, hora, método, URL y código HTTP).
4. **Validación Previa:** Verificación estricta de dominios institucionales (`@techdistribuidora.ec`), campos requeridos y restricciones de dominio de valores antes de emitir peticiones a la red.
5. **Caminos de Error:** Manejo resiliente e interceptación controlada de respuestas `401 Unauthorized` y `422 Unprocessable Entity`.

## Requisitos de Ejecución
- Cuenta de Google para ejecutar el notebook en **Google Colab**.
- Token de acceso generado desde [GoRest](https://gorest.co.in/consumer/login).

## Instrucciones de Uso
1. Abre el notebook `taller_integracion_api_rest.ipynb` en Google Colab.
2. Ejecuta secuencialmente las celdas.
3. Cuando la celda de credenciales lo solicite, ingresa tu Access Token de GoRest en el campo seguro de `getpass` (la clave no quedará expuesta en el código ni en el historial de ejecución).
4. Al finalizar el ciclo, inspecciona el archivo `integracion.log` generado en la raíz del entorno.
