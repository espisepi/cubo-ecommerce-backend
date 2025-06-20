Gracias, el problema está claro: **falta el decorador `@Body()` en el parámetro del método**.

Tu código actual:

```ts
@Post('signup')
signup(createUserDto: CreateUserDto) {
```

Debería ser:

```ts
@Post('signup')
signup(@Body() createUserDto: CreateUserDto) {
```

---

### ✅ Versión corregida:

```ts
import { Body, Controller, Post } from '@nestjs/common';
import { CreateUserDto } from './dto/create-user.dto';

@Controller('auth')
export class AuthController {
  @Post('signup')
  signup(@Body() createUserDto: CreateUserDto) {
    console.log("LA PUTA VARIABLE ESTA: ", {
      createUserDto
    });

    return { createUserDto };
  }
}
```

---

### ¿Por qué ocurre esto?

NestJS **no sabe de dónde obtener `createUserDto` si no le indicas con `@Body()`** que debe buscarlo en el cuerpo de la petición. Sin el decorador, espera que sea un parámetro del sistema de rutas (como `@Param`, `@Query`, etc.), y por eso llega como `undefined`.

---

Corrígelo y vuelve a probar con Insomnia. Verás que ahora sí llega el JSON correctamente.

¿Quieres que revisemos también el DTO o la respuesta del servicio para que todo esté tipado y validado?
