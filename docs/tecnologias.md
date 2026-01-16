---
layout: default
title: Tecnologías
nav_order: 6
---

# Tecnologías Empleadas

[← Volver al índice](index.md)

---

## 🛠️ Stack Tecnológico

El proyecto **RecetasFáciles** utiliza un stack moderno y escalable, dividido en dos fases principales:

- **Fase 1 (Actual):** Frontend estático con HTML, CSS y JavaScript
- **Fase 2 (Futura):** Backend con PHP y MySQL

---

## 🎨 Frontend (Interfaz de Usuario)

### Estructura y Maquetación

#### HTML5
**Versión:** HTML Living Standard  
**Propósito:** Estructura semántica del contenido

**Características implementadas:**
- Uso de etiquetas semánticas (`<header>`, `<nav>`, `<main>`, `<section>`, `<article>`, `<footer>`)
- Formularios HTML5 con validación nativa
- Atributos `data-*` para manipulación con JavaScript
- Accesibilidad con atributos ARIA
- Meta tags para SEO y responsive design

**Ejemplo de estructura:**
```html
<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta name="description" content="Portal de recetas de cocina y repostería">
  <title>RecetasFáciles - Inicio</title>
</head>
<body>
  <header>
    <nav><!-- Navegación --></nav>
  </header>
  <main>
    <section><!-- Contenido --></section>
  </main>
  <footer><!-- Pie de página --></footer>
</body>
</html>
```

---

### Estilos y Diseño

#### CSS3
**Versión:** CSS3  
**Propósito:** Estilos y diseño responsive

**Características implementadas:**
- **CSS Grid** para layouts complejos
- **Flexbox** para componentes flexibles
- **Media Queries** para diseño responsive
- **Animaciones y transiciones** CSS
- **Variables CSS** (Custom Properties) para paleta de colores
- **Metodología BEM** para organización de clases

**Ejemplo de variables CSS:**
```css
:root {
  --primary-orange: #E07A36;
  --secondary-beige: #F4E8D8;
  --white: #FFFFFF;
  --dark-gray: #333333;
  --spacing-md: 20px;
  --border-radius: 15px;
}
```

**Media Queries utilizadas:**
```css
/* Móvil */
@media (max-width: 667px) { }

/* Tablet Vertical */
@media (min-width: 668px) and (max-width: 1023px) { }

/* Tablet Horizontal */
@media (min-width: 1024px) and (max-width: 1199px) { }

/* Desktop */
@media (min-width: 1200px) { }
```

**Organización de archivos CSS:**
```
css/
├── styles.css        # Estilos principales
├── responsive.css    # Media queries
├── components.css    # Componentes reutilizables
└── variables.css     # Variables CSS
```

---

### Interactividad

#### JavaScript (Vanilla)
**Versión:** ECMAScript 2020 (ES11)  
**Propósito:** Lógica de interacción del lado del cliente

**Características implementadas:**
- Manipulación del DOM
- Event listeners
- Validación de formularios
- Banner carrusel automático
- Menús desplegables
- Búsqueda en tiempo real
- Animaciones dinámicas

**Ejemplo - Banner Carrusel:**
```javascript
// carousel.js
class Carousel {
  constructor(selector) {
    this.carousel = document.querySelector(selector);
    this.slides = this.carousel.querySelectorAll('.slide');
    this.currentSlide = 0;
    this.autoPlayInterval = null;
  }

  init() {
    this.showSlide(0);
    this.autoPlay();
    this.addEventListeners();
  }

  showSlide(index) {
    this.slides.forEach((slide, i) => {
      slide.classList.toggle('active', i === index);
    });
  }

  nextSlide() {
    this.currentSlide = (this.currentSlide + 1) % this.slides.length;
    this.showSlide(this.currentSlide);
  }

  autoPlay() {
    this.autoPlayInterval = setInterval(() => {
      this.nextSlide();
    }, 5000);
  }
}

// Inicialización
const carousel = new Carousel('#banner-carousel');
carousel.init();
```

**Ejemplo - Búsqueda en tiempo real:**
```javascript
// search.js
const searchInput = document.getElementById('searchInput');
const recipeCards = document.querySelectorAll('.recipe-card');

searchInput.addEventListener('input', (e) => {
  const searchTerm = e.target.value.toLowerCase();
  
  recipeCards.forEach(card => {
    const title = card.querySelector('.recipe-title').textContent.toLowerCase();
    const description = card.querySelector('.recipe-description').textContent.toLowerCase();
    
    if (title.includes(searchTerm) || description.includes(searchTerm)) {
      card.style.display = 'block';
    } else {
      card.style.display = 'none';
    }
  });
});
```

**Organización de archivos JS:**
```
js/
├── main.js          # Script principal
├── carousel.js      # Banner carrusel
├── search.js        # Búsqueda y filtros
├── menu.js          # Menú hamburguesa
└── validation.js    # Validación de formularios
```

---

#### jQuery (Opcional)
**Versión:** 3.6.0  
**Propósito:** Simplificación de tareas comunes

**Características:**
- Simplificación de selección de elementos
- Animaciones suaves
- Peticiones AJAX (para fase backend)

**CDN utilizado:**
```html
<script src="https://code.jquery.com/jquery-3.6.0.min.js"></script>
```

---

### Recursos Externos

#### Google Fonts
**Fuentes utilizadas:**
- **Playfair Display** (700) - Títulos
- **Lato** (400, 700) - Cuerpo de texto

**Importación:**
```html
<link href="https://fonts.googleapis.com/css2?family=Playfair+Display:wght@700&family=Lato:wght@400;700&display=swap" rel="stylesheet">
```

#### Font Awesome
**Versión:** 6.4.0  
**Propósito:** Iconografía

**CDN utilizado:**
```html
<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
```

---

## 🔧 Backend (Implementación Futura)

### Servidor y Lógica

#### PHP
**Versión recomendada:** PHP 8.1 o superior  
**Propósito:** Lógica del servidor

**Funcionalidades planificadas:**
- Gestión de usuarios y sesiones
- CRUD de recetas
- Procesamiento de formularios
- Sistema de comentarios
- Subida y procesamiento de imágenes
- API REST para comunicación con frontend

**Estructura de archivos PHP:**
```
backend/
├── config/
│   ├── database.php      # Configuración BD
│   └── config.php        # Constantes
├── models/
│   ├── User.php
│   ├── Recipe.php
│   └── Category.php
├── controllers/
│   ├── UserController.php
│   ├── RecipeController.php
│   └── AuthController.php
├── views/
│   └── (plantillas)
└── api/
    └── endpoints/
```

**Ejemplo de conexión a base de datos:**
```php
<?php
// config/database.php
class Database {
    private $host = "localhost";
    private $db_name = "recetasfaciles";
    private $username = "root";
    private $password = "";
    private $conn;

    public function getConnection() {
        $this->conn = null;
        try {
            $this->conn = new PDO(
                "mysql:host=" . $this->host . ";dbname=" . $this->db_name,
                $this->username,
                $this->password
            );
            $this->conn->setAttribute(PDO::ATTR_ERRMODE, PDO::ERRMODE_EXCEPTION);
        } catch(PDOException $e) {
            echo "Error de conexión: " . $e->getMessage();
        }
        return $this->conn;
    }
}
?>
```

---

### Base de Datos

#### MySQL
**Versión recomendada:** MySQL 8.0 o MariaDB 10.6  
**Propósito:** Almacenamiento de datos

**Tablas principales:**

```sql
-- Tabla de usuarios
CREATE TABLE usuarios (
    id INT AUTO_INCREMENT PRIMARY KEY,
    nombre VARCHAR(100) NOT NULL,
    email VARCHAR(100) UNIQUE NOT NULL,
    password VARCHAR(255) NOT NULL,
    rol ENUM('visitante', 'usuario', 'admin') DEFAULT 'usuario',
    foto_perfil VARCHAR(255),
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

-- Tabla de categorías
CREATE TABLE categorias (
    id INT AUTO_INCREMENT PRIMARY KEY,
    nombre VARCHAR(50) NOT NULL,
    icono VARCHAR(100),
    descripcion TEXT
);

-- Tabla de recetas
CREATE TABLE recetas (
    id INT AUTO_INCREMENT PRIMARY KEY,
    titulo VARCHAR(200) NOT NULL,
    descripcion TEXT,
    ingredientes TEXT NOT NULL,
    pasos TEXT NOT NULL,
    tiempo_preparacion INT,
    dificultad ENUM('facil', 'media', 'dificil'),
    porciones INT,
    imagen VARCHAR(255),
    user_id INT,
    categoria_id INT,
    destacada BOOLEAN DEFAULT FALSE,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    FOREIGN KEY (user_id) REFERENCES usuarios(id) ON DELETE CASCADE,
    FOREIGN KEY (categoria_id) REFERENCES categorias(id)
);

-- Tabla de comentarios
CREATE TABLE comentarios (
    id INT AUTO_INCREMENT PRIMARY KEY,
    contenido TEXT NOT NULL,
    valoracion INT CHECK (valoracion BETWEEN 1 AND 5),
    user_id INT,
    receta_id INT,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    FOREIGN KEY (user_id) REFERENCES usuarios(id) ON DELETE CASCADE,
    FOREIGN KEY (receta_id) REFERENCES recetas(id) ON DELETE CASCADE
);

-- Tabla de favoritos
CREATE TABLE favoritos (
    id INT AUTO_INCREMENT PRIMARY KEY,
    user_id INT,
    receta_id INT,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    FOREIGN KEY (user_id) REFERENCES usuarios(id) ON DELETE CASCADE,
    FOREIGN KEY (receta_id) REFERENCES recetas(id) ON DELETE CASCADE,
    UNIQUE KEY unique_favorite (user_id, receta_id)
);
```

---

## 🐳 Docker (Opcional)

### Contenedorización

**Propósito:** Facilitar el despliegue y portabilidad del proyecto

**Dockerfile:**
```dockerfile
FROM php:8.1-apache

# Instalar extensiones de PHP
RUN docker-php-ext-install pdo pdo_mysql mysqli

# Habilitar mod_rewrite de Apache
RUN a2enmod rewrite

# Copiar archivos del proyecto
COPY . /var/www/html/

# Permisos
RUN chown -R www-data:www-data /var/www/html

EXPOSE 80
```

**docker-compose.yml:**
```yaml
version: '3.8'

services:
  web:
    build: .
    ports:
      - "8080:80"
    volumes:
      - ./:/var/www/html
    depends_on:
      - db
    environment:
      - DB_HOST=db
      - DB_NAME=recetasfaciles
      - DB_USER=root
      - DB_PASS=root

  db:
    image: mysql:8.0
    environment:
      MYSQL_ROOT_PASSWORD: root
      MYSQL_DATABASE: recetasfaciles
    volumes:
      - db_data:/var/lib/mysql
    ports:
      - "3306:3306"

  phpmyadmin:
    image: phpmyadmin/phpmyadmin
    ports:
      - "8081:80"
    environment:
      PMA_HOST: db
      PMA_USER: root
      PMA_PASSWORD: root

volumes:
  db_data:
```

**Comandos Docker:**
```bash
# Construir y levantar contenedores
docker-compose up -d

# Ver logs
docker-compose logs -f

# Detener contenedores
docker-compose down

# Acceder al contenedor
docker exec -it recetasfaciles_web_1 bash
```

---

## 🔄 Control de Versiones

### Git & GitHub

**Versión de Git:** 2.40 o superior

**Comandos principales utilizados:**
```bash
# Inicializar repositorio
git init

# Añadir archivos
git add .

# Commit
git commit -m "Descripción del cambio"

# Crear rama
git checkout -b feature/nueva-funcionalidad

# Subir a GitHub
git push origin main
```

**Estructura de ramas:**
```
main (producción)
├── develop (desarrollo)
├── feature/banner-carrusel
├── feature/sistema-busqueda
└── hotfix/correccion-responsive
```

**.gitignore:**
```
# Archivos del sistema
.DS_Store
Thumbs.db

# IDEs
.vscode/
.idea/

# Dependencias
node_modules/
vendor/

# Configuración local
config/local.php
.env

# Archivos temporales
*.log
*.tmp
```

---

## 📦 Herramientas de Desarrollo

### Editor de Código
- **Visual Studio Code** con extensiones:
  - Live Server
  - Prettier
  - ESLint
  - HTML CSS Support

### Prototipado
- **Visily** - Diseño de mockups y wireframes

### Testing (Futuro)
- **PHPUnit** - Testing unitario PHP
- **Jest** - Testing JavaScript

### Optimización
- **TinyPNG** - Compresión de imágenes
- **Google Lighthouse** - Auditoría de rendimiento

---

## 📊 Comparativa de Tecnologías

| Aspecto | Tecnología Elegida | Alternativas Consideradas |
|---------|-------------------|---------------------------|
| **Frontend Framework** | Vanilla JS | React, Vue.js |
| **CSS** | CSS3 Puro | Bootstrap, Tailwind CSS |
| **Backend** | PHP | Node.js, Python (Django) |
| **Base de Datos** | MySQL | PostgreSQL, MongoDB |
| **Hosting** | Por determinar | Hostinger, Heroku, AWS |

---

## 🚀 Roadmap Tecnológico

### Fase 1 - Actual ✅
- HTML5, CSS3, JavaScript
- Diseño responsive
- Componentes interactivos

### Fase 2 - Próximamente 🔜
- PHP + MySQL
- Sistema de autenticación
- CRUD completo

### Fase 3 - Futuro 🔮
- API REST
- Progressive Web App (PWA)
- Notificaciones push
- Optimización SEO avanzada

---

[← Anterior: Guía de Estilo](guia-estilo.md) | [→ Siguiente: Instalación](instalacion.md)
