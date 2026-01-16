---
layout: default
title: Perfiles de Usuario
nav_order: 3
---

# Perfiles de Usuario

[← Volver al índice](index.md)

---

## 👥 Tipos de Usuarios

El sistema de **RecetasFáciles** contempla tres perfiles de usuario diferenciados, cada uno con funcionalidades y permisos específicos:

---

## 🌐 Visitante (No registrado)

Usuario que accede a la plataforma sin crear una cuenta.

### Permisos y Funcionalidades

✅ **Puede:**
- Explorar todas las recetas disponibles
- Utilizar la barra de búsqueda para encontrar recetas específicas
- Navegar por las diferentes categorías (Postres, Entradas, Desayunos, etc.)
- Visualizar el detalle completo de cualquier receta:
  - Ingredientes
  - Pasos de preparación
  - Tiempo estimado
  - Nivel de dificultad
  - Número de porciones
- Usar el banner carrusel para ver recetas destacadas

❌ **No puede:**
- Guardar recetas como favoritas
- Comentar o valorar recetas
- Subir sus propias recetas
- Crear listas personalizadas

### Caso de Uso Típico

> *María está buscando una receta de brownies para el cumpleaños de su hijo. Entra a RecetasFáciles desde su móvil, usa la barra de búsqueda para encontrar "brownie chocolate", visualiza varias opciones y sigue la receta paso a paso sin necesidad de registrarse.*

---

## 👤 Usuario Registrado

Usuario que ha creado una cuenta en la plataforma.

### Permisos y Funcionalidades

✅ **Puede:**
- Todas las funcionalidades del visitante, **más**:
- Guardar recetas como favoritas *(funcionalidad futura)*
- Comentar y valorar recetas *(funcionalidad futura)*
- Subir sus propias recetas con fotografías *(funcionalidad futura)*
- Gestionar su perfil personal
- Crear listas personalizadas de recetas (ej: "Menú semanal", "Postres para navidad")

❌ **No puede:**
- Eliminar recetas de otros usuarios
- Moderar comentarios
- Gestionar usuarios
- Modificar categorías del sistema

### Caso de Uso Típico

> *Pedro es un aficionado a la cocina que usa RecetasFáciles regularmente. Ha guardado 25 recetas como favoritas, creó una lista llamada "Comidas rápidas" para días ocupados, y recientemente subió su receta de paella valenciana que ha recibido 50 comentarios positivos.*

### Información del Perfil

El usuario registrado puede gestionar:
- **Datos personales**: Nombre, email, foto de perfil
- **Preferencias**: Tipo de cocina favorita, restricciones alimentarias
- **Actividad**: Recetas guardadas, recetas subidas, comentarios realizados

---

## 👨‍💼 Administrador

Usuario con privilegios completos de gestión del sistema.

### Permisos y Funcionalidades

✅ **Puede:**
- Acceso completo al sistema con funciones **CRUD** (Create, Read, Update, Delete)
- **Gestión de Recetas:**
  - Crear nuevas recetas
  - Editar cualquier receta existente
  - Eliminar recetas inapropiadas
  - Publicar/despublicar recetas
  - Destacar recetas en el banner carrusel
- **Gestión de Usuarios:**
  - Ver lista de usuarios registrados
  - Editar perfiles de usuario
  - Desactivar/activar cuentas
  - Asignar roles
- **Gestión de Categorías:**
  - Crear nuevas categorías
  - Editar categorías existentes
  - Eliminar categorías vacías
  - Reordenar categorías
- **Gestión de Contenido:**
  - Configurar imágenes del banner carrusel
  - Seleccionar recetas destacadas
  - Moderar comentarios
  - Eliminar contenido inapropiado

### Panel de Administración

El administrador accede a un panel especial con:
- Dashboard con estadísticas
- Gestión de base de datos
- Logs de actividad
- Reportes de usuarios

### Caso de Uso Típico

> *Ana es la administradora de RecetasFáciles. Cada semana revisa las nuevas recetas subidas por usuarios, modera comentarios reportados, actualiza el banner carrusel con recetas de temporada y responde consultas de usuarios sobre contenido.*

---

## 📊 Comparativa de Permisos

| Funcionalidad | Visitante | Usuario Registrado | Administrador |
|---------------|:---------:|:------------------:|:-------------:|
| Ver recetas | ✅ | ✅ | ✅ |
| Buscar recetas | ✅ | ✅ | ✅ |
| Ver detalle completo | ✅ | ✅ | ✅ |
| Guardar favoritos | ❌ | ✅ | ✅ |
| Comentar | ❌ | ✅ | ✅ |
| Subir recetas | ❌ | ✅ | ✅ |
| Crear listas personalizadas | ❌ | ✅ | ✅ |
| Editar cualquier receta | ❌ | ❌ | ✅ |
| Eliminar recetas | ❌ | ❌ | ✅ |
| Gestionar usuarios | ❌ | ❌ | ✅ |
| Moderar comentarios | ❌ | ❌ | ✅ |
| Gestionar categorías | ❌ | ❌ | ✅ |
| Configurar banner | ❌ | ❌ | ✅ |

---

## 🔐 Sistema de Autenticación *(Fase futura)*

### Registro de Usuarios
- Email y contraseña
- Confirmación por email
- Validación de datos

### Inicio de Sesión
- Email/contraseña
- Sesiones persistentes
- Recuperación de contraseña

### Seguridad
- Contraseñas hasheadas
- Tokens de sesión
- Protección CSRF

---

## 🎯 Flujo de Usuario

### Para Visitantes
```
Entrar al sitio → Explorar recetas → Buscar específica → Ver detalle → Cocinar
```

### Para Usuarios Registrados
```
Login → Explorar → Guardar favorita → Crear lista → Subir receta → Comentar
```

### Para Administradores
```
Login Admin → Panel → Moderar contenido → Gestionar usuarios → Actualizar destacados
```

---

[← Anterior: Introducción](introduccion.md) | [→ Siguiente: Arquitectura](arquitectura.md)
