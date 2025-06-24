# PFO 2: Sistema de Gestión de Tareas con API y Base de Datos

Este proyecto implementa un sistema básico de gestión de tareas con una API REST en Flask y persistencia de datos con SQLite. Incluye registro de usuarios, inicio de sesión con JWT y un endpoint de prueba para tareas.

## Características

* **API REST con Flask:** Endpoints para registro, login y gestión de tareas.
* **Autenticación de Usuarios:** Registro de usuarios con contraseñas hasheadas y login con JSON Web Tokens (JWT).
* **Persistencia de Datos:** Utiliza SQLite para almacenar los usuarios.
* **Cliente en Consola:** Una aplicación Python para interactuar con la API.

## Instalación y Ejecución

Instrucciones para ejecutar el proyecto:

1.  **Clonar el repositorio:**
    ```bash
    git clone https://github.com/Gaby46Pe/PR-PFO2-GAP-B.git
    cd pfo2-tareas
    ```

2.  **Crear y activar un entorno virtual:**
    ```bash
    python -m venv venv
    # En Windows:
    .\venv\Scripts\activate
    # En Linux/macOS:
    source venv/bin/activate
    ```

3.  **Instalar dependencias:**
    ```bash
    pip install -r requirements.txt
    ```
    (Si no tiene `requirements.txt`, ejecutar `pip install Flask Flask-SQLAlchemy Werkzeug Flask-JWT-Extended requests` y luego `pip freeze > requirements.txt`).

4.  **Ejecutar el Servidor Flask:**
    Abrir una terminal, activar el entorno virtual (si no lo hiciste) y ejecutar:
    ```bash
    python servidor.py
    ```
    El servidor se iniciará en `http://127.0.0.1:5000`. Verás un archivo `tareas.db` aparecer en el directorio del proyecto.

5.  **Ejecutar el Cliente en Consola:**
Abre **otra terminal diferente**, activa el entorno virtual y ejecuta:
    ```bash
    python cliente.py
    ```
    Sigue el menú para registrar un usuario, iniciar sesión y acceder a las tareas.


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

## Capturas de pantalla de pruebas exitosas
  ![Postman Login ok]screenshots/postman login ok pr pfo2.jpg
