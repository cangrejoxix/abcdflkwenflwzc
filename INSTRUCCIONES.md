# INSTRUCCIONES - Gestión de Anuncios Gonty

## Flujo de Trabajo

### Agregar Anuncio Nuevo

1. **Sube el video a Odysee**
   - Ve a https://odysee.com/$/upload
   - Sube tu video
   - Copia la URL del video publicado

2. **Edita anuncios.json**
   - Abre `anuncios.json`
   - Copia el bloque de ejemplo
   - Pega la URL de Odysee en `url_video`
   - Cambia los datos del patrocinador
   - Cambia `activo` a `true`

3. **Sube a GitHub**
   - `git add .`
   - `git commit -m "Nuevo anuncio: NOMBRE"`
   - `git push`

4. **Listo**
   - La app lo refleja en máximo 7 días

### Quitar Anuncio

1. Abre `anuncios.json`
2. Cambia `"activo": false`
3. `git push`

### Actualizar Anuncio

1. Edita los campos en `anuncios.json`
2. `git push`

## Estructura del JSON

```json
{
  "id": "ADV-001",           // Identificador único
  "activo": true,            // true = se muestra, false = no se muestra
  "patrocinador": "Nombre",  // Nombre del negocio
  "descripcion": "Texto",    // Descripción del anuncio
  "url_video": "https://odysee.com/...", // URL del video en Odysee
  "url_imagen": "https://...", // URL de la imagen (opcional)
  "url_plataforma": "https://...", // Link al sitio del patrocinador
  "url_redes": "https://...", // Link a redes sociales
  "fecha_inicio": "2026-07-01", // Cuándo empieza
  "fecha_fin": "2026-08-01"     // Cuándo termina
}
```

## Plataformas de Video

| Tipo de Video | Plataforma | Cuenta |
|---|---|---|
| Videos normales | YouTube | Anónima |
| Videos polémicos/adultos | Odysee | Anónima |

## Notas Importantes

- El JSON vive aquí (GitHub privado)
- Los videos viven en Odysee o YouTube
- La app lee el JSON de GitHub cada 7 días
- El usuario NUNCA necesita actualizar la APK
- Para borrar un anuncio: cambia `activo` a `false`
