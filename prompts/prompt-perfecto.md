# Prompt perfecto para asistentes de programación (WCAG 2.2 + ARIA)

## Prompt maestro (copiar y pegar)

Actúa como especialista senior en accesibilidad web y revisa **solo este archivo HTML**.
Objetivo: devolver una versión corregida que cumpla **WCAG 2.2 nivel AA** (y aplicar criterios AAA cuando no rompan UX ni contenido).
No expliques teoría: entrega el HTML final completo y, al final, un checklist breve de cumplimiento.

Reglas obligatorias:
1. Mantén funcionalidad y contenido original; mejora estructura semántica y accesibilidad.
2. Usa HTML semántico primero (`header`, `nav`, `main`, `section`, `article`, `aside`, `footer`, `button`, `table`, `form`, etc.).
3. Usa ARIA solo cuando la semántica nativa no alcance; evita `role` redundantes.
4. Garantiza navegación por teclado:
   - orden de foco lógico,
   - foco visible de alto contraste,
   - sin `tabindex` positivo,
   - evita trampas de teclado.
5. Encabezados jerárquicos correctos (`h1` único por página y estructura secuencial).
6. Formularios accesibles:
   - cada control con `label` asociado (`for`/`id`),
   - ayuda y errores con `aria-describedby`,
   - campos obligatorios identificados visual y programáticamente.
7. Imágenes:
   - `alt` descriptivo en imágenes informativas,
   - `alt=""` en decorativas.
8. Enlaces y botones:
   - texto de propósito claro (sin “click aquí”),
   - nombre accesible correcto.
9. Tablas:
   - usa `caption`, `thead`, `tbody`, `th` con `scope` apropiado.
10. Landmarks y navegación:
    - incluye enlace “saltar al contenido”,
    - `nav` con `aria-label` claro cuando haya varias navegaciones.
11. Contraste:
    - texto normal al menos 4.5:1 (AA),
    - componentes e indicadores de foco visibles,
    - no depender solo del color para transmitir significado.
12. Idioma y metadatos:
    - `lang` correcto en `<html>`,
    - `meta viewport` presente.
13. `accesskey`:
    - no usar salvo requisito explícito; si existe, documenta conflictos de atajos.
14. Si detectas JS inline no accesible (`onclick` en `div`, etc.), reemplázalo por controles nativos accesibles.
15. Devuelve:
    - HTML final completo,
    - checklist final con criterios WCAG 2.2 cubiertos (A/AA y AAA opcional aplicado).

## Variante estricta para reintentos

Rehaz el archivo desde cero manteniendo el contenido textual, pero optimiza para pasar validadores WAVE, Axe y Lighthouse sin errores críticos de accesibilidad.
Prioriza: semántica nativa, foco visible, nombres accesibles, contraste y estructura de encabezados.
Entrega un único HTML final sin texto adicional salvo checklist final.
