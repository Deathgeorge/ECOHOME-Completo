EcoHome Store
Descripción del proyecto
EcoHome Store es una plataforma fullstack desarrollada como solución integrada para gestión de productos y soporte en tiempo real.

El proyecto incluye:

Backend RESTful con Spring Boot
Frontend web con React
Aplicación móvil con Flutter
PostgreSQL como base de datos
Autenticación JWT
Chat en tiempo real con Socket.IO/WebSocket
Estructura del proyecto
ecohome-store/
│
├── backend/
├── web-react/
├── mobile-flutter/
├── db/
└── README.md
Tecnologías utilizadas
Backend
Java 17
Spring Boot
Spring Security
JWT
PostgreSQL
WebSocket / Socket.IO
Frontend Web
React
Axios
Socket.IO Client
Aplicación móvil
Flutter
Dart
HTTP
Socket.IO Client
Base de datos
PostgreSQL
Pasos de instalación
1. Clonar el repositorio
git clone https://github.com/danelappsmart-danel/ecohome-store-final-danel
2. Crear base de datos PostgreSQL
Crear una base de datos llamada:

CREATE DATABASE ecohome_store;
3. Ejecutar scripts SQL
Ingresar a la carpeta /db y ejecutar:

Crear estructura
psql -U postgres -d ecohome_store -f schema.sql
Insertar datos de prueba
psql -U postgres -d ecohome_store -f data.sql
Variables de entorno
Backend
Configurar en:

backend/src/main/resources/application.properties
Variables principales:

spring.datasource.url=jdbc:postgresql://localhost:5432/ecohome_store
spring.datasource.username=postgres
spring.datasource.password=postgres

jwt.secret=ecohome-secret-key
jwt.expiration=86400000
Frontend React
Configurar en:

web-react/.env
Variables:

REACT_APP_API_URL=http://localhost:8080
REACT_APP_SOCKET_URL=http://localhost:8080
Flutter
Configurar URL base en:

mobile-flutter/lib/config/constants.dart
Ejemplo:

const BASE_URL = "http://10.0.2.2:8080";
const SOCKET_URL = "http://10.0.2.2:8080";
Cómo ejecutar el backend
Ingresar a la carpeta:

cd backend
Ejecutar:

mvn spring-boot:run
El backend quedará disponible en:

http://localhost:8080
Cómo ejecutar React
Ingresar a la carpeta:

cd web-react
Instalar dependencias:

npm install
Ejecutar aplicación:

npm start
La aplicación quedará disponible en:

http://localhost:3000
Cómo ejecutar Flutter
Ingresar a la carpeta:

cd mobile-flutter
Instalar dependencias:

flutter pub get
Ejecutar aplicación:

flutter run
Para ejecutar en Chrome:

flutter run -d chrome
Credenciales de prueba
Usuario administrador
Correo: Guillermo@pulecio.com
Password: 123456
Rol: ADMIN
Usuario cliente
Correo: danel@pulecio.com
Password: 123456
Rol: CLIENT
Endpoints principales
Autenticación
POST /auth/signup
POST /auth/login
Productos
GET /products
POST /products
PUT /products/{id}
DELETE /products/{id}
Métricas usuario
GET /users/me/stats
Eventos Socket.IO / WebSocket
Eventos implementados
Conexión
connect
disconnect
Historial de mensajes
messages
Evento utilizado para enviar los últimos 10 mensajes almacenados.

Nuevos mensajes
message
Evento utilizado para:

enviar mensajes
recibir mensajes en tiempo real
broadcast entre clientes conectados
Funcionalidades implementadas
Backend
JWT Authentication
CRUD de productos
Persistencia PostgreSQL
Chat en tiempo real
Trazabilidad por usuario
Contador dinámico de productos
React
Login JWT
Catálogo de productos
Chat tiempo real
Indicador Usuario (N)
Flutter
Login JWT
Catálogo móvil
Chat tiempo real
Indicador Usuario (N)
Persistencia
Toda la información es persistida en PostgreSQL:

Usuarios
Productos
Mensajes del chat
La información permanece disponible después de reiniciar backend, frontend o aplicación móvil.

Seguridad
El proyecto implementa:

JWT para autenticación
Rutas protegidas
Contraseñas cifradas/hash
Validación de acceso mediante token