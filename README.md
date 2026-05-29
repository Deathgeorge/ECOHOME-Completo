Backend

# EcoHome API

Backend API para la aplicación EcoHome, construida con Java y Spring Boot. Proporciona funcionalidades de autenticación y gestión de usuarios.

## ✨ Características

-   Registro de usuarios con hash de contraseñas (BCrypt).
-   Login de usuarios y autenticación.
-   Autenticación stateless usando JSON Web Tokens (JWT).
-   Endpoints seguros utilizando Spring Security.
-   Gestión de productos (CRUD completo) con control de acceso basado en roles.
-   Chat en tiempo real mediante WebSockets (Socket.IO).

## 🛠️ Tecnologías Utilizadas

-   Java 17+
-   Spring Boot 3
-   Spring Security
-   Maven
-   Lombok
-   Auth0 JWT
-   jBCrypt
-   Netty SocketIO (WebSockets)

## 📋 Prerrequisitos

Antes de comenzar, asegúrate de tener instalado lo siguiente:
-   JDK 17 o superior.
-   Maven 3.6 o superior.
-   Una instancia de base de datos relacional en ejecución (ej. PostgreSQL, MySQL).

## 🚀 Cómo Empezar

Sigue estos pasos para tener una copia del proyecto funcionando en tu máquina local.

### 1. Clonar el Repositorio

```bash
git clone <URL-DEL-REPOSITORIO>
cd <NOMBRE-DEL-PROYECTO>
```

### 2. Configuración

Crea un archivo `application.properties` en el directorio `src/main/resources/` y añade la siguiente configuración. **No olvides reemplazar los valores de ejemplo con tu configuración real.**

```properties
# Configuración de la Base de Datos (Ejemplo para PostgreSQL)
spring.datasource.url=jdbc:postgresql://localhost:5432/ecohome_db
spring.datasource.username=postgres
spring.datasource.password=tu_contraseña

# Configuración de JPA/Hibernate
spring.jpa.hibernate.ddl-auto=update
spring.jpa.show-sql=true

# Secreto para JWT
# Utiliza una clave secreta fuerte y segura. Puedes generar una aquí: https://www.allkeysgenerator.com/
jwt.secret=tu-clave-secreta-muy-larga-y-segura-para-firmar-tokens
```

### 3. Construir y Ejecutar

Puedes construir y ejecutar la aplicación usando Maven.

```bash
# Construir el proyecto
mvn clean install

# Ejecutar la aplicación
mvn spring-boot:run
```

La API estará disponible en `http://localhost:8080`.

## Endpoints de la API

### Autenticación

#### `POST /api/v1/auth/register`

Registra un nuevo usuario en el sistema.

**Request Body:**
```json
{
  "name": "John Doe",
  "documentNumber": "123456789",
  "email": "john.doe@example.com",
  "password": "yourpassword",
  "role": "USER"
}
```

**Success Response (200 OK):**
```json
{
  "message": "Registro exitoso"
}
```

---

#### `POST /api/v1/auth/login`

Autentica a un usuario y devuelve un token JWT si las credenciales son correctas.

**Request Body:**
```json
{
  "email": "john.doe@example.com",
  "password": "yourpassword"
}
```

**Success Response (200 OK):**
```json
{
    "message": "Login exitoso",
    "userId": 1,
    "name": "John Doe",
    "token": "ey..."
}
```

## 🔒 Seguridad

La API utiliza Spring Security para proteger los endpoints. Todas las rutas, excepto `/api/v1/auth/login` y `/api/v1/auth/register`, requieren un token JWT válido en el encabezado `Authorization`.

**Formato del encabezado:** `Authorization: Bearer <tu-token-jwt>`


Flutter

# EcoHome App

Aplicación móvil desarrollada en Flutter para la gestión de productos y comunicación en tiempo real.

## Características Principales

* **Gestión de Productos**: 
  * Listado de productos detallando nombre, precio, stock y el usuario creador.
  * Formulario para la creación de nuevos productos.
* **Chat Global**: 
  * Sala de chat en tiempo real utilizando `Socket.IO`.
  * Recuperación automática del historial de los últimos mensajes.
* **Navegación Intuitiva**: Menú inferior (BottomNavigationBar) para cambiar fácilmente entre el listado, la creación de productos y el chat.

## Requisitos del Backend (Entorno de Desarrollo)

La aplicación está configurada para conectarse a un backend local (usando `10.0.2.2` en emuladores de Android y `localhost` en web/iOS):
* **API REST**: Se espera que corra en el puerto `8080` (Maneja endpoints como `/api/v1/products` y `/api/v1/chats/latest`).
* **WebSockets**: Servidor de Socket.IO corriendo en el puerto `8095`.

## Getting Started

This project is a starting point for a Flutter application.

A few resources to get you started if this is your first Flutter project:

- [Learn Flutter](https://docs.flutter.dev/get-started/learn-flutter)
- [Write your first Flutter app](https://docs.flutter.dev/get-started/codelab)
- [Flutter learning resources](https://docs.flutter.dev/reference/learning-resources)

For help getting started with Flutter development, view the
[online documentation](https://docs.flutter.dev/), which offers tutorials,
samples, guidance on mobile development, and a full API reference.



# EcoHome Frontend

Aplicación frontend para el proyecto EcoHome, construida con React, TypeScript y Vite.

## Características

*   **Autenticación**: Inicio de sesión de usuarios.
*   **Gestión de Productos**: Listado y creación de productos consumiendo una API REST.
*   **Chat en Tiempo Real**: Comunicación en tiempo real utilizando WebSockets (`socket.io-client`).

## Tecnologías Utilizadas

*   React (v19)
*   TypeScript
*   Vite
*   React Router DOM para el enrutamiento.
*   Socket.io-client para WebSockets.

## Requisitos Previos

Asegúrate de tener instalado Node.js (versión 18 o superior recomendada).

## Instalación y Ejecución

1.  Instala las dependencias:
    ```bash
    npm install
    ```
2.  Inicia el servidor de desarrollo:
    ```bash
    npm run dev
    ```
    La aplicación estará disponible en `http://localhost:5173` (o el puerto que indique Vite por consola).

## Estructura de Rutas
*   `/`: Página de inicio de sesión (`LoginForm`).
*   `/productos`: Listado de productos (`ListProductPage`).
*   `/crear-producto`: Formulario para crear un nuevo producto (`CreateProductoPage`).
*   `/chat`: Sala de chat en tiempo real (`ChatPage`).

