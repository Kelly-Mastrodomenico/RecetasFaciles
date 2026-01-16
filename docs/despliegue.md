# Despliegue en Producción

[← Volver al índice](index.md)

---

## 🌐 Opciones de Hosting

Para el despliegue de **RecetasFáciles**, se han evaluado varias opciones de hosting según las necesidades del proyecto.

### Comparativa de Plataformas

| Plataforma | Tipo | Precio | Fase Soportada | Dificultad |
|------------|------|--------|----------------|------------|
| **GitHub Pages** | Estático | Gratis | Frontend | ⭐ Fácil |
| **Netlify** | Estático | Gratis | Frontend | ⭐ Fácil |
| **Vercel** | Estático | Gratis | Frontend | ⭐⭐ Media |
| **Hostinger** | Compartido | €2-5/mes | Full Stack | ⭐⭐⭐ Media |
| **InfinityFree** | Compartido | Gratis | Full Stack | ⭐⭐ Media |
| **Heroku** | PaaS | Gratis/€5+ | Full Stack | ⭐⭐⭐ Media-Alta |
| **DigitalOcean** | VPS | €5+/mes | Full Stack | ⭐⭐⭐⭐ Alta |
| **AWS / Azure** | Cloud | Variable | Full Stack | ⭐⭐⭐⭐⭐ Muy Alta |

---

## 📄 Fase 1: Despliegue Frontend

### Opción 1: GitHub Pages (Recomendado para inicio)

**Ventajas:**
- ✅ Totalmente gratuito
- ✅ Integración directa con GitHub
- ✅ SSL/HTTPS automático
- ✅ Ideal para prototipos

**Limitaciones:**
- ❌ Solo archivos estáticos (HTML, CSS, JS)
- ❌ No soporta backend (PHP, MySQL)

#### Pasos de Despliegue

1. **Preparar el repositorio:**
```bash
# Asegúrate de estar en la rama main
git checkout main

# Commit de todos los cambios
git add .
git commit -m "Preparar para despliegue en GitHub Pages"
git push origin main
```

2. **Configurar GitHub Pages:**
- Ve a tu repositorio en GitHub
- Settings → Pages
- Source: **Deploy from a branch**
- Branch: **main** / Folder: **/ (root)**
- Click en **Save**

3. **Esperar el despliegue:**
- GitHub comenzará a construir tu sitio
- En 1-2 minutos estará disponible
- URL: `https://tu-usuario.github.io/RecetasFaciles/`

4. **Verificar:**
```bash
# Visitar la URL generada
open https://tu-usuario.github.io/RecetasFaciles/
```

#### Configuración de Dominio Personalizado (Opcional)

1. **Comprar dominio** (ej: recetasfaciles.com en Namecheap, GoDaddy)

2. **Configurar DNS:**
```
Type: CNAME
Host: www
Value: tu-usuario.github.io
```

3. **En GitHub Pages:**
- Settings → Pages → Custom domain
- Introducir: `www.recetasfaciles.com`
- Marcar **Enforce HTTPS**

---

### Opción 2: Netlify

**Ventajas:**
- ✅ Deploy automático desde Git
- ✅ SSL gratis
- ✅ CDN global
- ✅ Formularios serverless

#### Pasos de Despliegue

1. **Crear cuenta en [Netlify](https://www.netlify.com)**

2. **Nuevo sitio desde Git:**
- Click en **"New site from Git"**
- Conectar con GitHub
- Seleccionar repositorio `RecetasFaciles`

3. **Configuración de build:**
```yaml
# Netlify generalmente no necesita configuración para HTML estático
# Pero puedes crear netlify.toml

[build]
  publish = "."
  command = "echo 'No build needed'"

[[redirects]]
  from = "/*"
  to = "/index.html"
  status = 200
```

4. **Deploy:**
- Click en **"Deploy site"**
- Netlify asignará una URL: `https://random-name.netlify.app`

5. **Dominio personalizado:**
- Site settings → Domain management
- Add custom domain

---

### Opción 3: Vercel

Similar a Netlify, ideal para proyectos modernos.

```bash
# Instalar Vercel CLI
npm install -g vercel

# Deploy desde terminal
cd RecetasFaciles
vercel

# Seguir instrucciones interactivas
```

---

## 🔧 Fase 2: Despliegue Full Stack (PHP + MySQL)

### Opción 1: Hostinger (Recomendado para producción)

**Características:**
- ✅ PHP 8.1+
- ✅ MySQL 8.0
- ✅ Panel cPanel
- ✅ SSL gratuito (Let's Encrypt)
- ✅ Soporte técnico 24/7
- 💰 Desde €2.99/mes

#### Pasos de Despliegue

1. **Contratar hosting:**
- Visitar [Hostinger.es](https://www.hostinger.es)
- Elegir plan **Premium** o **Business**
- Configurar dominio (ej: recetasfaciles.com)

2. **Acceder a cPanel:**
- Login en panel.hostinger.com
- Acceder a cPanel

3. **Crear base de datos:**
- MySQL Databases → Create New Database
- Nombre: `u123456_recetas`
- Crear usuario y contraseña
- Asignar usuario a la base de datos (ALL PRIVILEGES)

4. **Subir archivos:**

**Método A - FileZilla (FTP):**
```
Host: ftp.recetasfaciles.com
Username: tu-usuario
Password: tu-contraseña
Port: 21

# Subir archivos a /public_html
```

**Método B - cPanel File Manager:**
- File Manager → public_html
- Upload → Seleccionar todos los archivos
- Extract (si subiste un .zip)

5. **Configurar base de datos:**
- phpMyAdmin → Importar
- Seleccionar `schema.sql`
- Click en **Go**

6. **Actualizar config/database.php:**
```php
<?php
define('DB_HOST', 'localhost'); // o mysql.hostinger.com
define('DB_NAME', 'u123456_recetas');
define('DB_USER', 'u123456_admin');
define('DB_PASS', 'tu_contraseña_segura');
?>
```

7. **Configurar SSL:**
- cPanel → SSL/TLS Status
- Run AutoSSL (automático con Let's Encrypt)
- Forzar HTTPS en .htaccess:

```apache
# .htaccess
RewriteEngine On
RewriteCond %{HTTPS} off
RewriteRule ^(.*)$ https://%{HTTP_HOST}%{REQUEST_URI} [L,R=301]
```

8. **Verificar funcionamiento:**
- Visitar: `https://recetasfaciles.com`
- Probar todas las funcionalidades

---

### Opción 2: InfinityFree (Hosting Gratuito)

**Para pruebas y desarrollo:**

**Características:**
- ✅ Gratis
- ✅ PHP 8.0
- ✅ MySQL
- ❌ Sin soporte
- ❌ Limitaciones de tráfico

**URL:** [infinityfree.net](https://infinityfree.net)

#### Pasos:
1. Crear cuenta gratuita
2. Crear sitio (subdominio .rf.gd gratis)
3. Subir archivos vía FTP o File Manager
4. Configurar MySQL desde el panel

---

### Opción 3: Heroku (PaaS)

**Para aplicaciones escalables:**

#### Requisitos:
```bash
# Instalar Heroku CLI
curl https://cli-assets.heroku.com/install.sh | sh

# Login
heroku login
```

#### Preparar proyecto:

1. **Crear Procfile:**
```
web: vendor/bin/heroku-php-apache2 public/
```

2. **Crear composer.json:**
```json
{
  "require": {
    "php": "^8.1"
  }
}
```

3. **Deploy:**
```bash
# Crear app
heroku create recetasfaciles

# Agregar MySQL (ClearDB addon)
heroku addons:create cleardb:ignite

# Obtener credenciales
heroku config:get CLEARDB_DATABASE_URL

# Push a Heroku
git push heroku main

# Abrir app
heroku open
```

---

## 🐳 Despliegue con Docker

### En VPS (DigitalOcean, Linode, AWS EC2)

1. **Crear Droplet/Instancia:**
- Ubuntu 22.04 LTS
- 2GB RAM mínimo
- Configurar SSH

2. **Conectar vía SSH:**
```bash
ssh root@tu-ip-servidor
```

3. **Instalar Docker:**
```bash
# Actualizar sistema
apt update && apt upgrade -y

# Instalar Docker
curl -fsSL https://get.docker.com -o get-docker.sh
sh get-docker.sh

# Instalar Docker Compose
apt install docker-compose -y
```

4. **Clonar proyecto:**
```bash
git clone https://github.com/tu-usuario/RecetasFaciles.git
cd RecetasFaciles
```

5. **Configurar variables de entorno:**
```bash
cp .env.example .env
nano .env

# Editar credenciales de producción
```

6. **Levantar contenedores:**
```bash
docker-compose up -d --build
```

7. **Configurar Nginx como proxy inverso:**
```nginx
# /etc/nginx/sites-available/recetasfaciles.com

server {
    listen 80;
    server_name recetasfaciles.com www.recetasfaciles.com;

    location / {
        proxy_pass http://localhost:8080;
        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
    }
}
```

8. **Habilitar sitio:**
```bash
ln -s /etc/nginx/sites-available/recetasfaciles.com /etc/nginx/sites-enabled/
nginx -t
systemctl reload nginx
```

9. **Configurar SSL con Certbot:**
```bash
apt install certbot python3-certbot-nginx -y
certbot --nginx -d recetasfaciles.com -d www.recetasfaciles.com
```

---

## 🔒 Seguridad en Producción

### Checklist de Seguridad

- [ ] **Cambiar credenciales por defecto**
  ```php
  // NO usar en producción
  DB_USER = 'root'
  DB_PASS = ''
  ```

- [ ] **Deshabilitar errores PHP visibles**
  ```php
  ini_set('display_errors', 0);
  error_reporting(0);
  ```

- [ ] **Validar y sanitizar inputs**
  ```php
  $titulo = filter_var($_POST['titulo'], FILTER_SANITIZE_STRING);
  ```

- [ ] **Usar prepared statements**
  ```php
  $stmt = $pdo->prepare("SELECT * FROM recetas WHERE id = ?");
  $stmt->execute([$id]);
  ```

- [ ] **Implementar HTTPS**
  - Forzar redirección HTTP → HTTPS
  - Usar certificados SSL válidos

- [ ] **Configurar headers de seguridad**
  ```php
  header("X-Content-Type-Options: nosniff");
  header("X-Frame-Options: DENY");
  header("X-XSS-Protection: 1; mode=block");
  ```

- [ ] **Proteger directorios sensibles**
  ```apache
  # .htaccess en /config/
  Deny from all
  ```

- [ ] **Hacer backups regulares**
  ```bash
  # Backup de base de datos
  mysqldump -u user -p recetasfaciles > backup_$(date +%Y%m%d).sql
  ```

---

## 📊 Optimización de Rendimiento

### Imágenes

```bash
# Comprimir imágenes antes de subir
# Usar TinyPNG, ImageOptim, etc.

# Convertir a WebP (mejor compresión)
cwebp brownie.jpg -o brownie.webp
```

### CSS y JavaScript

```html
<!-- Minificar archivos -->
<link rel="stylesheet" href="css/styles.min.css">
<script src="js/main.min.js"></script>

<!-- Usar CDN para librerías -->
<script src="https://cdn.jsdelivr.net/npm/jquery@3.6.0/dist/jquery.min.js"></script>
```

### Cache del Navegador

```apache
# .htaccess - Configurar cache
<IfModule mod_expires.c>
  ExpiresActive On
  ExpiresByType image/jpg "access plus 1 year"
  ExpiresByType image/jpeg "access plus 1 year"
  ExpiresByType image/png "access plus 1 year"
  ExpiresByType text/css "access plus 1 month"
  ExpiresByType text/javascript "access plus 1 month"
</IfModule>
```

### Lazy Loading

```html
<!-- Cargar imágenes bajo demanda -->
<img src="receta.jpg" loading="lazy" alt="Receta">
```

---

## 📈 Monitoreo y Analíticas

### Google Analytics

```html
<!-- En el <head> -->
<script async src="https://www.googletagmanager.com/gtag/js?id=G-XXXXXXXXXX"></script>
<script>
  window.dataLayer = window.dataLayer || [];
  function gtag(){dataLayer.push(arguments);}
  gtag('js', new Date());
  gtag('config', 'G-XXXXXXXXXX');
</script>
```

### Logs de Errores

```php
// config.php
ini_set('log_errors', 1);
ini_set('error_log', '/ruta/logs/php-error.log');
```

---

## ✅ Verificación Post-Despliegue

### Checklist

- [ ] El sitio carga correctamente en la URL de producción
- [ ] HTTPS funciona y es forzado
- [ ] Base de datos conecta correctamente
- [ ] Todas las imágenes se cargan
- [ ] Formularios funcionan
- [ ] Búsqueda y filtros operativos
- [ ] Diseño responsive en todos los dispositivos
- [ ] No hay errores en consola del navegador
- [ ] Rendimiento aceptable (PageSpeed Insights > 80)
- [ ] SEO básico configurado (meta tags, sitemap.xml)

---

[← Anterior: Instalación](instalacion.md) | [→ Siguiente: Conclusiones](conclusiones.md)
