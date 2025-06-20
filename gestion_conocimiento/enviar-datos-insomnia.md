Para enviar datos correctamente desde **Insomnia** a tu endpoint de NestJS:

### 1. **Tipo de petición**

* Método: `POST`
* URL: `http://localhost:3000/signup` (ajusta el host y puerto si es distinto)

---

### 2. **Configurar el Body**

1. En Insomnia, ve a la pestaña **Body**
2. Selecciona el tipo **JSON**
3. Escribe el contenido que esperas en `CreateUserDto`. Por ejemplo, si `CreateUserDto` es algo como:

```ts
export class CreateUserDto {
  email: string;
  password: string;
}
```

Entonces, el cuerpo en Insomnia sería:

```json
{
  "email": "test@example.com",
  "password": "superSecret123"
}
```

---

### 3. **Encabezados**

Insomnia debería ponerlo automáticamente, pero si no, ve a la pestaña **Headers** y asegúrate de tener:

```http
Content-Type: application/json
```

---

### 4. **Ejecutar**

Pulsa el botón "Send" y deberías recibir la respuesta de tu backend.

---

### ¿Errores comunes?

* **400 Bad Request**: Asegúrate de que el JSON coincide con la estructura de `CreateUserDto` y que tienes los validadores (si usas `class-validator`).
* **404 Not Found**: Verifica la URL y que esté bien registrado el controlador en tu `AppModule`.

¿Quieres que te ayude a validar si tu DTO está bien estructurado o a definirlo correctamente?
