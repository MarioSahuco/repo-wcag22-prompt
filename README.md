# Repositorio de Prompt de Accesibilidad WCAG 2.2 / WCAG 2.2 Accessibility Prompt Repo

## ES - Objetivo
Este repositorio documenta un proceso para diseñar y probar un prompt eficaz que guíe asistentes de programación (Copilot, Gemini, etc.) para corregir HTML según WCAG 2.2 + ARIA.

## EN - Objective
This repository documents a process to design and test an effective prompt that guides coding assistants (Copilot, Gemini, etc.) to fix HTML according to WCAG 2.2 + ARIA.

## Estructura / Structure
- `originals/`: versiones iniciales sin foco especial en accesibilidad.
- `corrected/`: versiones corregidas aplicando semántica, ARIA y criterios A/AA (AAA opcional).
- `prompts/prompt-perfecto.md`: prompt maestro y prompt estricto de reintento.
- `docs/screenshots/`: evidencias de validación (antes/después).
- `docs/validation/validation-log.md`: bitácora de pruebas.

## ES - Proceso seguido
1. Se crearon 3 páginas originales con patrones comunes de problemas: navegación no semántica, formulario sin etiquetas, tabla sin estructura, textos ambiguos y contraste pobre.
2. Se redactó un prompt maestro con reglas obligatorias de WCAG 2.2 y buenas prácticas ARIA.
3. Se aplicó el prompt para obtener versiones corregidas en `corrected/`.
4. Se preparó la validación con múltiples herramientas (WAVE, Axe, Lighthouse, Accessibility Insights, ANDI, ARC Toolkit).
5. Se dejó una bitácora de validación para documentar iteraciones antes/después.

## EN - Process followed
1. Three original pages were created with typical accessibility issues: non-semantic navigation, unlabeled forms, unstructured tables, ambiguous links, and poor contrast.
2. A master prompt was written with mandatory WCAG 2.2 rules and ARIA best practices.
3. The prompt was applied to produce corrected versions in `corrected/`.
4. Validation workflow was prepared with multiple tools (WAVE, Axe, Lighthouse, Accessibility Insights, ANDI, ARC Toolkit).
5. A validation log was added to document before/after iterations.

## ES - Problemas detectados y soluciones aplicadas
- Estructura de encabezados inconsistente -> jerarquía `h1`/`h2` corregida.
- Uso de `div` clicables -> reemplazo por enlaces/botones nativos.
- Formularios sin asociación `label`/`input` -> asociación completa y ayudas con `aria-describedby`.
- Tablas sin `caption` ni `scope` -> estructura semántica completa.
- Texto de enlaces ambiguo -> enlaces con propósito claro.
- Falta de navegación por teclado -> skip link, foco visible y orden lógico.
- Contraste insuficiente -> paleta ajustada para AA.

## EN - Issues found and applied fixes
- Inconsistent heading structure -> corrected `h1`/`h2` hierarchy.
- Clickable `div`s -> replaced with native links/buttons.
- Forms without `label`/`input` mapping -> full associations and helper text via `aria-describedby`.
- Tables without `caption`/`scope` -> complete semantic structure.
- Ambiguous link text -> clear-purpose link labels.
- Missing keyboard navigation support -> skip link, visible focus, logical tab order.
- Insufficient contrast -> AA-friendly color palette.

## Prompt utilizado / Prompt used
Ver `prompts/prompt-perfecto.md`.

## Validación requerida / Required validation
Ejecutar al menos 3 herramientas y adjuntar capturas antes/después:
1. WAVE
2. Axe DevTools
3. Lighthouse
4. (Opcional adicional) Accessibility Insights, ANDI, ARC Toolkit, Access Assistant

## Capturas / Screenshots
Guardar evidencia en `docs/screenshots/`.
Luego enlazar aquí:
- ES: Inserta enlaces Markdown a cada captura de “antes” y “después”.
- EN: Insert Markdown links to each “before” and “after” screenshot.

## Ejemplo de enlace / Link example
- `[WAVE antes - landing](docs/screenshots/wave-before-index-landing.png)`
- `[WAVE después - landing](docs/screenshots/wave-after-index-landing.png)`

## Estado actual / Current status
- Se generó base completa del ejercicio (original + corregido + prompt + documentación).
- Falta adjuntar capturas reales de validadores externos para cerrar evidencia final de cumplimiento AA/AAA.

## Publicación en GitHub / Publishing to GitHub
Comandos sugeridos:

```bash
git init
git add .
git commit -m "feat: add WCAG 2.2 prompt project with original and corrected HTML"
# Crear repo remoto y subir (GitHub CLI)
gh repo create repo-wcag22-prompt --public --source=. --remote=origin --push
```

Si no usas `gh`, crea el repositorio manualmente en GitHub y luego:

```bash
git remote add origin https://github.com/TU_USUARIO/repo-wcag22-prompt.git
git branch -M main
git push -u origin main
```
