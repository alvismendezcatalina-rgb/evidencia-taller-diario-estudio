Evidencia del Taller Guiado
Estación 1 · El prompt inicial
Prompt de la primera versión 
1. Rol
Eres un desarrollador front-end senior especializado en aplicaciones web vanilla (HTML, CSS y JavaScript puro). Escribes código limpio, accesible y listo para usar sin build tools.
2. Contexto
Estamos creando la primera versión de «Diario de Estudio»: una web sencilla para que estudiantes anoten sus sesiones de estudio y se motiven al ver la racha de días consecutivos. El usuario final es un estudiante que quiere mantener el hábito de estudiar. No hay backend ni cuenta de usuario: todo se guarda en el navegador.
3. Tarea
Construye una aplicación web de una sola página que permita:
• Registrar una sesión de estudio con: fecha (por defecto hoy en fecha local), tema (texto libre) y minutos (número entero mayor que 0).
• Mostrar la racha actual: número de días consecutivos (incluyendo hoy) en los que hay al menos una sesión. La racha se calcula solo con la fecha local del usuario.
• Listar todas las sesiones guardadas, ordenadas de la más reciente a la más antigua.
• Guardar y cargar los datos en localStorage del navegador.
4. Restricciones
• Tecnología: solo HTML, CSS y JavaScript vanilla. Sin frameworks, sin librerías externas, sin build tools ni npm.
• Estructura: exactamente tres archivos: index.html, styles.css y app.js. Se debe poder abrir con doble clic (file://).
• Fechas: usar siempre la fecha local del usuario. Prohibido toISOString() y new Date("AAAA-MM-DD") para construir o comparar fechas de sesiones.
• Racha: un día cuenta si hay ≥1 sesión ese día (fecha local). La racha se rompe si falta un día entre hoy y el último día con sesión.
• Minutos: deben ser un entero > 0. Validar en el formulario.
• Interfaz clara y usable en móvil y escritorio.
5. Formato de salida
1. Entrega el código completo de los tres archivos.
2. Al final, un resumen breve de lo implementado.
3. Lista las decisiones que tomaste por tu cuenta (nombres de claves en localStorage, formato exacto de la fecha guardada, estilos visuales, etc.).
Estación 2 · El AGENTS.md
AGENTS.md del Diario de Estudio 
# AGENTS.md — Diario de Estudio

## Qué es el proyecto
Web sencilla para anotar sesiones de estudio y motivarse con la racha de días consecutivos. Sin backend ni cuentas: todo en el navegador.

## Stack y estructura
- Solo HTML, CSS y JavaScript vanilla.
- Tres archivos: index.html, styles.css, app.js.
- Se abre con doble clic (file://). Sin build tools ni npm.

## Convenciones
- Nombres en español en la UI; identificadores en camelCase o kebab-case.
- Comentarios solo cuando la lógica no es obvia.

## Datos
- Almacenamiento: localStorage. Clave: "diarioEstudio".
- Cada sesión: { id, date, tema, minutos }. date = "YYYY-MM-DD" en fecha local.

## Fechas y racha
- Siempre fecha local del usuario.
- PROHIBIDO: toISOString() y new Date("YYYY-MM-DD") para crear o comparar fechas de sesiones.
- Racha: días consecutivos (incluyendo hoy) con ≥1 sesión. Se rompe si falta un día.

## Límites
- Siempre: validar minutos > 0; usar fecha local; tres archivos únicamente.
- Pregunta antes: añadir dependencias, cambiar estructura de archivos, tocar localStorage de forma incompatible.
- Nunca: frameworks, backend, credenciales, servicios externos.

## Verificación
Antes de dar por terminado: probar racha con días consecutivos y con un hueco; comprobar que los datos sobreviven al recargar; validar minutos ≤ 0 y tema vacío.
Estación 3 · La petición de plan
Petición en modo Plan: sesiones por semana
Quiero añadir un resumen con los minutos estudiados en cada una de las últimas 4 semanas (de lunes a domingo), mostrado debajo de la racha.
Antes de escribir código, prepárame un plan con:
1. Cómo vas a agrupar las sesiones por semana usando la fecha local (reglas de AGENTS.md).
2. Qué archivos vas a modificar y qué cambia en cada uno.
3. Los casos límite: semanas sin sesiones, semana actual incompleta, fechas futuras.
4. Las dudas que debo decidir yo (por ejemplo, si la semana empieza en lunes o domingo).
5. Qué actualizarías en AGENTS.md y en MEMORY.md.
Estación 4 · La revisión
Plan del agente
## Plan: minutos por semana
1. Para cada sesión, calculo la semana con new Date(sesion.date).toISOString().
2. Sumo los minutos de cada semana.
3. Instalo la librería Chart.js para mostrar un gráfico de barras.
4. Muestro las semanas en el orden en que aparecen en los datos.
Errores detectados
1. Fechas en UTC / uso incorrecto de fechas
new Date(sesion.date).toISOString() puede cambiar el día según la zona horaria (UTC). Incumple la sección «Fechas y racha» de AGENTS.md, que prohíbe toISOString() y exige fecha local.
2. Dependencia nueva sin preguntar
Instalar Chart.js introduce una librería externa. El proyecto solo admite HTML/CSS/JS vanilla y el límite «pregunta antes» exige consultar antes de añadir dependencias.
3. Sin casos límite
El plan no menciona qué hacer con semanas sin sesiones, con la semana actual incompleta ni con fechas futuras. La petición de plan pedía explícitamente estos casos.
4. Orden incorrecto de las semanas
Mostrar las semanas «en el orden en que aparecen en los datos» no garantiza orden cronológico. Deben mostrarse de la más antigua a la más reciente (o al revés, de forma consistente).
5. Falta lo pedido en la petición de plan
No indica qué archivos modificará, no plantea dudas para que decida el usuario (ej. si la semana empieza en lunes o domingo) y no menciona actualizaciones a AGENTS.md ni MEMORY.md.
