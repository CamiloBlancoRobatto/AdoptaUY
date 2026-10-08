# Cómo trabajamos en el repositorio

Guía corta para que el equipo no se pise.

## Ramas

- `main`: siempre estable. **Nadie sube directo acá.**
- Una rama por tarea, con el nombre de la tarea:
  - `feature/registro-particular`
  - `fix/validacion-email`
  - `docs/actualizar-der`

## Flujo de trabajo

1. Antes de empezar: `git checkout main && git pull`
2. Crear la rama: `git checkout -b feature/nombre-de-la-tarea`
3. Trabajar y hacer commits chicos y frecuentes.
4. Subir la rama: `git push -u origin feature/nombre-de-la-tarea`
5. Abrir un **Pull Request** hacia `main` en GitHub.
6. Otro integrante lo revisa y lo aprueba. Recién ahí se une (**Merge**).
7. Borrar la rama y volver a `main`: `git checkout main && git pull`

## Mensajes de commit

Una línea clara, en presente y con un prefijo:

```
feat: agrega formulario de registro de particular
fix: corrige validación del email
docs: actualiza DER con subtipos de publicación
refactor: separa lógica de publicaciones en un servicio
```

## Pull Requests

- Título claro y una descripción de qué cambia y por qué.
- Si cierra una tarea de Trello, poner el enlace a la tarjeta.
- Probar que funciona antes de pedir revisión.

## Qué no se sube

- Contraseñas, claves ni el archivo `.env` (ya está en `.gitignore`).
- Carpetas `vendor/` y `node_modules/`.
- Datos personales reales (por ejemplo, la encuesta con correos).
