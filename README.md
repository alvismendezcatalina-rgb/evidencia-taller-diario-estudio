# Taller guiado: Diario de Estudio

Módulo 01 · El nuevo programador · Evidencia
Autor: Catalina Alvis M · SENA ADSO, Ficha 3267541

Este repositorio contiene las 4 estaciones del taller para que un agente de IA construya el **Diario de Estudio**, una web para registrar sesiones de estudio y ver la racha de días seguidos.

El archivo [AGENTS.md](AGENTS.md) también está disponible en la raíz.

---

## Estación 1. El prompt inicial

Prompt estructurado (rol, contexto, tarea, restricciones y salida) que fija las reglas del proyecto:

```markdown
# Rol: Desarrollador web senior que enseña a principiantes.
# Contexto: Diario de Estudio, prototipo local para registrar sesiones y ver rachas de estudio.
# Tarea:
1. Formulario (fecha, tema, minutos).
2. Validaciones (tema requerido, minutos > 0, fecha no futura).
3. Racha actual (días seguidos activos hasta hoy/ayer).
4. Lista de sesiones (de reciente a antigua).
5. Persistencia en localStorage.
# Restricciones: HTML, CSS y JS puros en 3 archivos (index.html, styles.css, app.js). Fechas estrictamente en hora local (crear con new Date(A, M-1, D), prohibido toISOString/UTC). Comentarios en español.
# Formato de salida: Plan corto, código por archivo, resumen y decisiones autónomas.
