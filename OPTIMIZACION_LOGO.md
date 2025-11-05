# Guía de Optimización del Logo - Identidad de Territorio

## Comandos para Generar Versiones Optimizadas del Logo

### Prerequisitos
Instala las herramientas necesarias:

```bash
# Windows (con Chocolatey)
choco install imagemagick
choco install webp

# macOS (con Homebrew)
brew install imagemagick
brew install webp

# Ubuntu/Debian
sudo apt install imagemagick webp
```

### 1. Crear Directorio de Assets

```bash
mkdir assets
mkdir assets/icons
mkdir assets/logos
```

### 2. Generar Variantes PNG en Diferentes Tamaños

```bash
# Logo para header (versiones optimizadas)
magick logo.png -resize 120x120 -quality 90 assets/logos/logo-120.png
magick logo.png -resize 88x88 -quality 90 assets/logos/logo-88.png
magick logo.png -resize 64x64 -quality 90 assets/logos/logo-64.png
magick logo.png -resize 45x45 -quality 90 assets/logos/logo-45.png

# Versiones para diferentes densidades de pantalla
magick logo.png -resize 240x240 -quality 90 assets/logos/logo-120@2x.png
magick logo.png -resize 176x176 -quality 90 assets/logos/logo-88@2x.png
magick logo.png -resize 128x128 -quality 90 assets/logos/logo-64@2x.png
magick logo.png -resize 90x90 -quality 90 assets/logos/logo-45@2x.png
```

### 3. Generar Versiones WebP (Mayor Compresión)

```bash
# Convertir a WebP con alta calidad
cwebp -q 85 logo.png -o assets/logos/logo-original.webp
cwebp -q 85 assets/logos/logo-120.png -o assets/logos/logo-120.webp
cwebp -q 85 assets/logos/logo-88.png -o assets/logos/logo-88.webp
cwebp -q 85 assets/logos/logo-64.png -o assets/logos/logo-64.webp
cwebp -q 85 assets/logos/logo-45.png -o assets/logos/logo-45.webp

# Versiones @2x en WebP
cwebp -q 85 assets/logos/logo-120@2x.png -o assets/logos/logo-120@2x.webp
cwebp -q 85 assets/logos/logo-88@2x.png -o assets/logos/logo-88@2x.webp
cwebp -q 85 assets/logos/logo-64@2x.png -o assets/logos/logo-64@2x.webp
cwebp -q 85 assets/logos/logo-45@2x.png -o assets/logos/logo-45@2x.webp
```

### 4. Generar Favicons (Múltiples Tamaños)

```bash
# Favicons estándar
magick logo.png -resize 16x16 -quality 95 assets/icons/favicon-16.png
magick logo.png -resize 32x32 -quality 95 assets/icons/favicon-32.png
magick logo.png -resize 48x48 -quality 95 assets/icons/favicon-48.png

# Apple Touch Icons
magick logo.png -resize 57x57 -quality 95 assets/icons/apple-touch-icon-57.png
magick logo.png -resize 60x60 -quality 95 assets/icons/apple-touch-icon-60.png
magick logo.png -resize 72x72 -quality 95 assets/icons/apple-touch-icon-72.png
magick logo.png -resize 76x76 -quality 95 assets/icons/apple-touch-icon-76.png
magick logo.png -resize 114x114 -quality 95 assets/icons/apple-touch-icon-114.png
magick logo.png -resize 120x120 -quality 95 assets/icons/apple-touch-icon-120.png
magick logo.png -resize 144x144 -quality 95 assets/icons/apple-touch-icon-144.png
magick logo.png -resize 152x152 -quality 95 assets/icons/apple-touch-icon-152.png
magick logo.png -resize 180x180 -quality 95 assets/icons/apple-touch-icon-180.png

# Android/PWA Icons
magick logo.png -resize 192x192 -quality 95 assets/icons/android-icon-192.png
magick logo.png -resize 512x512 -quality 95 assets/icons/android-icon-512.png

# Microsoft Tiles
magick logo.png -resize 70x70 -quality 95 assets/icons/ms-tile-70.png
magick logo.png -resize 150x150 -quality 95 assets/icons/ms-tile-150.png
magick logo.png -resize 310x310 -quality 95 assets/icons/ms-tile-310.png
```

### 5. Generar Favicon.ico (Múltiples Resoluciones)

```bash
# Crear favicon.ico con múltiples tamaños embebidos
magick assets/icons/favicon-16.png assets/icons/favicon-32.png assets/icons/favicon-48.png assets/icons/favicon.ico
```

### 6. Optimizar Todas las Imágenes PNG (Opcional)

```bash
# Si tienes pngquant instalado para mayor compresión
find assets -name "*.png" -exec pngquant --quality=80-95 --output {} {} \;
```

## Cómo Actualizar el HTML

### Agregar Meta Tags para Favicons

Añade esto en el `<head>` de tu `index.html`:

```html
<!-- Favicons -->
<link rel="icon" type="image/x-icon" href="assets/icons/favicon.ico">
<link rel="icon" type="image/png" sizes="16x16" href="assets/icons/favicon-16.png">
<link rel="icon" type="image/png" sizes="32x32" href="assets/icons/favicon-32.png">
<link rel="icon" type="image/png" sizes="48x48" href="assets/icons/favicon-48.png">

<!-- Apple Touch Icons -->
<link rel="apple-touch-icon" sizes="57x57" href="assets/icons/apple-touch-icon-57.png">
<link rel="apple-touch-icon" sizes="60x60" href="assets/icons/apple-touch-icon-60.png">
<link rel="apple-touch-icon" sizes="72x72" href="assets/icons/apple-touch-icon-72.png">
<link rel="apple-touch-icon" sizes="76x76" href="assets/icons/apple-touch-icon-76.png">
<link rel="apple-touch-icon" sizes="114x114" href="assets/icons/apple-touch-icon-114.png">
<link rel="apple-touch-icon" sizes="120x120" href="assets/icons/apple-touch-icon-120.png">
<link rel="apple-touch-icon" sizes="144x144" href="assets/icons/apple-touch-icon-144.png">
<link rel="apple-touch-icon" sizes="152x152" href="assets/icons/apple-touch-icon-152.png">
<link rel="apple-touch-icon" sizes="180x180" href="assets/icons/apple-touch-icon-180.png">

<!-- Android/PWA Icons -->
<link rel="icon" type="image/png" sizes="192x192" href="assets/icons/android-icon-192.png">
<link rel="icon" type="image/png" sizes="512x512" href="assets/icons/android-icon-512.png">

<!-- Microsoft Tiles -->
<meta name="msapplication-TileColor" content="#4CAF50">
<meta name="msapplication-TileImage" content="assets/icons/ms-tile-150.png">
<meta name="msapplication-square70x70logo" content="assets/icons/ms-tile-70.png">
<meta name="msapplication-square150x150logo" content="assets/icons/ms-tile-150.png">
<meta name="msapplication-square310x310logo" content="assets/icons/ms-tile-310.png">
```

### Actualizar CSS para Usar Logos Optimizados

```css
/* Desktop - logo más grande y nítido */
.header-logo { 
    content: url('assets/logos/logo-88.webp');
    height: 88px; 
    width: auto; 
}

/* Móvil - logo optimizado para pantalla pequeña */
@media (max-width: 800px) {
    .header-logo { 
        content: url('assets/logos/logo-45.webp');
        height: 45px; 
    }
}

/* Pantallas de alta densidad - usar versiones @2x */
@media (-webkit-min-device-pixel-ratio: 2), (min-resolution: 192dpi) {
    .header-logo { 
        content: url('assets/logos/logo-88@2x.webp');
    }
    
    @media (max-width: 800px) {
        .header-logo { 
            content: url('assets/logos/logo-45@2x.webp');
        }
    }
}

/* Fallback para navegadores que no soportan WebP */
.no-webp .header-logo { 
    content: url('assets/logos/logo-88.png');
}

.no-webp .header-logo {
    @media (max-width: 800px) {
        content: url('assets/logos/logo-45.png');
    }
}

/* Watermark optimizado */
.watermark-img { 
    content: url('assets/logos/logo-original.webp');
}

.no-webp .watermark-img { 
    content: url('logo.png');
}
```

## Comandos en Lote (Todo de Una Vez)

### Script para Windows (PowerShell)

```powershell
# Crear directorios
New-Item -ItemType Directory -Path "assets\icons" -Force
New-Item -ItemType Directory -Path "assets\logos" -Force

# Generar todas las versiones
$sizes = @(120, 88, 64, 45, 240, 176, 128, 90, 16, 32, 48, 57, 60, 72, 76, 114, 144, 152, 180, 192, 512, 70, 150, 310)
foreach ($size in $sizes) {
    magick logo.png -resize "${size}x${size}" -quality 90 "assets\logos\logo-${size}.png"
    cwebp -q 85 "assets\logos\logo-${size}.png" -o "assets\logos\logo-${size}.webp"
}

# Crear favicon.ico
magick "assets\logos\logo-16.png" "assets\logos\logo-32.png" "assets\logos\logo-48.png" "assets\icons\favicon.ico"
```

### Script para Unix/Linux/macOS (Bash)

```bash
#!/bin/bash
# Crear directorios
mkdir -p assets/icons assets/logos

# Generar todas las versiones
sizes=(120 88 64 45 240 176 128 90 16 32 48 57 60 72 76 114 144 152 180 192 512 70 150 310)
for size in "${sizes[@]}"; do
    magick logo.png -resize "${size}x${size}" -quality 90 "assets/logos/logo-${size}.png"
    cwebp -q 85 "assets/logos/logo-${size}.png" -o "assets/logos/logo-${size}.webp"
done

# Crear favicon.ico
magick assets/logos/logo-16.png assets/logos/logo-32.png assets/logos/logo-48.png assets/icons/favicon.ico
```

## Beneficios de Esta Optimización

1. **Rendimiento**: Imágenes más pequeñas cargan más rápido
2. **Responsividad**: Diferentes tamaños para diferentes dispositivos
3. **Calidad**: Versiones @2x para pantallas de alta densidad
4. **Compatibilidad**: Favicons para todos los navegadores y dispositivos
5. **SEO**: Mejores métricas de velocidad de carga
6. **UX**: Logo visible y nítido en todos los dispositivos

## Verificación

Después de ejecutar los comandos, tu estructura debería verse así:

```
IDENTIDAD DE TERRITORIO/
├── index.html
├── logo.png (original)
├── OPTIMIZACION_LOGO.md
└── assets/
    ├── icons/
    │   ├── favicon.ico
    │   ├── favicon-16.png
    │   ├── favicon-32.png
    │   ├── apple-touch-icon-*.png
    │   ├── android-icon-*.png
    │   └── ms-tile-*.png
    └── logos/
        ├── logo-45.png
        ├── logo-45.webp
        ├── logo-45@2x.png
        ├── logo-45@2x.webp
        ├── logo-64.png
        ├── logo-64.webp
        └── ... (más variantes)
```

¡Ejecuta estos comandos y tendrás un logo perfectamente optimizado para todos los dispositivos!