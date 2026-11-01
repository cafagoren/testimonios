# Registro de pruebas — Aplicación de testimonios

## Entorno
- Node.js: v24.22.1
- npm: 11.19.1
- Rama Git: test/casos-basicos
- Compilación: `npm run build` completado correctamente.

## Pruebas manuales

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
| P09 — Presentación | Se revisó en escritorio y en 800 × 400; también se probó la navegación por teclado. | Aprobada |
| P10 — Compilación | `npm run build` terminó sin errores. | Aprobada |

## Pruebas de reproducción automática

| Prueba | Resultado obtenido | Estado |
|---|---|---|
| A01 — Activación | Al pulsar Reanudar, el testimonio avanzó aproximadamente cada cinco segundos. | Aprobada |
| A02 — Pausa | Al pulsar Pausar, el testimonio permaneció igual durante más de cinco segundos. | Aprobada |
| A03 — Acción manual | Al pulsar Siguiente durante la reproducción, cambió el testimonio y la reproducción quedó pausada. | Aprobada |
| A04 — Reanudación | Reanudar volvió a activar el avance sin aceleración observada. | Aprobada |
| A05 — Límites | La reproducción pasó del testimonio 8 al 1. | Aprobada |
| A06 — Pocos datos | Con un registro no apareció Reanudar; con cero apareció el mensaje sin controles. | Aprobada |
| A07 — Limpieza | El efecto contiene clearInterval y no se observó aceleración al pausar y reanudar. | Aprobada |

## Evidencias pendientes
- Capturas de P01–P10.
- Revisión del README.
- Revisión por otra persona/pareja, si se consigue.