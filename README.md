# Switch Scroll · React

Landing blanca con un único componente interactivo, de 1.140 px de ancho máximo.

## Abrir la demo

```sh
npm install
npm run dev
```

## Llevarlo a otro proyecto

Copia únicamente **SwitchScroll.jsx**. Incluye el SVG original, las seis imágenes de muestra, los estilos encapsulados y toda la interacción. Solo necesita React (19 o superior). No necesita archivos CSS, librerías de animación ni imágenes externas.

```jsx
import SwitchScroll from './SwitchScroll';

const cards = [
  {
    id: 'primera',
    image: '/imagenes/primera.jpg',
    imagePosition: 'center',
    eyebrow: '01 / DESCUBRE',
    title: 'Tu primera tarjeta',
    subtitle: 'El contenido que quieras mostrar.',
  },
  {
    id: 'segunda',
    image: '/imagenes/segunda.jpg',
    title: 'Tu segunda tarjeta',
    subtitle: 'Otra historia dentro de la pantalla.',
    href: '/proyecto',
    linkLabel: 'Ver proyecto',
  },
];

export default function Pagina() {
  return <SwitchScroll cards={cards} maxWidth={1140} scrollStep={0.7} />;
}
```

Sin `cards`, muestra seis tarjetas de ejemplo. Una lista vacía no renderiza nada. Con una tarjeta muestra el marco sin recorrido adicional ni controles.

### Propiedades

| Propiedad | Valor por defecto | Uso |
| --- | --- | --- |
| `cards` | Seis tarjetas de ejemplo | Imagen, título, subtítulo y enlace opcional |
| `maxWidth` | `1140` | Ancho máximo horizontal en píxeles |
| `scrollStep` | `0.7` | Alturas de pantalla necesarias para pasar una tarjeta |
| `onCardChange` | — | Recibe el índice activo, empezando en cero |
| `className`, `style` | — | Personalización del contenedor |

### Comportamiento

- El scroll normal de la página desvanece la tarjeta actual y después muestra la siguiente dentro del Switch fijo, sin desplazamiento ni dos tarjetas visibles a la vez. Al subir, vuelve a las anteriores. No bloquea la rueda ni el gesto táctil.
- El componente reserva espacio vertical para su recorrido; al terminar, continúa el resto de la página.
- No se muestran botones de navegación, puntos ni contador. La navegación se realiza mediante scroll o gestos táctiles.
- En pantallas de hasta 700 px y tablets en vertical de hasta 1.024 px se gira el marco 90°. El contenido permanece derecho. En apaisado se aprovecha el ancho disponible.
- Respeta la preferencia de movimiento reducido y excluye del foco los enlaces de tarjetas inactivas.
- Usa un documento con scroll normal. Evita `overflow: hidden/auto/scroll` o transformaciones en contenedores ancestros que cambien el comportamiento de `position: sticky`.
- Las tarjetas están pensadas para títulos y subtítulos breves. Ajusta el contenido si añades textos largos.

El archivo es de mayor tamaño porque conserva el SVG recibido, que contiene una imagen PNG incrustada. `main.jsx` e `index.html` son únicamente el arranque de la demo; no son necesarios para exportar el componente.
