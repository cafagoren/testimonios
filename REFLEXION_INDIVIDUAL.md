# Reflexión individual — Aplicación de testimonios

**Estudiante:** Paul Moreno Medrano  
**Modalidad:** Trabajo individual

## Organización de la aplicación

La aplicación está dividida en archivos con responsabilidades distintas. `data.js` contiene los testimonios, `Testimonial.jsx` presenta la tarjeta y `Controls.jsx` muestra los botones. `App.jsx` reúne los componentes y controla cuál testimonio se muestra.

Desde `App`, la información baja a los componentes mediante props: `Testimonial` recibe el objeto `item` y `Controls` recibe funciones para responder a los botones.

## Estado y navegación

`useState` guarda el índice del testimonio actual. Al pulsar un botón, ocurre esta secuencia:

1. El usuario hace clic.
2. El botón ejecuta el callback recibido desde `App`.
3. La función correspondiente llama a `setIndex`.
4. React vuelve a calcular la interfaz con el nuevo estado.
5. React actualiza en el DOM las partes necesarias.

El índice comienza en cero, mientras que el contador visible comienza en uno. Para conectar el último testimonio con el primero se utiliza el operador `%`, que permite regresar al inicio al llegar al límite.

## Reproducción automática

La reproducción comienza pausada. Al pulsar **Reanudar**, `useEffect` crea un intervalo que avanza el testimonio aproximadamente cada cinco segundos. Al pulsar **Pausar** o usar un botón de navegación manual, se detiene la reproducción.

La función `clearInterval` limpia el temporizador cuando corresponde. Esto ayuda a evitar que se acumulen intervalos y la reproducción se acelere.

## Experimento de reutilización

Durante la práctica mostré dos componentes `Testimonial` con datos diferentes y modifiqué una sola regla de la tarjeta. El cambio se reflejó en ambas tarjetas. Después restauré la navegación normal.

Reutilizar `Testimonial` evita escribir una tarjeta completa para cada persona. Por ejemplo, si necesito modificar la presentación de todas las tarjetas, puedo cambiar el componente o sus estilos en un solo lugar.

## Comparación y aprendizaje

Con una actualización manual del DOM tendría que localizar los elementos y cambiar por separado sus textos e imagen. Con React, cambio el estado y el componente calcula qué información mostrar.

La separación en archivos fue una decisión de organización del proyecto. React proporciona componentes, props y estado para construir y actualizar la interfaz.

Una dificultad de usar React en una aplicación pequeña es que requiere aprender herramientas y conceptos adicionales. Durante esta práctica también tuve que entender cuándo se crea y se limpia el temporizador.

Una pregunta que todavía puedo profundizar es: **¿cómo debería ajustarse el índice si los testimonios llegaran desde una API y la lista cambiara mientras la aplicación está abierta?**

## Forma de trabajo

Realicé la práctica de manera individual: preparé el entorno, organicé los datos, construí los componentes, implementé la navegación y la reproducción automática, y ejecuté las pruebas registradas.

Al trabajar solo, no hubo cambio de roles entre conductor y observador. La revisión por otra pareja queda pendiente, ya que requiere la participación de otras personas.

## Preguntas sobre reproducción automática

**¿Por qué se usa un efecto para el temporizador y un evento para el clic?**  
El clic ocurre como respuesta directa a una acción del usuario. El temporizador funciona durante un periodo de tiempo, por lo que `useEffect` permite crearlo y limpiarlo según el estado de reproducción.

**¿Qué problema evita `clearInterval`?**  
Elimina el intervalo cuando deja de ser necesario y evita que se acumulen temporizadores que hagan avanzar los testimonios demasiado rápido.

**¿Por qué no existe un Hook llamado `render`?**  
Renderizar es el proceso en el que React calcula la interfaz a partir del estado y las props. No es una función que este componente deba llamar como Hook.

**¿Qué pasaría si los datos llegaran de una API y cambiaran?**  
Habría que actualizar la lista y comprobar que el índice siga siendo válido cuando cambie su tamaño. También habría que considerar los estados de carga y error.