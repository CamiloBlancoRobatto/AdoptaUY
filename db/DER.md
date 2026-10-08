# Modelo de datos (DER)

Versión con `Publicacion_Animal` separada en dos subtipos (`Publicacion_Adopcion` y `Publicacion_Perdida`). La versión que sigue el pasaje a tablas original del documento integrador es [`AdoptaUY_DER.mmd`](AdoptaUY_DER.mmd).

Notas:
- La ISA de `Usuario` (Particular, Refugio, Administrador) es total y disjunta; Mermaid no la dibuja, por eso se muestra como tres relaciones 1 : 0..1.
- `Reporte` apunta a un usuario **o** a una publicación (una de las dos FK queda nula).

```mermaid
erDiagram
    Usuario {
        int ID_Usuario PK
        string Email
        string Contrasena
        string Tipo_Usuario
        string Estado_Usuario
        date Fecha_Alta
        boolean Email_Verificado
    }

    Particular {
        int ID_Usuario PK, FK
        string CI
        string Nombre
        string Apellido
        string Telefono
    }

    Administrador {
        int ID_Usuario PK, FK
    }

    Refugio {
        int ID_Usuario PK, FK
        string Nombre_Refugio
        string Certificado_Personeria
        string Comprobante_Domicilio
        string Ubicacion
        decimal Latitud
        decimal Longitud
        string Estado_Validacion
        string Motivo_Rechazo
        date Fecha_Solicitud
        date Fecha_Resolucion
        string URL_Foto
    }

    Refugio_Datos_Contacto {
        int ID_Usuario PK, FK
        string Dato_Contacto PK
    }

    Cuenta_Bancaria {
        int ID_Cuenta_Banco PK
        int ID_Usuario PK, FK
        string Banco
        string Tipo_Cuenta
        string Numero_Cuenta
        string Titular
    }

    Publicacion_Animal {
        int ID_Publicacion PK
        int ID_Usuario FK
        string Especie
        string Raza
        string Sexo
        string Descripcion
        string Estado_Publicacion
        string Estado_Moderacion
        date Fecha_Creacion
    }

    Publicacion_Adopcion {
        int ID_Publicacion PK, FK
        int Edad_Meses
        string Tamano
        string Estado_Salud
        string Temperamento
        string Estado_Esterilizacion
        string Ubicacion_Aproximada
    }

    Publicacion_Perdida {
        int ID_Publicacion PK, FK
        string Nombre_Mascota
        date Fecha_Extravio
        string Zona_Extravio
        string Contacto
        date Fecha_Vencimiento
    }

    Foto_Animal {
        int ID_Foto PK
        int ID_Publicacion PK, FK
        string URL_Foto
    }

    Solicitud_Adopcion {
        int ID_Solicitud PK
        int ID_Publicacion FK
        int ID_Usuario FK
        date Fecha_Solicitud
        string Estado_Solicitud
    }

    Adopcion {
        int ID_Adopcion PK
        int ID_Solicitud FK
        date Fecha_Adopcion
    }

    Seguimiento {
        int ID_Adopcion PK, FK
        date Fecha_Aviso
        date Fecha_Limite
        string URL_Foto
        date Fecha_Envio
        string Estado_Evidencia
    }

    Reporte {
        int ID_Reporte PK
        int ID_Usuario_Reportante FK
        int ID_Usuario_Reportado FK
        int ID_Publicacion_Reportada FK
        string Motivo
        date Fecha_Reporte
        string Estado_Reporte
        string Medida
    }

    %% ISA de Usuario (total y disjunta)
    Usuario ||--o| Particular : "es"
    Usuario ||--o| Refugio : "es"
    Usuario ||--o| Administrador : "es"

    %% Refugio
    Refugio ||--|{ Refugio_Datos_Contacto : "tiene"
    Refugio ||--o{ Cuenta_Bancaria : "registra"

    %% Publicaciones
    Usuario ||--o{ Publicacion_Animal : "publica"
    Publicacion_Animal ||--o| Publicacion_Adopcion : "es"
    Publicacion_Animal ||--o| Publicacion_Perdida : "es"
    Publicacion_Animal ||--|{ Foto_Animal : "tiene"

    %% Adopcion y seguimiento
    Usuario ||--o{ Solicitud_Adopcion : "solicita"
    Publicacion_Adopcion ||--o{ Solicitud_Adopcion : "recibe"
    Solicitud_Adopcion ||--o| Adopcion : "genera"
    Adopcion ||--|| Seguimiento : "tiene"

    %% Reportes (relacion exclusiva: usuario O publicacion)
    Usuario ||--o{ Reporte : "reporta"
    Usuario |o--o{ Reporte : "es_reportado"
    Publicacion_Animal |o--o{ Reporte : "es_reportada"
```
