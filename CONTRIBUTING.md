# 🤝 Guía de Contribución

Gracias por tu interés en contribuir a este proyecto. Esta guía te ayudará a realizar contribuciones efectivas.

## 📋 Tipos de Contribuciones

- 🐛 **Bug reports**: Reportar errores o problemas
- ✨ **Features**: Proponer nuevas funcionalidades
- 📝 **Documentación**: Mejorar la documentación
- 🎨 **Diseño**: Mejoras visuales o de UX
- ⚡ **Performance**: Optimizaciones de rendimiento

## 🔧 Proceso de Contribución

### 1. Fork y Clone

```bash
# Fork el repositorio en GitHub
# Luego clona tu fork
git clone https://github.com/tu-usuario/qrencounter.git
cd qrencounter
```

### 2. Crear una Rama

```bash
git checkout -b feature/nombre-descriptivo
# o
git checkout -b fix/nombre-del-bug
```

### 3. Realizar Cambios

- Mantén el código limpio y bien comentado
- Sigue las convenciones de estilo existentes
- Prueba tus cambios en múltiples navegadores

### 4. Commit

```bash
git add .
git commit -m "feat: descripción breve del cambio"
```

**Convención de commits:**
- `feat:` Nueva funcionalidad
- `fix:` Corrección de bug
- `docs:` Cambios en documentación
- `style:` Cambios de formato (sin afectar lógica)
- `refactor:` Refactorización de código
- `test:` Añadir o modificar tests
- `chore:` Tareas de mantenimiento

### 5. Push y Pull Request

```bash
git push origin feature/nombre-descriptivo
```

Luego crea un Pull Request en GitHub con:
- Descripción clara del cambio
- Screenshots si es visual
- Referencias a issues relacionados

## 📐 Estándares de Código

### HTML
- Usa HTML5 semántico
- Indentación: 4 espacios
- Atributos en minúsculas
- Comillas dobles para atributos

### CSS
- Mobile-first approach
- Variables CSS para colores reutilizables
- Nombres de clase descriptivos en inglés
- Evitar !important

### JavaScript
- ES6+ syntax
- Async/await sobre Promises
- Comentarios JSDoc para funciones
- Manejo explícito de errores

## ✅ Checklist Pre-PR

- [ ] El código funciona correctamente
- [ ] No hay errores en la consola
- [ ] Funciona en Chrome, Firefox, Safari
- [ ] Funciona en móviles
- [ ] La documentación está actualizada
- [ ] Los commits son descriptivos

## 🐛 Reportar Bugs

Incluye:
1. Descripción del problema
2. Pasos para reproducir
3. Comportamiento esperado vs actual
4. Navegador y versión
5. Screenshots si aplica

## 💡 Sugerir Funcionalidades

Incluye:
1. Descripción de la funcionalidad
2. Caso de uso
3. Beneficio para los usuarios
4. Posible implementación

## 📞 Contacto

¿Preguntas? Abre un issue con la etiqueta `question`.

---

¡Gracias por contribuir! 🎉
