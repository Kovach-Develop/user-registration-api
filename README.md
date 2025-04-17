# User Registration API

API RESTful para el registro de usuarios usando Java 17, Spring Boot, JWT y base de datos en memoria H2.

---

## 🧰 Tecnologías utilizadas

- Java 17
- Spring Boot
- Spring Data JPA
- H2 Database
- JWT (Json Web Token)
- Maven
- Swagger (opcional)

---

## 🚀 Cómo ejecutar el proyecto

### 1. Clona el repositorio o descomprime el ZIP

```bash
git clone https://github.com/tu-usuario/user-registration-api.git
cd user-registration-api
```

O simplemente descomprime el archivo `user-registration-api.zip`.

---

### 2. Ejecuta el proyecto con Maven

```bash
./mvnw spring-boot:run
```

O si estás en Windows:

```bash
mvnw.cmd spring-boot:run
```

También puedes usar tu IDE favorito (IntelliJ, VSCode, etc.) para correr la clase `DemoApplication.java`.

---

### 3. Accede a la consola H2 (opcional)

- URL: `http://localhost:8080/h2-console`
- JDBC URL: `jdbc:h2:mem:testdb`
- Usuario: `sa`
- Contraseña: *(dejar en blanco)*

---

### 4. Prueba la API con Swagger

- URL: `http://localhost:8080/swagger-ui/index.html` *(si habilitado)*

---

## 📬 Endpoint disponible

### POST `/api/users/register`

#### 📝 Request Body (JSON)
```json
{
  "name": "Juan Rodriguez",
  "email": "juan@rodriguez.org",
  "password": "hunter2",
  "phones": [
    {
      "number": "1234567",
      "citycode": "1",
      "contrycode": "57"
    }
  ]
}
```

#### ✅ Response exitoso
```json
{
  "id": "uuid-generado",
  "created": "2025-04-16T12:00:00",
  "modified": "2025-04-16T12:00:00",
  "lastLogin": "2025-04-16T12:00:00",
  "token": "jwt-generado",
  "isActive": true
}
```

#### ❌ Ejemplo de error (correo duplicado)
```json
{
  "mensaje": "El correo ya registrado"
}
```

---

## 🔐 Validaciones

- **Email**: Debe tener un formato válido (ej. `usuario@dominio.com`).
- **Password**: Validación configurable con expresión regular.
- **Correo único**: No puede registrarse más de una vez.

---

## 🧱 Diagrama de la solución

```
[ Controller ] --> [ Service ] --> [ Repository ] --> [ H2 DB ]
        |              |                |
     UserDTO     Validaciones         JPA
        |
     JWT generado y persistido
```

---

## ✅ Ejemplo con CURL

```bash
curl -X POST http://localhost:8080/api/users/register \
-H "Content-Type: application/json" \
-d '{
  "name": "Juan Rodriguez",
  "email": "juan@rodriguez.org",
  "password": "hunter2",
  "phones": [
    {
      "number": "1234567",
      "citycode": "1",
      "contrycode": "57"
    }
  ]
}'
```

---

## 📌 Notas finales

- El proyecto usa una base en memoria, por lo tanto los datos se pierden al reiniciar.
- Puedes cambiar las configuraciones en `application.properties`.
- Incluye `pom.xml` ya configurado para dependencias y plugins.

---

¡Listo para tu prueba técnica! 🚀
