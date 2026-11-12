# Estado — ¿Quién tiene el cuaderno?

**Creado:** 12/11/2026
**Estado:** 🟢 funcionando en local · ⬜ sin repo en GitHub · ⬜ sin Pages

## Qué se pidió
> «quiero hacer esto en web estática que se almacene en el localstorage, hacer web donde se
> registre quien fue el ultimo que inicio el cuaderno de aula»

## Qué está hecho
Un único `index.html` (16 KB, sin dependencias), con los estilos y los tokens de color de sus
otras webs (`que-entrega-toca`), claro y oscuro automáticos.

- Panel grande con quién lo tiene y el «hace X» que se actualiza solo.
- Registrar cogida / devolución, con grupo-hora y nota opcionales.
- Historial de 300 registros con borrado por fila.
- Autocompletado de nombres y grupos ya usados.
- Exportar e importar `.json`.
- Todos los accesos a `localStorage` van en `try/catch`, con respaldo en memoria si falla.

## ⬜ Pendiente
- ⬜ **Decidir si vale con un solo dispositivo.** Si varios profesores van a registrar desde su
  propio móvil, **localStorage no puede hacerlo** y hay que llevarlo a avinox. Ver README.
- ⬜ Crear el repo en GitHub y activar Pages (comandos en el README).
- ⬜ Probarlo en la tablet o en el ordenador del aula.
- ⬜ Preguntar a Joaquín qué significa exactamente «inició» el cuaderno: ahora está montado como
  **«lo cogió»** (quién se lo llevó y desde cuándo). Si lo que quiere es **quién escribió la última
  anotación**, el texto de los botones cambia, pero la estructura sirve igual.
