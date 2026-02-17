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
4. Se preparó la validación con múltiples herramientas (WAVE, Axe, Lighthouse, Accessibility Insights, ANDI, ARC Toolkit).
5. Se dejó una bitácora de validación para documentar iteraciones antes/después.

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

## Validación requerida
Ejecutar al menos 3 herramientas y adjuntar capturas antes/después:
1. WAVE
2. Axe DevTools
3. Lighthouse
4. Opcional adicional: Accessibility Insights, ANDI, ARC Toolkit, Access Assistant.

## Capturas
Guardar evidencia en `docs/screenshots/`.
Luego enlazar aquí con formato Markdown a cada captura de antes y después.

## Ejemplo de enlace
- `[WAVE antes - landing](docs/screenshots/wave-antes-index-landing.png)`
- `[WAVE después - landing](docs/screenshots/wave-despues-index-landing.png)`

## Estado actual
- Se generó base completa del ejercicio (original + corregido + prompt + documentación).
- Falta adjuntar capturas reales de validadores externos para cerrar evidencia final de cumplimiento AA/AAA.

## Publicación en GitHub
Comandos sugeridos:

```bash
git init
git add .
git commit -m "feat: proyecto WCAG 2.2 con HTML original y corregido"
# Crear repo remoto y subir (GitHub CLI)
gh repo create repo-wcag22-prompt --public --source=. --remote=origin --push
```

Si no usas `gh`, crea el repositorio manualmente en GitHub y luego:

```bash
git remote add origin https://github.com/TU_USUARIO/repo-wcag22-prompt.git
git branch -M main
git push -u origin main
```
