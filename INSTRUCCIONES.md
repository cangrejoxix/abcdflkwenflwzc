# INSTRUCCIONES - Gestión de Anuncios Gonty

## Flujo de Trabajo

### Agregar Anuncio Nuevo

1. **Sube archivos a Cloudflare R2**
   - Sube la imagen/banner a `gonty-assets/imagenes/`
   - Sube el video (si aplica) a `gonty-assets/videos/`
   - Copia las URLs de R2

2. **Edita anuncios.json**
   - Abre `anuncios.json`
   - Copia el bloque de ejemplo
   - Pega las URLs de R2
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
  "url_video": "https://...", // URL del video en R2
  "url_imagen": "https://...", // URL de la imagen en R2
  "url_plataforma": "https://...", // Link al sitio del patrocinador
  "url_redes": "https://...", // Link a redes sociales
  "fecha_inicio": "2026-07-01", // Cuándo empieza
  "fecha_fin": "2026-08-01"     // Cuándo termina
}
```

## URLs de Cloudflare R2

- **Bucket:** `gonty-assets`
- **Endpoint:** `https://TU-CUENTA.r2.cloudflarestorage.com`
- **Estructura:**
  - `gonty-assets/videos/` → Videos de anuncios
  - `gonty-assets/imagenes/` → Imágenes/banners

## Notas Importantes

- El JSON vive aquí (GitHub privado)
- Los archivos pesados (videos/imagenes) viven en R2
- La app lee el JSON vía Cloudflare Worker cada 7 días
- El usuario NUNCA necesita actualizar la APK
