
# Explicación de cada carpeta

## `index.php`
Punto de entrada de la API.
Aquí llegan todas las requests.

---

## `nexventa/controllers/`
Controladores.
Reciben requests y devuelven respuestas.

Ejemplo:

```txt id="w17f7s"
UserController.php
AuthController.php
```

```php id="a5ns59"
class UserController {

    public function index() {

        echo json_encode([
            "users" => []
        ]);
    }
}
```

---

## `nexventa/models/`

Acceso a base de datos.

Ejemplo:

```txt id="ewr24n"
User.php
Product.php
```

```php id="b5ktum"
class User {

    public static function all() {

        // query SQL
    }
}
```

---

## `nexventa/middleware/`

Middlewares.

Ejemplo:

```txt id="yukij1"
AuthMiddleware.php
CorsMiddleware.php
```

---

## `nexventa/services/`

Lógica de negocio.

Muy útil para no saturar controladores.

Ejemplo:

```txt id="5xiwq5"
AuthService.php
EmailService.php
PaymentService.php
```

---

## `nexventa/routes/`

Definición de rutas.

Ejemplo:

```txt id="5v0d0h"
api.php
```

```php id="0h3xsi"
Router::get('/users', [UserController::class, 'index']);
```

---

## `nexventa/helpers/`

Funciones reutilizables.

Ejemplo:

```txt id="db1w6l"
response.php
jwt.php
validator.php
```

---

## `nexventa/config/`

Configuraciones.

Ejemplo:

```txt id="m1s5tw"
database.php
app.php
cors.php
```

---

## `nexventa/core/`

Núcleo de la mini arquitectura.

Aquí normalmente van:

```txt id="b3hujx"
Router.php
Request.php
Response.php
Database.php
Controller.php
Middleware.php
```

---

## `storage/`

Archivos generados.

### uploads

```txt id="9lfjz5"
storage/uploads/
```

### logs

```txt id="k7wm5r"
storage/logs/
```

---

# `vendor/`

Dependencias de Composer.

No se edita manualmente.

---

# `.env`

Variables de entorno.

```env id="h3v9ux"
DB_HOST=localhost
DB_NAME=mi_api
DB_USER=root
DB_PASS=1234

JWT_SECRET=abc123
```

---

# Arquitectura recomendada

## Flujo

```txt id="k8b8nk"
Request
   ↓
public/index.php
   ↓
Router
   ↓
Middleware
   ↓
Controller
   ↓
Service
   ↓
Model
   ↓
Response JSON
```

---

# Ejemplo real pequeño

```txt id="9zh4eq"
nexventa/
├── controllers/
│   └── UserController.php
│
├── models/
│   └── User.php
│
├── middleware/
│   └── AuthMiddleware.php
│
├── routes/
│   └── api.php
│
└── core/
    └── Router.php
```