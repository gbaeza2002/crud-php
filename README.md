# API CRUD de Clientes con Laravel

API RESTful para gestionar clientes utilizando Laravel siguiendo el patrón MVC.

## Estructura del Proyecto

Este proyecto sigue la arquitectura MVC (Model-View-Controller) de Laravel:

- **Model**: `app/Models/Cliente.php` - Define el modelo de datos
- **View**: `app/Http/Resources/ClienteResource.php` - Formatea las respuestas JSON
- **Controller**: `app/Http/Controllers/ClienteController.php` - Maneja la lógica de negocio

## Endpoints de la API

### Base URL
```
/api/clientes
```

### Endpoints disponibles

1. **GET /api/clientes** - Obtener todos los clientes
2. **GET /api/clientes/{id}** - Obtener un cliente específico
3. **POST /api/clientes** - Crear un nuevo cliente
4. **PUT /api/clientes/{id}** - Actualizar un cliente
5. **DELETE /api/clientes/{id}** - Eliminar un cliente

## Ejemplos de uso

### Crear un cliente (POST)
```json
{
    "nombre": "Juan Pérez",
    "email": "juan@example.com",
    "telefono": "+56912345678",
    "direccion": "Av. Principal 123",
    "ciudad": "Santiago",
    "pais": "Chile"
}
```

### Actualizar un cliente (PUT)
```json
{
    "nombre": "Juan Pérez",
    "email": "juan.nuevo@example.com",
    "telefono": "+56987654321",
    "direccion": "Av. Nueva 456",
    "ciudad": "Valparaíso",
    "pais": "Chile"
}
```

## Respuestas de la API

### Éxito
```json
{
    "success": true,
    "data": {
        "id": 1,
        "nombre": "Juan Pérez",
        "email": "juan@example.com",
        "telefono": "+56912345678",
        "direccion": "Av. Principal 123",
        "ciudad": "Santiago",
        "pais": "Chile",
        "created_at": "2024-01-01 12:00:00",
        "updated_at": "2024-01-01 12:00:00"
    },
    "message": "Cliente creado exitosamente"
}
```

### Error
```json
{
    "success": false,
    "message": "Error de validación",
    "errors": {
        "email": ["El email ya ha sido registrado."]
    }
}
```

## Instalación

1. Instalar dependencias:
```bash
composer install
```

2. Configurar el archivo `.env` con tus credenciales de base de datos

3. Ejecutar las migraciones:
```bash
php artisan migrate
```

4. Iniciar el servidor:
```bash
php artisan serve
```

## Validaciones

- **nombre**: Requerido, string, máximo 255 caracteres
- **email**: Requerido, email válido, único en la tabla, máximo 255 caracteres
- **telefono**: Opcional, string, máximo 20 caracteres
- **direccion**: Opcional, string
- **ciudad**: Opcional, string, máximo 100 caracteres
- **pais**: Opcional, string, máximo 100 caracteres

