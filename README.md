# PFO 2: Sistema de Gestión de Tareas con API y Base de Datos

Este proyecto implementa un sistema básico de gestión de tareas con una API REST en Flask y persistencia de datos con SQLite. Incluye registro de usuarios, inicio de sesión con JWT y un endpoint de prueba para tareas.

## Características

* **API REST con Flask:** Endpoints para registro, login y gestión de tareas.
* **Autenticación de Usuarios:** Registro de usuarios con contraseñas hasheadas y login con JSON Web Tokens (JWT).
* **Persistencia de Datos:** Utiliza SQLite para almacenar los usuarios.
* **Cliente en Consola:** Una aplicación Python para interactuar con la API.

## Endpoints de la API

* **`POST /registro`**
    * **Descripción:** Registra un nuevo usuario en el sistema.
    * **Request Body (JSON):**
        ```json
        {
            "usuario": "nombre_de_usuario",
            "contraseña": "contraseña_segura"
        }
        ```
    * **Respuestas:**
        * `201 Created`: `{"mensaje": "Usuario <nombre> registrado con éxito"}`
        * `400 Bad Request`: `{"mensaje": "Faltan usuario o contraseña"}`
        * `409 Conflict`: `{"mensaje": "El usuario ya existe"}`

    * **`POST /login`**
    * **Descripción:** Autentica a un usuario y devuelve un token JWT.
    * **Request Body (JSON):**
        ```json
        {
            "usuario": "nombre_de_usuario",
            "contraseña": "contraseña_del_usuario"
        }
        ```
    * **Respuestas:**
        * `200 OK`: `{"access_token": "..."}`
        * `400 Bad Request`: `{"mensaje": "Faltan usuario o contraseña"}`
        * `401 Unauthorized`: `{"mensaje": "Credenciales inválidas"}`
    
    * **`GET /tareas`**
    * **Descripción:** Muestra un HTML de bienvenida. Requiere autenticación JWT.
    * **Headers:** `Authorization: Bearer <access_token>`
    * **Respuestas:**
        * `200 OK`: Contenido HTML de la página de bienvenida.
        * `401 Unauthorized`: Si el token no es válido o está ausente.

 