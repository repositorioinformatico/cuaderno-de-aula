# Por dónde empezó a rellenarse el cuaderno de aula en la última clase

Web estática de una sola página con el **plano de mesas del aula**, para dejar marcado por dónde
empezó a rellenarse el cuaderno de aula, **hacia dónde** sigue y **en qué parte de la hoja** se
escribe.

🔗 https://repositorioinformatico.github.io/cuaderno-de-aula/

## Qué hace

- **Plano de mesas** en rejilla. El tamaño solo se toca entrando en `🗺️ Editar mapa del aula`:
  ahí aparecen `+ Fila` / `− Fila` / `+ Columna` / `− Columna` (hasta 12 × 10) y la medida actual.
  Fuera de ese modo los botones no se ven, para no tocarlos sin querer en clase.
- **Nombres de los alumnos**: con `✏️ Editar nombres` cada mesa pasa a ser un campo de texto. Se
  guarda según se escribe.
- **La mesa por donde empezó**: fuera del modo edición, tocar una mesa la marca en verde con el
  rótulo «Empezó aquí». Tocarla otra vez la desmarca.
- **Flecha verde grande en el lateral**: la dirección en que avanza el cuaderno. Se pulsa y gira
  180°, entre **hacia delante** y **hacia detrás**.
- **Parte de la hoja**: **justo debajo de la flecha**, bajo el rótulo «Hoy se escribe», un dibujo
  de la hoja partida en dos con la mitad **arriba** o **abajo** en verde. Van juntas a propósito:
  de una mirada al lateral se ve hacia dónde va el cuaderno y dónde toca escribir hoy.
- **Resumen arriba del todo** con el nombre, la posición, la dirección y la mitad de la hoja.
- **Guardar la clase** deja constancia fechada en el historial (200 clases, borrables una a una).
- **Copia de seguridad** en `.json`, descargable y recargable.

## Cómo funciona por dentro

Un solo `index.html`, sin dependencias ni build. Todo se guarda en **localStorage** del navegador,
bajo la clave `cuaderno-de-aula:v2`.

```json
{
  "filas": 4,
  "columnas": 5,
  "nombres": { "0-0": "Nombre del alumno" },
  "inicio": "0-0",
  "direccion": "delante",
  "seccion": "arriba",
  "marcado": "2026-11-13T10:00:00.000Z",
  "historial": [
    { "id": "…", "fecha": "…", "nombre": "…", "posicion": "fila 1, mesa 1",
      "direccion": "delante", "seccion": "arriba" }
  ]
}
```

Las mesas se identifican por `"fila-columna"` empezando en 0, así que `"0-0"` es la de arriba a
la izquierda del plano. Si se quitan filas o columnas y la mesa marcada se queda fuera del plano, se
desmarca sola.

**La v1 (quién se llevó el cuaderno) está en el historial de git**, en el commit `d76723b`. La
clave de localStorage cambió de `v1` a `v2`, así que los datos antiguos siguen ahí pero no se
leen.

## ⚠️ El límite que hay que tener claro

**localStorage es de un navegador y de un dispositivo.** Lo que se marque en la tablet del aula no
lo ve nadie desde su móvil, ni al contrario. Cada equipo tiene su propio plano y su propio
historial.

👉 **Sirve si se marca siempre desde el mismo sitio**: el ordenador del aula, una tablet fija, o el
móvil de una sola persona.

👉 **NO sirve si varios profesores van a marcarlo cada uno desde su propio móvil.** Para eso hace
falta que los datos vivan en un servidor, no en el navegador. La vía natural sería montarlo en
**avinox**, como el marco de fotos o el panel de fondeo, con un fichero JSON compartido.

🔴 **Los nombres de los alumnos se quedan en el navegador del dispositivo**, no salen a ningún
sitio ni viajan a GitHub. Pero si el aula usa un equipo compartido, cualquiera que abra la web los
ve: conviene usar solo el nombre, sin apellidos.

Otras cosas de localStorage: se vacía si se borran los datos del navegador, no existe en modo
privado, y si el navegador lo bloquea la web sigue funcionando pero solo recuerda las cosas
mientras la pestaña esté abierta. De ahí el botón de copia de seguridad.

## Publicar

El repo ya existe y Pages ya está activado, así que basta con:

```bash
cd dev/claude-code/cuaderno-de-aula
git add -A && git commit -m "…" && git push
```

GitHub Pages tarda **de 30 segundos a 2 minutos** en reconstruir. Si al recargar sigue saliendo lo
viejo, es la caché del navegador: recarga forzada (`⌘⇧R`).
