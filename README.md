# 🔗 QR Dinámico con GitHub Pages

Sistema profesional de redirección dinámica para códigos QR utilizando GitHub Pages. Permite cambiar el destino del QR sin necesidad de regenerarlo.

## 📋 Características

- ✅ **Redirección dinámica**: Cambia el destino sin regenerar el QR
- ✅ **JavaScript moderno**: Usa `fetch` y `async/await`
- ✅ **Manejo de errores**: Fallback automático si falla la configuración
- ✅ **Meta refresh**: Redirección de respaldo sin JavaScript
- ✅ **Responsive**: Funciona en todos los dispositivos
- ✅ **Zero dependencies**: No requiere librerías externas
- ✅ **Compatible con GitHub Pages**: Despliegue gratuito y automático

## 🏗️ Estructura del Proyecto

```
qrencounter/
├── index.html      # Página principal con lógica de redirección
├── config.json     # Configuración de URL destino
└── README.md       # Documentación del proyecto
```

## 🚀 Configuración Inicial

### 1. Clonar o Fork del Repositorio

```bash
git clone https://github.com/tu-usuario/qrencounter.git
cd qrencounter
```

### 2. Configurar GitHub Pages

1. Ve a **Settings** → **Pages** en tu repositorio
2. En **Source**, selecciona la rama `main` y carpeta `/ (root)`
3. Guarda los cambios
4. Tu sitio estará disponible en: `https://tu-usuario.github.io/qrencounter/`

### 3. Generar el Código QR

Genera tu código QR apuntando a:
```
https://tu-usuario.github.io/qrencounter/
```

**Herramientas recomendadas:**
- [QR Code Generator](https://www.qr-code-generator.com/)
- [QRCode Monkey](https://www.qrcode-monkey.com/)
- API: `https://api.qrserver.com/v1/create-qr-code/?size=300x300&data=https://tu-usuario.github.io/qrencounter/`

## ⚙️ Configuración de la URL Destino

### Método 1: Editar directamente en GitHub (Recomendado)

1. Abre `config.json` en GitHub
2. Haz clic en el icono de editar (lápiz)
3. Modifica la URL:
   ```json
   {
     "redirectUrl": "https://www.tu-nuevo-destino.com",
     "metadata": {
       "lastUpdated": "2025-12-13",
       "description": "URL de destino para redirección dinámica de códigos QR",
       "version": "1.0.0"
     }
   }
   ```
4. Commit los cambios
5. Espera ~1 minuto para que GitHub Pages actualice

### Método 2: Editar localmente

```bash
# Editar config.json
nano config.json

# Commit y push
git add config.json
git commit -m "Actualizar URL de redirección"
git push origin main
```

## 🔧 Funcionamiento Técnico

### Flujo de Redirección

1. **Usuario escanea QR** → Abre `https://tu-usuario.github.io/qrencounter/`
2. **JavaScript carga** → Hace `fetch` de `config.json`
3. **Valida URL** → Verifica que sea válida
4. **Redirige** → `window.location.href = config.redirectUrl`

### Sistema de Fallback

Si `config.json` falla por cualquier razón:
- ✅ Se activa el `<meta http-equiv="refresh">` (línea 6 del HTML)
- ✅ Redirige a URL de respaldo en 5 segundos
- ✅ Muestra mensaje de error al usuario

### Prevención de Caché

El código incluye `cache: 'no-cache'` en el fetch para evitar que el navegador use versiones antiguas de `config.json`.

## 📱 Casos de Uso

### Caso 1: Menú de Restaurante
```json
{
  "redirectUrl": "https://drive.google.com/file/d/tu-menu-pdf/view"
}
```

### Caso 2: Formulario de Contacto
```json
{
  "redirectUrl": "https://forms.google.com/tu-formulario"
}
```

### Caso 3: Página de Producto
```json
{
  "redirectUrl": "https://www.tienda.com/producto/oferta-especial"
}
```

### Caso 4: Red Social
```json
{
  "redirectUrl": "https://instagram.com/tu-cuenta"
}
```

## 🎨 Personalización

### Cambiar Colores del Gradiente

En [index.html](index.html#L25), modifica:
```css
background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
```

### Cambiar Tiempo de Redirección

**JavaScript** ([index.html](index.html#L103)):
```javascript
setTimeout(() => {
    window.location.href = config.redirectUrl;
}, 1000); // Cambiar 1000 (1 segundo)
```

**Meta Refresh** ([index.html](index.html#L6)):
```html
<meta http-equiv="refresh" content="5;url=https://www.google.com">
<!-- Cambiar el 5 (5 segundos) -->
```

### Cambiar Idioma

Modifica los textos en [index.html](index.html#L92-L93):
```html
<h1>Redirecting...</h1>
<p id="message">Please wait a moment.</p>
```

## 🛡️ Seguridad

### Validaciones Implementadas

1. **Validación de respuesta HTTP**: Verifica status 200
2. **Validación de estructura JSON**: Comprueba que `redirectUrl` existe
3. **Validación de formato URL**: Usa `new URL()` para validar
4. **Prevención XSS**: No inyecta HTML sin sanitizar

### URL de Respaldo

⚠️ **IMPORTANTE**: Cambia la URL de respaldo en el meta refresh:
```html
<meta http-equiv="refresh" content="5;url=https://www.tu-sitio-respaldo.com">
```

## 📊 Analytics (Opcional)

Para rastrear los escaneos, añade Google Analytics antes del `</head>`:

```html
<!-- Google Analytics -->
<script async src="https://www.googletagmanager.com/gtag/js?id=G-XXXXXXXXXX"></script>
<script>
  window.dataLayer = window.dataLayer || [];
  function gtag(){dataLayer.push(arguments);}
  gtag('js', new Date());
  gtag('config', 'G-XXXXXXXXXX');
</script>
```

## 🐛 Solución de Problemas

### El QR no redirige

1. Verifica que GitHub Pages esté activo
2. Comprueba que `config.json` tenga formato válido
3. Usa la consola del navegador (F12) para ver errores

### Error "Failed to fetch"

- GitHub Pages aún no ha publicado los cambios (espera 1-2 minutos)
- Verifica que `config.json` esté en la raíz del repositorio
- Comprueba que el repositorio sea público

### Caché del navegador

Si los cambios no se reflejan:
```javascript
// El código ya incluye cache: 'no-cache'
// Alternativamente, añade un timestamp:
fetch(`config.json?t=${Date.now()}`)
```

## 🔄 Actualización del Destino

### Frecuencia recomendada
- ✅ Se puede cambiar tan frecuentemente como necesites
- ✅ Los cambios se propagan en ~1 minuto
- ✅ No afecta al código QR impreso

### Proceso de actualización
1. Editar `config.json` en GitHub
2. Commit cambios
3. Esperar propagación (~1 min)
4. ¡Listo! El QR apunta al nuevo destino

## 📝 Mantenimiento

### Backup de configuración
```bash
# Clonar localmente
git clone https://github.com/tu-usuario/qrencounter.git

# Hacer backup
cp config.json config.backup.json
```

### Versionado
Usa los commits de Git como historial:
```bash
# Ver historial de cambios
git log config.json

# Revertir a versión anterior
git checkout [commit-hash] config.json
```

## 🚀 Despliegue en Producción

### Checklist pre-despliegue

- [ ] Configurar URL de respaldo en meta refresh
- [ ] Validar formato de `config.json`
- [ ] Probar redirección en varios dispositivos
- [ ] Activar GitHub Pages
- [ ] Generar código QR con URL correcta
- [ ] Probar QR escaneado en móvil
- [ ] Configurar Analytics (opcional)

## 📄 Licencia

Este proyecto es de código abierto. Puedes usarlo libremente para proyectos personales o comerciales.

## 🤝 Contribuciones

¿Mejoras o sugerencias? Abre un issue o pull request.

---

**Desarrollado con ❤️ para Encounter Coffee**

*Última actualización: Diciembre 2025*
