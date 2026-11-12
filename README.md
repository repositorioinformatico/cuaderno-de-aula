# ¿Quién tiene el cuaderno?

Web estática de una sola página para registrar **quién fue el último que cogió el cuaderno de
aula** y desde cuándo lo tiene.

## Qué hace

- Arriba, en grande: **quién lo tiene ahora** y **desde cuándo** (con un «hace 2 h y 10 min» que
  se refresca solo cada minuto).
- Botón **«Lo cojo yo»** con nombre, grupo/hora y nota opcional.
- Botón **«Lo he devuelto»** para marcar que está en su sitio.
- **Historial** de los últimos 300 registros, borrables uno a uno.
- Los nombres y los grupos ya escritos se sugieren solos (`<datalist>`), así que a partir del
  segundo uso es escribir una letra y listo.
- **Copia de seguridad** en `.json`, descargable y recargable.

## Cómo funciona por dentro

Un solo `index.html`, sin dependencias ni build. Todo se guarda en **localStorage** del navegador,
bajo la clave `cuaderno-de-aula:v1`.

```json
{ "registros": [
  { "id": "…", "tipo": "cogida|devolucion", "nombre": "…",
    "grupo": "…", "nota": "…", "fecha": "2026-11-12T13:40:00.000Z" }
]}
```

## ⚠️ El límite que hay que tener claro

**localStorage es de un navegador y de un dispositivo.** Lo que se registre en la tablet del aula
no lo ve nadie desde su móvil, ni al contrario. Cada equipo tiene su propio historial.

👉 **Sirve si el cuaderno se registra siempre desde el mismo sitio**: el ordenador del aula, una
tablet fija, o el móvil de una sola persona.

👉 **NO sirve si varios profesores van a registrar cada uno desde su propio móvil.** Para eso hace
falta que los datos vivan en un servidor, no en el navegador. La vía natural sería montarlo en
**avinox**, como el marco de fotos o el panel de fondeo, con un fichero JSON compartido.

Otras cosas que conviene saber de localStorage: se vacía si se borran los datos del navegador, no
existe en modo privado, y si el navegador lo bloquea la web sigue funcionando pero solo recuerda
las cosas mientras la pestaña esté abierta. De ahí el botón de copia de seguridad.

## Publicar en GitHub Pages

```bash
cd dev/claude-code/cuaderno-de-aula
git init && git add -A && git commit -m "Primera versión"
gh repo create cuaderno-de-aula --public --source=. --push
gh api -X POST repos/repositorioinformatico/cuaderno-de-aula/pages \
  -f 'source[branch]=main' -f 'source[path]=/'
```

Queda en `https://repositorioinformatico.github.io/cuaderno-de-aula/`.
