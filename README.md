# Repositorio de Prompt de Accesibilidad WCAG 2.2

## Objetivo
Este repositorio documenta el diseño y la validación de un prompt eficaz para asistentes de programación (Copilot, Gemini y equivalentes) orientado a corregir HTML según WCAG 2.2 y buenas prácticas ARIA.

## Estructura del repositorio
- `originals/`: versiones iniciales sin foco especial en accesibilidad.
- `corrected/`: versiones corregidas aplicando semántica, ARIA y criterios A/AA (AAA opcional).
- `prompts/prompt-perfecto.md`: prompt maestro y variante estricta de reintento.
- `docs/screenshots/`: capturas de validación antes/después.
- `docs/validation/validation-log.md`: bitácora de resultados de validación.

## Proceso de desarrollo del prompt
1. Se crearon tres páginas base con problemas frecuentes de accesibilidad: `index-landing.html`, `index-form.html` e `index-table-media.html`.
2. Se redactó un prompt maestro con reglas concretas de WCAG 2.2 (semántica, estructura, contraste, teclado, formularios, tablas, imágenes y ARIA).
3. Se aplicó el prompt para generar versiones corregidas en `corrected/`.
4. Se ejecutó validación automática comparativa antes/después con WAVE, Axe DevTools y Lighthouse.
5. Se documentaron resultados y evidencias con capturas.

## Problemas encontrados y soluciones aplicadas
- Falta de `lang` en `<html>` -> se añadió `lang="es"`.
- Contraste insuficiente -> se ajustó paleta de colores para AA.
- Encabezados desordenados -> jerarquía semántica corregida (`h1`, `h2`, etc.).
- Uso de `div` clicables -> sustitución por elementos nativos (`a`, `button`).
- Falta de landmarks -> incorporación de `header`, `nav`, `main`, `footer`.
- Enlaces ambiguos -> textos con propósito claro.
- Navegación por teclado mejorada -> enlace de salto, foco visible y orden lógico.

## Prompt utilizado
Ver `prompts/prompt-perfecto.md`.

## Validación de accesibilidad (antes/después)
Caso documentado: `index-landing.html`.

### WAVE
- Antes: AIM 7.2/10, 1 error de idioma, 1 error de contraste y 5 alertas.
- Después: AIM 10/10, 0 errores, 0 errores de contraste y 1 alerta (enlace redundante).

### Axe DevTools
- Antes: 2 problemas graves (`html` sin `lang` y contraste insuficiente).
- Después: 0 problemas automáticos.

### Lighthouse
- Antes: 74/100.
- Después: 100/100.

## Conclusión
Tras aplicar el prompt, la versión corregida eliminó los errores críticos detectados automáticamente por WAVE, Axe DevTools y Lighthouse, logrando una mejora consistente en cumplimiento de accesibilidad conforme a WCAG.

## Evidencias (capturas)
- [WAVE antes - landing](docs/screenshots/wave-antes-index-landing.png)
- [WAVE después - landing](docs/screenshots/wave-despues-index-landing.png)
- [Axe antes - landing](docs/screenshots/axe-antes-index-landing.png)
- [Axe después - landing](docs/screenshots/axe-despues-index-landing.png)
- [Lighthouse antes - landing](docs/screenshots/lighthouse-antes-index-landing.png)
- [Lighthouse después - landing](docs/screenshots/lighthouse-despues-index-landing.png)

## Checklist de entrega
- [x] Archivos HTML originales y corregidos.
- [x] Prompt final documentado.
- [x] Validación con al menos tres herramientas (WAVE, Axe, Lighthouse).
- [x] Capturas antes/después.
- [x] Bitácora de resultados de validación.
- [x] README en español con proceso, problemas y soluciones.

## Publicación en GitHub
```bash
git add .
git commit -m "docs: versión final lista para entrega"
git remote add origin https://github.com/TU_USUARIO/repo-wcag22-prompt.git
git branch -M main
git push -u origin main
```
