# Repositorio de Prompt de Accesibilidad WCAG 2.2

## Objetivo
Este repositorio documenta un proceso para diseñar y probar un prompt eficaz que guíe asistentes de programación (Copilot, Gemini, etc.) para corregir HTML según WCAG 2.2 + ARIA.

## Estructura
- `originals/`: versiones iniciales sin foco especial en accesibilidad.
- `corrected/`: versiones corregidas aplicando semántica, ARIA y criterios A/AA (AAA opcional).
- `prompts/prompt-perfecto.md`: prompt maestro y prompt estricto de reintento.
- `docs/screenshots/`: evidencias de validación (antes/después).
- `docs/validation/validation-log.md`: bitácora de pruebas.

## Proceso seguido
1. Se crearon 3 páginas originales con patrones comunes de problemas: navegación no semántica, formulario sin etiquetas, tabla sin estructura, textos ambiguos y contraste pobre.
2. Se redactó un prompt maestro con reglas obligatorias de WCAG 2.2 y buenas prácticas ARIA.
3. Se aplicó el prompt para obtener versiones corregidas en `corrected/`.
4. Se validó el resultado con herramientas automáticas (WAVE, Axe DevTools y Lighthouse).
5. Se documentaron resultados de antes/después en la bitácora de validación.

## Problemas detectados y soluciones aplicadas
- Estructura de encabezados inconsistente -> jerarquía `h1`/`h2` corregida.
- Uso de `div` clicables -> reemplazo por enlaces/botones nativos.
- Formularios sin asociación `label`/`input` -> asociación completa y ayudas con `aria-describedby`.
- Tablas sin `caption` ni `scope` -> estructura semántica completa.
- Texto de enlaces ambiguo -> enlaces con propósito claro.
- Falta de navegación por teclado -> enlace de salto al contenido, foco visible y orden lógico.
- Contraste insuficiente -> paleta ajustada para AA.

## Prompt utilizado
Ver `prompts/prompt-perfecto.md`.

## Resultados de validación (página landing)
Se validó la versión original (`originals/index-landing.html`) y la versión corregida (`corrected/index-landing.html`) con WAVE, Axe DevTools y Lighthouse.

### WAVE
- Antes: AIM 7.2/10, 1 error de idioma, 1 error de contraste y 5 alertas.
- Después: AIM 10/10, 0 errores, 0 errores de contraste y 1 alerta (enlace redundante).

### Axe DevTools
- Antes: 2 problemas graves (`html` sin `lang` y contraste insuficiente).
- Después: 0 problemas automáticos.

### Lighthouse
- Antes: 74/100.
- Después: 100/100.

### Conclusión
La versión corregida elimina los errores críticos detectados por los validadores automáticos y mejora de forma clara el cumplimiento de accesibilidad conforme a WCAG.

## Evidencias (capturas)
- [WAVE antes - landing](docs/screenshots/wave-antes-index-landing.png)
- [WAVE después - landing](docs/screenshots/wave-despues-index-landing.png)
- [Axe antes - landing](docs/screenshots/axe-antes-index-landing.png)
- [Axe después - landing](docs/screenshots/axe-despues-index-landing.png)
- [Lighthouse antes - landing](docs/screenshots/lighthouse-antes-index-landing.png)
- [Lighthouse después - landing](docs/screenshots/lighthouse-despues-index-landing.png)

## Estado actual
- Base del ejercicio completa (original + corregido + prompt + documentación).
- Validación y evidencias completas para `index-landing.html`.
- Pendiente, si se requiere por rúbrica, replicar evidencias equivalentes para `index-form.html` e `index-table-media.html`.

## Publicación en GitHub
Comandos sugeridos:

```bash
git add .
git commit -m "docs: agregar resultados y capturas de validación de accesibilidad"
# Crear repo remoto y subir (GitHub CLI)
gh repo create repo-wcag22-prompt --public --source=. --remote=origin --push
```

Si no usas `gh`, crea el repositorio manualmente en GitHub y luego:

```bash
git remote add origin https://github.com/TU_USUARIO/repo-wcag22-prompt.git
git branch -M main
git push -u origin main
```
