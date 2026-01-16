# Guía de Estilo

[← Volver al índice](index.md)

---

## 🎨 Paleta de Colores

La paleta de colores ha sido seleccionada para transmitir **calidez, apetito y frescura**, características esenciales para un sitio web de recetas.

![Paleta de Colores](img/paleta-colores.png)

### Colores Principales

| Color | Muestra | Hexadecimal | RGB | Uso |
|-------|:-------:|-------------|-----|-----|
| **Naranja Oscuro** | ![#E07A36](https://img.shields.io/badge/-E07A36-E07A36?style=flat) | `#E07A36` | `rgb(224, 122, 54)` | Botones principales, enlaces, CTAs |
| **Beige** | ![#F4E8D8](https://img.shields.io/badge/-F4E8D8-F4E8D8?style=flat) | `#F4E8D8` | `rgb(244, 232, 216)` | Fondos secundarios, cards |
| **Blanco** | ![#FFFFFF](https://img.shields.io/badge/-FFFFFF-FFFFFF?style=flat-square&logoColor=black) | `#FFFFFF` | `rgb(255, 255, 255)` | Fondo principal, texto sobre oscuro |
| **Gris Oscuro** | ![#333333](https://img.shields.io/badge/-333333-333333?style=flat) | `#333333` | `rgb(51, 51, 51)` | Texto principal, headers |

---

### Colores de Estado (Badges de Dificultad)

| Nivel | Badge Visual | Hexadecimal | RGB |
|-------|:------------:|-------------|-----|
| **Fácil** | ![Fácil](https://img.shields.io/badge/Dificultad-Fácil-4CAF50?style=for-the-badge) | `#4CAF50` | `rgb(76, 175, 80)` |
| **Media** | ![Media](https://img.shields.io/badge/Dificultad-Media-FF9800?style=for-the-badge) | `#FF9800` | `rgb(255, 152, 0)` |
| **Difícil** | ![Difícil](https://img.shields.io/badge/Dificultad-Difícil-F44336?style=for-the-badge) | `#F44336` | `rgb(244, 67, 54)` |

### Código CSS

```css
:root {
  /* Colores principales */
  --primary-orange: #E07A36;
  --secondary-beige: #F4E8D8;
  --white: #FFFFFF;
  --dark-gray: #333333;
  
  /* Colores de estado */
  --difficulty-easy: #4CAF50;
  --difficulty-medium: #FF9800;
  --difficulty-hard: #F44336;
  
  /* Colores de interacción */
  --hover-orange: #C96A2E;
  --shadow: rgba(0, 0, 0, 0.1);
}
```

---

## ✍️ Tipografía

Las fuentes seleccionadas provienen de **Google Fonts**, garantizando compatibilidad cross-browser y carga rápida.

### Fuente para Títulos: Playfair Display

**Familia:** Serif  
**Peso utilizado:** 700 (Bold)  
**Descarga:** [Google Fonts - Playfair Display](https://fonts.google.com/specimen/Playfair+Display)

**Uso:**
- Títulos principales (h1)
- Nombre de recetas destacadas
- Logotipo

**Características:**
- Elegante y sofisticada
- Alta legibilidad en tamaños grandes
- Transmite calidad y profesionalismo
- Inspiración en revistas gastronómicas

**Ejemplo:**
```css
h1, h2, .recipe-title-featured {
  font-family: 'Playfair Display', serif;
  font-weight: 700;
}
```

### Fuente para Cuerpo de Texto: Lato

**Familia:** Sans-serif  
**Pesos utilizados:**
- 400 (Regular) - Texto normal
- 700 (Bold) - Énfasis

**Descarga:** [Google Fonts - Lato](https://fonts.google.com/specimen/Lato)

**Uso:**
- Texto de navegación
- Descripciones de recetas
- Ingredientes y pasos
- Botones
- Footer

**Características:**
- Moderna y limpia
- Excelente legibilidad en pantalla
- Funciona bien en todos los tamaños
- Neutral y profesional

**Ejemplo:**
```css
body, p, a, button, .recipe-description {
  font-family: 'Lato', sans-serif;
  font-weight: 400;
}
```

### Importación de Fuentes

```html
<!-- En el <head> del HTML -->
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Playfair+Display:wght@700&family=Lato:wght@400;700&display=swap" rel="stylesheet">
```

---

## 📏 Jerarquía Tipográfica

| Elemento | Fuente | Tamaño Desktop | Tamaño Móvil | Peso | Line Height |
|----------|--------|----------------|--------------|------|-------------|
| **H1** (Título principal) | Playfair Display | 48px | 32px | 700 | 1.2 |
| **H2** (Secciones) | Playfair Display | 36px | 28px | 700 | 1.3 |
| **H3** (Nombre receta) | Lato | 24px | 20px | 700 | 1.4 |
| **Párrafo** | Lato | 16px | 14px | 400 | 1.6 |
| **Botones** | Lato | 16px | 14px | 600 | 1.5 |
| **Navegación** | Lato | 16px | 14px | 500 | 1.5 |
| **Footer** | Lato | 14px | 12px | 400 | 1.6 |

### Código CSS

```css
/* Títulos */
h1 {
  font-family: 'Playfair Display', serif;
  font-size: 48px;
  font-weight: 700;
  line-height: 1.2;
  color: var(--dark-gray);
}

h2 {
  font-family: 'Playfair Display', serif;
  font-size: 36px;
  font-weight: 700;
  line-height: 1.3;
}

h3 {
  font-family: 'Lato', sans-serif;
  font-size: 24px;
  font-weight: 700;
  line-height: 1.4;
}

/* Texto de cuerpo */
p, li {
  font-family: 'Lato', sans-serif;
  font-size: 16px;
  font-weight: 400;
  line-height: 1.6;
  color: var(--dark-gray);
}

/* Responsive */
@media (max-width: 667px) {
  h1 { font-size: 32px; }
  h2 { font-size: 28px; }
  h3 { font-size: 20px; }
  p { font-size: 14px; }
}
```

---

## 🎯 Iconografía

**Fuente de Iconos:** Font Awesome 6 (Free)  
**Enlace:** [Font Awesome](https://fontawesome.com)

### Iconos Utilizados

| Elemento | Icono | Código HTML |
|----------|-------|-------------|
| **Tiempo** | ⏱️ | `<i class="fa-regular fa-clock"></i>` |
| **Porciones** | 👤 | `<i class="fa-solid fa-user"></i>` |
| **Dificultad** | ⭐ | `<i class="fa-solid fa-star"></i>` |
| **Búsqueda** | 🔍 | `<i class="fa-solid fa-magnifying-glass"></i>` |
| **Menú hamburguesa** | ☰ | `<i class="fa-solid fa-bars"></i>` |
| **Facebook** | 📘 | `<i class="fa-brands fa-facebook"></i>` |
| **Instagram** | 📷 | `<i class="fa-brands fa-instagram"></i>` |
| **Postres** | 🍰 | `<i class="fa-solid fa-cake-candles"></i>` |
| **Platos** | 🍲 | `<i class="fa-solid fa-bowl-food"></i>` |
| **Bebidas** | 🥤 | `<i class="fa-solid fa-glass-water"></i>` |
| **Corazón** (Favoritos) | ❤️ | `<i class="fa-regular fa-heart"></i>` |

### Importación de Font Awesome

```html
<!-- En el <head> del HTML -->
<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
```

---

## 🔘 Botones y Componentes

### Botón Principal

**Uso:** Call-to-action principal (Ver Receta, Registrarse, etc.)

```css
.btn-primary {
  background-color: var(--primary-orange);
  color: var(--white);
  padding: 15px 40px;
  border-radius: 25px;
  border: none;
  font-family: 'Lato', sans-serif;
  font-size: 16px;
  font-weight: 600;
  cursor: pointer;
  transition: all 0.3s ease;
}

.btn-primary:hover {
  background-color: var(--hover-orange);
  transform: scale(1.05);
  box-shadow: 0 5px 15px rgba(224, 122, 54, 0.3);
}

/* Responsive */
@media (max-width: 667px) {
  .btn-primary {
    padding: 12px 30px;
    font-size: 14px;
  }
}
```

### Botón Secundario

**Uso:** Acciones secundarias (Cancelar, Ver más, etc.)

```css
.btn-secondary {
  background-color: transparent;
  color: var(--primary-orange);
  padding: 15px 40px;
  border-radius: 25px;
  border: 2px solid var(--primary-orange);
  font-family: 'Lato', sans-serif;
  font-size: 16px;
  font-weight: 600;
  cursor: pointer;
  transition: all 0.3s ease;
}

.btn-secondary:hover {
  background-color: var(--primary-orange);
  color: var(--white);
}
```

---

## 🃏 Cards de Receta

**Diseño:** Tarjetas elevadas con sombra suave

```css
.recipe-card {
  background-color: var(--white);
  border-radius: 15px;
  overflow: hidden;
  box-shadow: 0 4px 15px var(--shadow);
  transition: all 0.3s ease;
}

.recipe-card:hover {
  transform: translateY(-10px);
  box-shadow: 0 8px 25px rgba(0, 0, 0, 0.2);
}

.recipe-card img {
  width: 100%;
  height: 200px;
  object-fit: cover;
}

.recipe-card-content {
  padding: 20px;
}

.recipe-card-title {
  font-family: 'Lato', sans-serif;
  font-size: 18px;
  font-weight: 700;
  color: var(--dark-gray);
  margin-bottom: 10px;
}

.recipe-card-meta {
  display: flex;
  gap: 15px;
  font-size: 14px;
  color: #666;
  margin-bottom: 15px;
}

.difficulty-badge {
  display: inline-block;
  padding: 5px 15px;
  border-radius: 20px;
  font-size: 12px;
  font-weight: 600;
  color: var(--white);
}

.difficulty-easy { background-color: var(--difficulty-easy); }
.difficulty-medium { background-color: var(--difficulty-medium); }
.difficulty-hard { background-color: var(--difficulty-hard); }
```

---

## 📐 Espaciado y Layout

### Sistema de Espaciado

```css
:root {
  --spacing-xs: 5px;
  --spacing-sm: 10px;
  --spacing-md: 20px;
  --spacing-lg: 30px;
  --spacing-xl: 40px;
  --spacing-xxl: 60px;
}
```

### Contenedor Principal

```css
.container {
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 var(--spacing-lg);
}

@media (max-width: 667px) {
  .container {
    padding: 0 var(--spacing-md);
  }
}
```

---

## 🌈 Efectos y Animaciones

### Transiciones Suaves

```css
.smooth-transition {
  transition: all 0.3s ease;
}
```

### Hover en Enlaces

```css
a {
  color: var(--primary-orange);
  text-decoration: none;
  transition: color 0.3s ease;
}

a:hover {
  color: var(--hover-orange);
  text-decoration: underline;
}
```

### Animación de Carga (Opcional)

```css
@keyframes fadeIn {
  from {
    opacity: 0;
    transform: translateY(20px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

.fade-in {
  animation: fadeIn 0.6s ease-out;
}
```

---

## ♿ Accesibilidad

### Contraste de Colores

Todos los colores cumplen con las pautas **WCAG 2.1 AA**:

| Combinación | Ratio de Contraste | Estado |
|-------------|-------------------|--------|
| Texto oscuro (#333) sobre blanco (#FFF) | 12.63:1 | ✅ AAA |
| Naranja (#E07A36) sobre blanco | 3.51:1 | ✅ AA |
| Blanco sobre naranja oscuro | 3.51:1 | ✅ AA |

### Focus States

```css
button:focus, a:focus, input:focus {
  outline: 3px solid var(--primary-orange);
  outline-offset: 2px;
}
```

---

[← Anterior: Arquitectura](arquitectura.md) | [→ Siguiente: Tecnologías](tecnologias.md)
