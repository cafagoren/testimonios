# Registro de pruebas — Aplicación de testimonios

**Responsable:** Paul Moreno Medrano  
**Modalidad:** Trabajo individual

## Entorno

- Node.js: v24.22.1
- npm: 11.19.1
- Compilación: `npm run build` completado correctamente.
- Repositorio y aplicación publicados en GitHub.

## Pruebas manuales de la etapa básica

Las siguientes pruebas se registraron con la lista completa de ocho testimonios, salvo P06 y P07, en las que se modificaron temporalmente los datos.

| Prueba | Resultado obtenido | Estado |
|---|---|---|
| P01 — Inicio | Se mostró el primer testimonio y el contador 1 de 8. | Aprobada |
| P02 — Siguiente | Siguiente avanzó al testimonio siguiente. | Aprobada |
| P03 — Límite superior | Desde el último, Siguiente volvió al primero. | Aprobada |
| P04 — Límite inferior | Desde el primero, Anterior pasó al último. | Aprobada |
| P05 — Aleatorio | Aleatorio cambió a otro testimonio válido. | Aprobada |
| P06 — Un registro | Ana permaneció al pulsar Anterior, Siguiente y Aleatorio. | Aprobada |
| P07 — Sin registros | Apareció “No hay testimonios disponibles” y no hubo tarjeta ni controles. | Aprobada |
| P08 — Ocho registros | La navegación llegó al testimonio 8 de 8. | Aprobada |
| P09 — Presentación | Se revisaron tres tamaños, navegación por teclado y un texto largo a 320 píxeles. | Aprobada |
| P10 — Compilación | `npm run build` terminó sin errores y no se observaron errores rojos de aplicación en la consola. | Aprobada |

## Traza de índices con tres registros

La siguiente tabla describe el comportamiento esperado con Ana, Luis y María. El índice comienza en cero y la posición visible comienza en uno.

| Acción | Índice antes | Índice después | Posición visible |
|---|---|---|---|
| Inicio | — | 0 | 1 de 3 |
| Siguiente desde Ana | 0 | 1 | 2 de 3 |
| Siguiente desde María | 2 | 0 | 1 de 3 |
| Anterior desde Ana | 0 | 2 | 3 de 3 |

Se comprobaron P01–P04 con los tres registros y coincidieron con los resultados esperados. En P05 se pulsó Aleatorio diez veces y en cada ocasión cambió a otro testimonio.
La función `random` elige un salto entre 1 y `total - 1`. Después suma ese salto al índice actual y usa `% total` para mantenerse dentro de la lista. Como el salto nunca es cero ni igual al total, el resultado es distinto del índice actual cuando hay dos o más testimonios. Con menos de dos, la función termina sin cambiarlo.

## Pruebas de reproducción automática

| Prueba | Resultado obtenido | Estado |
|---|---|---|
| A01 — Activación | Al pulsar Reanudar, el testimonio avanzó aproximadamente cada cinco segundos. | Aprobada |
| A02 — Pausa | Al pulsar Pausar, el testimonio permaneció igual durante más de cinco segundos. | Aprobada |
| A03 — Acción manual | Al pulsar Anterior, Siguiente o Aleatorio durante la reproducción, cambió el testimonio y la reproducción quedó pausada. | Aprobada |
| A04 — Reanudación | Reanudar volvió a activar el avance sin aceleración observada. | Aprobada |
| A05 — Límites | La reproducción pasó del testimonio 8 al 1. | Aprobada |
| A06 — Pocos datos | Con un registro no apareció Reanudar; con cero apareció el mensaje sin controles. | Aprobada |
| A07 — Limpieza | El efecto contiene `clearInterval` y no se observó aceleración al pausar y reanudar. | Aprobada |

## Revisión y corrección

Se revisó la reutilización de `Testimonial` mostrando dos tarjetas y modificando una regla de estilo compartida. El cambio se reflejó en ambas. Al terminar, se restauró la navegación.

Durante el primer despliegue, GitHub Actions mostró un error al consultar GitHub Pages. Después de seleccionar GitHub Actions como origen de publicación, se volvió a ejecutar el flujo y terminó correctamente. La aplicación publicada también se comprobó en el navegador.

## Capturas y documentación

- `evidencias/vista-320.png`
- `evidencias/vista-768.png`
- `evidencias/vista-1280.png`
- `README.md`: instalación, ejecución, estructura y decisiones.
- `REFLEXION_INDIVIDUAL.md`: explicación y reflexión sobre la práctica.

## Pendientes de revisión

- Revisión por otra persona o pareja, si se consigue. La práctica se realizó de forma individual.