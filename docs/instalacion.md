# Instalación y Configuración

[← Volver al índice](index.md)

---

## 💻 Requisitos del Sistema

### Requisitos Mínimos (Fase Frontend)

| Componente | Requisito |
|------------|-----------|
| **Sistema Operativo** | Windows 10/11, macOS 10.15+, Linux (Ubuntu 20.04+) |
| **Navegador Web** | Chrome 90+, Firefox 88+, Safari 14+, Edge 90+ |
| **Editor de Código** | Visual Studio Code, Sublime Text, o similar |
| **Git** | Versión 2.30 o superior |
| **Conexión a Internet** | Para CDNs (Google Fonts, Font Awesome) |

### Requisitos para Fase Backend (Futura)

| Componente | Versión Mínima |
|------------|----------------|
| **PHP** | 8.1 o superior |
| **MySQL** | 8.0 o MariaDB 10.6 |
| **Apache/Nginx** | Apache 2.4 o Nginx 1.18 |
| **Composer** | 2.0 o superior |
| **Node.js** (opcional) | 16.x o superior |

---

## 📥 Instalación - Fase 1 (Frontend)

### Paso 1: Clonar el Repositorio

```bash
# Clonar desde GitHub
git clone https://github.com/tu-usuario/RecetasFaciles.git

# Navegar al directorio
cd RecetasFaciles
```

### Paso 2: Estructura de Archivos

Verifica que la estructura sea la siguiente:

```
RecetasFaciles/
├── index.html
├── css/
│   ├── styles.css
│   ├── responsive.css
│   └── components.css
├── js/
│   ├── main.js
│   ├── carousel.js
│   ├── search.js
│   └── menu.js
├── img/
│   ├── recipes/
│   ├── categories/
│   └── logo.svg
├── pages/
│   ├── receta-detalle.html
│   ├── categoria.html
│   └── registro.html
└── README.md
```

### Paso 3: Abrir el Proyecto

#### Opción A: Con Live Server (Recomendado)

1. Abrir Visual Studio Code
2. Instalar la extensión **Live Server**
3. Clic derecho en `index.html`
4. Seleccionar **"Open with Live Server"**
5. Se abrirá automáticamente en `http://localhost:5500`

#### Opción B: Con servidor local de Python

```bash
# Python 3
python -m http.server 8000

# Abrir navegador en http://localhost:8000
```

#### Opción C: Con XAMPP/WAMP

1. Copiar la carpeta del proyecto a `htdocs/` (XAMPP) o `www/` (WAMP)
2. Iniciar Apache
3. Acceder a `http://localhost/RecetasFaciles`

### Paso 4: Verificar Funcionamiento

Comprueba que los siguientes elementos funcionen correctamente:

- ✅ El banner carrusel rota automáticamente cada 5 segundos
- ✅ La barra de búsqueda filtra recetas en tiempo real
- ✅ El menú desplegable de categorías se muestra correctamente
- ✅ Las cards de recetas tienen efecto hover
- ✅ El diseño es responsive en móvil, tablet y desktop

---

## 🗄️ Instalación - Fase 2 (Backend)

### Paso 1: Instalar XAMPP/WAMP/MAMP

#### Windows - XAMPP
1. Descargar desde [https://www.apachefriends.org](https://www.apachefriends.org)
2. Ejecutar instalador
3. Seleccionar componentes: Apache, MySQL, PHP, phpMyAdmin
4. Instalar en `C:\xampp`

#### macOS - MAMP
1. Descargar desde [https://www.mamp.info](https://www.mamp.info)
2. Instalar aplicación
3. Configurar puertos: Apache (8888), MySQL (8889)

#### Linux - Instalación manual
```bash
# Ubuntu/Debian
sudo apt update
sudo apt install apache2 php php-mysql mysql-server

# Verificar instalación
php -v
mysql --version
```

### Paso 2: Configurar Base de Datos

#### Crear la Base de Datos

1. Acceder a **phpMyAdmin**: `http://localhost/phpmyadmin`
2. Crear nueva base de datos: `recetasfaciles`
3. Configurar cotejamiento: `utf8mb4_unicode_ci`

#### Importar Estructura SQL

```sql
-- Ejecutar en phpMyAdmin o desde terminal

-- Crear base de datos
CREATE DATABASE IF NOT EXISTS recetasfaciles
CHARACTER SET utf8mb4
COLLATE utf8mb4_unicode_ci;

USE recetasfaciles;

-- Importar archivo SQL
SOURCE /ruta/al/proyecto/database/schema.sql;
```

**O desde terminal:**
```bash
mysql -u root -p recetasfaciles < database/schema.sql
```

### Paso 3: Configurar Archivo de Conexión

Crear el archivo `config/database.php`:

```php
<?php
// config/database.php

define('DB_HOST', 'localhost');
define('DB_NAME', 'recetasfaciles');
define('DB_USER', 'root');
define('DB_PASS', ''); // Cambiar en producción

// Crear conexión
try {
    $pdo = new PDO(
        "mysql:host=" . DB_HOST . ";dbname=" . DB_NAME . ";charset=utf8mb4",
        DB_USER,
        DB_PASS,
        [
            PDO::ATTR_ERRMODE => PDO::ERRMODE_EXCEPTION,
            PDO::ATTR_DEFAULT_FETCH_MODE => PDO::FETCH_ASSOC,
            PDO::ATTR_EMULATE_PREPARES => false
        ]
    );
} catch(PDOException $e) {
    die("Error de conexión: " . $e->getMessage());
}
?>
```

### Paso 4: Configurar Variables de Entorno

Crear archivo `.env` en la raíz del proyecto:

```env
# Configuración de Base de Datos
DB_HOST=localhost
DB_NAME=recetasfaciles
DB_USER=root
DB_PASS=

# Configuración de la Aplicación
APP_NAME="RecetasFáciles"
APP_URL=http://localhost/RecetasFaciles
APP_ENV=development

# Configuración de Sesión
SESSION_LIFETIME=7200

# Configuración de Subida de Archivos
MAX_FILE_SIZE=5242880
UPLOAD_PATH=uploads/recipes/
```

### Paso 5: Instalar Dependencias (Opcional)

Si usas Composer:

```bash
# Instalar Composer
curl -sS https://getcomposer.org/installer | php
sudo mv composer.phar /usr/local/bin/composer

# Instalar dependencias del proyecto
composer install
```

**composer.json:**
```json
{
    "name": "recetasfaciles/web",
    "description": "Portal de recetas de cocina",
    "require": {
        "php": ">=8.1"
    },
    "require-dev": {
        "phpunit/phpunit": "^9.5"
    },
    "autoload": {
        "psr-4": {
            "App\\": "src/"
        }
    }
}
```

### Paso 6: Configurar Permisos

#### Linux/macOS
```bash
# Permisos para directorios de escritura
sudo chmod -R 775 uploads/
sudo chmod -R 775 storage/

# Propietario Apache
sudo chown -R www-data:www-data uploads/
sudo chown -R www-data:www-data storage/
```

#### Windows
1. Clic derecho en carpetas `uploads/` y `storage/`
2. Propiedades → Seguridad
3. Dar permisos de escritura al usuario `IUSR`

### Paso 7: Datos de Prueba (Seed)

Insertar datos iniciales:

```sql
-- Insertar categorías
INSERT INTO categorias (nombre, icono, descripcion) VALUES
('Postres', 'fa-cake-candles', 'Deliciosos postres y dulces'),
('Entradas', 'fa-bowl-food', 'Aperitivos y entradas'),
('Desayunos', 'fa-mug-hot', 'Desayunos nutritivos'),
('Platos Principales', 'fa-utensils', 'Platos principales'),
('Cena', 'fa-moon', 'Cenas ligeras'),
('Bebidas', 'fa-glass-water', 'Bebidas refrescantes');

-- Insertar usuario administrador
INSERT INTO usuarios (nombre, email, password, rol) VALUES
('Administrador', 'admin@recetasfaciles.com', '$2y$10$...', 'admin');

-- Insertar receta de ejemplo
INSERT INTO recetas (titulo, descripcion, ingredientes, pasos, tiempo_preparacion, dificultad, porciones, categoria_id, user_id, destacada) VALUES
('Brownie de Chocolate', 
 'Delicioso brownie de chocolate con textura fudge',
 '200g chocolate, 150g mantequilla, 200g azúcar, 3 huevos, 100g harina',
 '1. Derretir chocolate. 2. Mezclar ingredientes. 3. Hornear 25 min a 180°C',
 40,
 'facil',
 12,
 1,
 1,
 true);
```

---

## 🐳 Instalación con Docker (Opcional)

### Requisitos
- Docker Desktop instalado
- Docker Compose

### Pasos

1. **Crear archivo docker-compose.yml** (ver sección Tecnologías)

2. **Construir contenedores:**
```bash
docker-compose up -d --build
```

3. **Verificar estado:**
```bash
docker-compose ps
```

4. **Acceder a la aplicación:**
- **Web:** http://localhost:8080
- **phpMyAdmin:** http://localhost:8081

5. **Ver logs:**
```bash
docker-compose logs -f web
```

6. **Detener contenedores:**
```bash
docker-compose down
```

---

## 🔧 Configuración Adicional

### Apache - Habilitar mod_rewrite

#### Linux
```bash
sudo a2enmod rewrite
sudo systemctl restart apache2
```

#### .htaccess (para URLs amigables)
```apache
RewriteEngine On
RewriteBase /RecetasFaciles/

# Redirigir a HTTPS (producción)
# RewriteCond %{HTTPS} off
# RewriteRule ^(.*)$ https://%{HTTP_HOST}%{REQUEST_URI} [L,R=301]

# Remover .php de las URLs
RewriteCond %{REQUEST_FILENAME} !-f
RewriteRule ^([^\.]+)$ $1.php [NC,L]
```

### PHP - Configuración recomendada

Editar `php.ini`:

```ini
; Subida de archivos
upload_max_filesize = 10M
post_max_size = 10M

; Errores (desarrollo)
display_errors = On
error_reporting = E_ALL

; Errores (producción)
; display_errors = Off
; error_reporting = E_ALL & ~E_NOTICE

; Zona horaria
date.timezone = Europe/Madrid

; Memoria
memory_limit = 256M
```

---

## ✅ Verificación de Instalación

### Checklist Frontend

- [ ] El sitio se abre correctamente en el navegador
- [ ] No hay errores en la consola del navegador (F12)
- [ ] Todos los estilos CSS se cargan correctamente
- [ ] Las fuentes de Google Fonts se visualizan bien
- [ ] Los iconos de Font Awesome se muestran
- [ ] El JavaScript funciona (banner, búsqueda, menú)
- [ ] El diseño es responsive en todos los dispositivos

### Checklist Backend

- [ ] Conexión a la base de datos exitosa
- [ ] Tablas creadas correctamente
- [ ] Datos de prueba insertados
- [ ] Login de administrador funcional
- [ ] Sesiones funcionando
- [ ] Subida de imágenes operativa
- [ ] Sin errores PHP en los logs

### Script de Diagnóstico

Crear `test-connection.php`:

```php
<?php
// test-connection.php

echo "<h1>Diagnóstico de Instalación</h1>";

// Test PHP
echo "<h2>✅ PHP instalado</h2>";
echo "Versión: " . phpversion() . "<br>";

// Test MySQL
try {
    require_once 'config/database.php';
    echo "<h2>✅ Conexión a MySQL exitosa</h2>";
    
    $stmt = $pdo->query("SELECT COUNT(*) as total FROM recetas");
    $result = $stmt->fetch();
    echo "Recetas en BD: " . $result['total'] . "<br>";
    
} catch(PDOException $e) {
    echo "<h2>❌ Error de conexión a MySQL</h2>";
    echo $e->getMessage();
}

// Test de extensiones PHP
echo "<h2>Extensiones PHP</h2>";
$extensions = ['pdo', 'pdo_mysql', 'gd', 'mbstring'];
foreach($extensions as $ext) {
    $status = extension_loaded($ext) ? '✅' : '❌';
    echo "$status $ext<br>";
}

phpinfo();
?>
```

---

## 🚨 Solución de Problemas Comunes

### Error: "Cannot connect to database"
**Solución:**
```bash
# Verificar que MySQL esté corriendo
sudo systemctl status mysql

# Iniciar MySQL
sudo systemctl start mysql

# Verificar credenciales en config/database.php
```

### Error: "Permission denied" al subir imágenes
**Solución:**
```bash
# Dar permisos de escritura
sudo chmod -R 775 uploads/
sudo chown -R www-data:www-data uploads/
```

### Error: "Class not found"
**Solución:**
```bash
# Regenerar autoload de Composer
composer dump-autoload
```

### Las fuentes no se cargan
**Solución:**
- Verificar conexión a internet
- Comprobar que el CDN de Google Fonts esté accesible
- Considerar descargar fuentes localmente

---

[← Anterior: Tecnologías](tecnologias.md) | [→ Siguiente: Despliegue](despliegue.md)
