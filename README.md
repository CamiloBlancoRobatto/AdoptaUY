# 🐾 AdoptaUY

**Plataforma web para centralizar la adopción responsable de perros y gatos en Montevideo.**

![Laravel](https://img.shields.io/badge/Laravel-13-FF2D20?logo=laravel&logoColor=white)
![PHP](https://img.shields.io/badge/PHP-8.3+-777BB4?logo=php&logoColor=white)
![MySQL](https://img.shields.io/badge/MySQL-8.x-4479A1?logo=mysql&logoColor=white)
![Nginx](https://img.shields.io/badge/Nginx-009639?logo=nginx&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-2496ED?logo=docker&logoColor=white)
![Estado](https://img.shields.io/badge/estado-en%20desarrollo-yellow)

AdoptaUY es una aplicación web adaptable (responsive) que reúne en un solo lugar a particulares, refugios y adoptantes. Hoy el proceso de adopción está disperso entre redes sociales, carteles y el boca a boca; AdoptaUY lo ordena y le agrega seguimiento después de la adopción.

> Proyecto académico del equipo **CodeCrafters** (ITI, 2026).

---

## ✨ ¿Qué permite hacer?

- **Publicar mascotas en adopción** (con 1 a 6 fotos) y consultarlas con filtros por fecha, edad, especie, raza y sexo.
- **Publicar mascotas perdidas**, con vigencia de 30 días.
- **Solicitar una adopción**: el publicante recibe la lista de solicitantes con sus datos de contacto y elige a quién adjudicar.
- **Seguimiento posterior**: a los 15 días el adoptante envía una fotografía del animal, para reducir el reabandono.
- **Refugios validados**: el Administrador valida la documentación y los refugios aparecen en un mapa de Montevideo.
- **Donaciones**: cada refugio publica su cuenta bancaria. La plataforma **no procesa pagos**.
- **Reportes y moderación** de usuarios y publicaciones.
- **Notificaciones por correo** para los eventos importantes.

## 👥 Actores

| Actor | Qué hace |
|---|---|
| Usuario Invitado | Consulta publicaciones y refugios sin registrarse |
| Particular | Publica, solicita adopciones, reporta |
| Refugio | Igual que el particular, una vez validado; además publica cuentas para donaciones |
| Administrador | Valida refugios, modera y resuelve reportes |

## 🧱 Stack tecnológico

| Capa | Tecnología |
|---|---|
| Backend | PHP 8.3+ con Laravel 13 (MVC, ORM Eloquent) |
| Frontend | HTML5 + CSS3, diseño adaptable |
| Base de datos | MySQL 8.x |
| Tareas y colas | Planificador y colas de Laravel |
| Servidor web | Nginx (proxy inverso hacia PHP-FPM) |
| Infraestructura | Docker sobre Ubuntu Server 24.04 LTS |

## 📁 Estructura del repositorio

```
adoptauy/
├── docs/      Documento integrador y anexos
├── db/        Modelo de datos (DER en Mermaid)
├── src/       Código de la aplicación (Laravel)
├── README.md
├── CONTRIBUTING.md
└── .gitignore
```

## 🗄️ Modelo de datos

El DER está en [`db/DER.md`](db/DER.md) y GitHub lo muestra renderizado. El archivo fuente es [`db/AdoptaUY_DER_subtipos.mmd`](db/AdoptaUY_DER_subtipos.mmd).

## 🚀 Puesta en marcha

> Se completa cuando esté el primer incremento en `src/`.

```bash
git clone https://github.com/<usuario>/adoptauy.git
cd adoptauy/src
# instrucciones de instalación y Docker: pendiente
```

## 🗓️ Estado del proyecto

El proyecto se organiza con **Scrum** en seis sprints, dos por hito.

| Hito | Fecha | Estado |
|---|---|---|
| Hito 1 | 18/09/2026 | ✅ Entregado |
| Hito 2 | 23/10/2026 | 🔧 En curso: registro, inicio de sesión, página de inicio y publicación de mascotas |

El seguimiento de tareas se lleva en Trello.

## 🤝 Equipo

| Integrante | Rol |
|---|---|
| Camilo Blanco | Coordinador general, Scrum Master, desarrollo |
| Leandro Estévez | Subcoordinador, Scrum Master, desarrollo |
| Iñaki Pérez | Desarrollo |
| Rodrigo González | Desarrollo |

**Product Owner:** Martín Viar (docente, en representación del ITI).

Para colaborar, leé [CONTRIBUTING.md](CONTRIBUTING.md).
