# Aplicación de testimonios

Aplicación web creada con React y Vite para consultar testimonios de usuarios ficticios.

**Autor:** Paul Moreno Medrano

## Etapas completadas

- Navegación manual entre ocho testimonios.
- Reproducción automática con pausa y reanudación.
- Pruebas manuales, capturas y despliegue en GitHub Pages.

## Funcionalidades

- **Anterior** y **Siguiente** recorren los testimonios y conectan el primero con el último.
- **Aleatorio** selecciona un testimonio distinto cuando hay dos o más.
- **Reanudar** inicia el avance automático cada cinco segundos.
- **Pausar** detiene el avance automático.
- Usar un control de navegación manual también pausa la reproducción.
- Con un solo testimonio no aparece el botón de reproducción.
- Sin testimonios se muestra un mensaje informativo.

## Tecnologías y versiones

- React y Vite.
- Node.js: `v24.22.1`.
- npm: `11.19.1`.

Las versiones exactas de las dependencias están en `package.json` y `package-lock.json`.

## Instalación y ejecución

1. Descarga o clona el repositorio.
2. Abre una terminal en la carpeta del proyecto.
3. Instala las dependencias:

   ```bash
   npm install
   ```

4. Inicia el servidor de desarrollo:

   ```bash
   npm run dev
   ```

5. Abre la dirección **Local** que aparece en la terminal.

## Compilación

Para generar la versión de producción:

```bash
npm run build
```

## Estructura principal

```text
src/
├── components/
│   ├── Controls.jsx
│   └── Testimonial.jsx
├── App.jsx
├── data.js
├── main.jsx
└── styles.css
```

- `data.js` contiene los testimonios.
- `Testimonial.jsx` muestra los datos de una tarjeta.
- `Controls.jsx` presenta los controles de navegación.
- `App.jsx` coordina el índice y la reproducción automática.
- `main.jsx` monta la aplicación.
- `styles.css` contiene los estilos.

## Decisiones principales

Los datos se mantienen separados de los componentes. `App` conserva el índice del testimonio actual y pasa el registro y las funciones necesarias a sus componentes hijos.

La reproducción comienza pausada para permitir la lectura. `useEffect` crea el intervalo cuando se pulsa Reanudar y `clearInterval` lo limpia al pausar o desmontar el componente.

## Pruebas y evidencias

El archivo [REGISTRO_PRUEBAS.md](REGISTRO_PRUEBAS.md) contiene los resultados de las pruebas manuales. La carpeta `evidencias/` contiene capturas en tres tamaños de pantalla.

## Enlaces

- [Aplicación publicada](https://cafagoren.github.io/testimonios/)
- [Repositorio](https://github.com/cafagoren/testimonios)