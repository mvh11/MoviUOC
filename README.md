# MoviUOC – Aplicación Móvil de Movilidad Segura para Estudiantes DUOC UC

MoviUOC es una aplicación móvil desarrollada en **Android Studio (Kotlin + Jetpack Compose)** para mejorar la movilidad y seguridad de los estudiantes DUOC UC, permitiéndoles crear y buscar viajes, compartir transporte y registrar perfiles como conductor o pasajero. El proyecto incluye **tres microservicios Spring Boot**, validaciones, cámara, persistencia local y testing.

---

## 1. Nombre del Proyecto
**MoviUOC – Sistema de Movilidad Segura DUOC UC**

---

## 2. Integrantes
- **Maximiliano Venegas** 
- **Elias Lobos**

---

## 3. Funcionalidades de la Aplicación

### ✔ Interfaz y Navegación (Jetpack Compose)
- Splash Screen animado.
- Pantallas 100% Compose (sin XML).
- Home con navegación hacia crear viaje, buscar viaje y perfil.
- Animaciones integradas.

### ✔ Autenticación y Usuario
- Login con validación estricta de correos `@duocuc.cl`.
- Registro con validación de contraseña segura.
- Roles: **Pasajero** y **Conductor**.
- Gestión de sesión con `SessionManager` (SharedPreferences).

### ✔ Perfil
- Captura de foto con cámara usando `takePictureLauncher`.
- Foto guardada como imagen de perfil.

### ✔ Viajes
- Crear viaje (CRUD).
- Buscar viajes disponibles.
- Persistencia local con Room.
- Consumo de microservicio viajes vía Retrofit + Coroutines.

### ✔ Networking / API
- Consumo de 3 microservicios:
  - usuarios-service (8080)
  - conductores-service (8081)
  - viajes-service (8082)

### ✔ Testing
- Unit tests con JUnit4.
- Tests con MockK.

### ✔ APK Firmado
- Archivo `.jks` generado.
- APK *release* compilado.

---

## 4. Endpoints Utilizados (APIs y Microservicios)

### Usuarios Service (8080)
GET /usuarios
POST /usuarios
GET /usuarios/{id}
PUT /usuarios/{id}
DELETE /usuarios/{id}
GET /usuarios/login?email={email}&password={password}

### Conductores Service (8081)
GET /conductores
POST /conductores

### Viajes Service (8082)
GET /viajes
POST /viajes

---

## 5. Pasos para Ejecutar el Proyecto

### A) Requisitos
- Android Studio Ladybug/Koala
- JDK 17
- Maven 3.9+
- Emulador Android o dispositivo físico

---

### B) Ejecutar Microservicios
Clonar el repo:
git clone https://github.com/tuusuario/MoviUOC.git

usuarios-service:
cd usuarios-service
mvn spring-boot:run

Conductores-service:
cd conductores-service
mvn spring-boot:run

Viajes-service:
cd viajes-service
mvn spring-boot:run

Verificación:
- http://localhost:8080/usuarios
- http://localhost:8081/conductores
- http://localhost:8082/viajes

Consola H2:
- http://localhost:8080/h2-console
- http://localhost:8081/h2-console
- http://localhost:8082/h2-console

---

### C) Ejecutar la App Android

1. Abrir Android Studio.
2. Importar carpeta `/MoviUOC/app`.
3. Run ▶ en emulador o dispositivo.

---

### D) Generar el APK Firmado

Android Studio →  
**Build → Generate Signed Bundle / APK…**

- Tipo: APK
- Crear keystore `.jks`
- Generar archivo release

