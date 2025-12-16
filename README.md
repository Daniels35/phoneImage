# 📱 Phone Image Slider

**Componente visual de celular con carrusel de imágenes automático.**

Este proyecto es un prototipo de interfaz ("UI Component") creado para una sección personalizada de una Landing Page. Su objetivo es simular un teléfono móvil físico que muestra una galería de fotos en su pantalla, utilizando técnicas de posicionamiento CSS para lograr un efecto realista de "marco" sobre el contenido dinámico.

## 📋 Características Principales

### 🎨 Composición Visual (Mockup)
* **Marco de Dispositivo:** Utiliza una imagen PNG transparente de un celular (`celular.png`) como contenedor principal, creando la ilusión de un dispositivo físico.
* **Capas Superpuestas (Z-Index):** Implementa un manejo preciso de capas CSS. Las imágenes del carrusel se colocan con un `z-index: -10` para que aparezcan "detrás" del marco del teléfono pero dentro de su pantalla, mientras que elementos decorativos (como el chocolate) flotan por encima.
* **Elementos Decorativos:** Incluye imágenes flotantes adicionales (ej. `imagen-chocolate`) posicionadas absolutamente para romper la rigidez del diseño y dar profundidad.

### 🔄 Carrusel Automático
* **Transición Infinita:** Un script ligero en JavaScript rota las imágenes automáticamente en un bucle infinito.
* **Lógica de Clases:** Controla la visibilidad alternando la clase CSS `.imagen-activa`, lo que permite una separación limpia entre el estilo y la lógica.
* **Temporizador:** Configurado para cambiar de imagen cada **5 segundos** (5000 ms).

## 📂 Estructura del Proyecto

* `index.html`: Archivo único que contiene:
    * **Estructura HTML:** Contenedores para el celular y la lista de imágenes.
    * **Estilos CSS:** Reglas de posicionamiento absoluto/relativo para encajar las fotos en la pantalla del mockup.
    * **Script JS:** Lógica del intervalo de tiempo.

## 🚀 Instalación y Uso

1.  Descarga el archivo `index.html`.
2.  Asegúrate de que las URLs de las imágenes sean accesibles (actualmente apuntan a `chocoprints.co`).
3.  Abre el archivo en tu navegador web.
4.  Para integrarlo en tu web, copia el bloque `<div class="contenedor-celular">...</div>` y los estilos CSS correspondientes.

## ⚙️ Configuración (Hardcoded)

Este es un prototipo estático. Para personalizarlo, debes editar directamente el código HTML/JS:

**1. Cambiar Imágenes:**
Añade o elimina etiquetas `<img>` dentro del `div` con clase `contenedor-imagenes`.

**2. Ajustar Velocidad:**
Modifica el valor `5000` en la función `setInterval` al final del script.

---
**Versión:** 1.0 (Prototipo)
**Autor:** Daniel Diaz
**Tecnología:** HTML5, CSS3, Vanilla JS.

### 💻 Snippet de Lógica (Slider)

Este es el script que da vida al carrusel, seleccionando todas las imágenes y rotando la clase de visibilidad:

```javascript
document.addEventListener('DOMContentLoaded', function() {
    let imagenes = document.querySelectorAll('.contenedor-imagenes img');
    let indiceActual = 0;

    function cambiarImagen() {
        // Ocultar imagen actual
        imagenes[indiceActual].classList.remove('imagen-activa');
        
        // Calcular siguiente índice (bucle)
        indiceActual = (indiceActual + 1) % imagenes.length;
        
        // Mostrar nueva imagen
        imagenes[indiceActual].classList.add('imagen-activa');
    }

    // Ejecutar cada 5 segundos
    setInterval(cambiarImagen, 5000);
});
