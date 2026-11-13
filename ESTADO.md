# Estado — Por dónde empezó el cuaderno de aula

**Creado:** 12/11/2026 · **Replanteado:** 13/11/2026
**Estado:** 🟢 publicado en https://repositorioinformatico.github.io/cuaderno-de-aula/

## Qué se pidió

El 12/11, la v1:
> «quiero hacer esto en web estática que se almacene en el localstorage, hacer web donde se
> registre quien fue el ultimo que inicio el cuaderno de aula»

El 13/11, el cambio de rumbo (v2):
> «quiero que le cambies el titulo […] por donde empezo a rellenarse el cuaderno de aula en la
> ultima clase […] que visualmente muestre la disposicion de mesas y nombres y que me permita
> escribir los nombres de cada alumno en cada mesa y que indiquemos con una flecha grande verde
> en el lateral, la orientacion del cuaderno de aula hacia delante o hacia detras y en que
> seccion del cuaderno se tiene que escribir si arriba o abajo»

**Lo que cambió de verdad:** la v1 registraba *personas y horas* (quién se lo llevó). La v2 ya no
registra eso: es un **plano del aula** que responde a «¿por dónde seguimos hoy?». Todo lo de
cogidas y devoluciones se quitó.

## Qué está hecho

Un único `index.html` (22 KB, sin dependencias), con los tokens de color de sus otras webs
(`que-entrega-toca`), claro y oscuro automáticos.

- Rejilla de mesas redimensionable, sin rótulos de orientación en el plano, con la flecha
  de dirección a la izquierda y la mitad de la hoja a la derecha.
- Dos modos exclusivos: «editar nombres» (cada mesa es un campo de texto que se guarda según se
  escribe) y «editar mapa del aula» (solo entonces salen los botones de filas y columnas).
- Marcar la mesa de inicio tocándola (verde, con rótulo «Empezó aquí»).
- Flecha verde grande en el lateral que gira 180° entre delante y detrás.
- Dibujo de la hoja partida en dos mitades (arriba / abajo), al lado derecho del plano.
- Resumen grande arriba del todo con las tres cosas a la vez.
- Historial de 200 clases guardadas, borrables por fila.
- Exportar e importar `.json`.
- Todos los accesos a `localStorage` van en `try/catch`, con respaldo en memoria si falla.

## ⬜ Pendiente

- ⬜ **Probarlo en la tablet o en el ordenador del aula**, que es donde se va a usar de verdad.
- ⬜ **Decidir si vale con un solo dispositivo.** Si varios profesores van a marcarlo desde su
  propio móvil, **localStorage no puede hacerlo** y hay que llevarlo a avinox. Ver README.
- ⬜ **Ajustar el plano al aula real** (cuántas filas y cuántas mesas por fila). Ahora arranca en
  4 × 5 porque no sabemos la disposición real.
- ⬜ Decidir si hace falta distinguir **grupo** (1SMX A / B): ahora el plano es único, y si los dos
  grupos se sientan distinto habría que guardar un plano por grupo.
