# Execution Plan: agentic-screen-context

## Fase 1: Entorno, Repositorio y Tipado
- [x] Crear repositorio GitHub en `v0.1.0` vía `github-mcp-server`.
- [x] Crear documentación de arquitectura (`specs/SPEC.md`, `DESIGN.md`, `plan.md`, `.agents/rules/`, `PROJECT_MEMORY.md`).
- [ ] Configurar `package.json`, `tsconfig.json`, `.gitignore`, `LICENSE`.
- [ ] Crear interfaces globales en `src/types/index.ts`.

## Fase 2: Implementación de Módulos con Loop Prompting
- [ ] **Módulo Capture** (`src/modules/capture.ts`):
  - Invocación de utilidades nativas según SO (Linux X11/Wayland, macOS, Windows).
  - Loop Prompting: `tests/capture.test.ts` (100% pasando).
- [ ] **Módulo Parser** (`src/modules/parser.ts`):
  - Extracción de rutas, funciones y errores con regex.
  - Tesseract.js WASM + integración Gemini si `GEMINI_API_KEY` existe.
  - Loop Prompting: validación con tests de regex y parsing.
- [ ] **Módulo Enricher** (`src/modules/enricher.ts`):
  - Búsqueda fuzzy con `fuzzysort` en archivos locales.
  - Extracción contextual de +/- 15 líneas e imports.
  - Loop Prompting: `tests/enricher.test.ts` (100% pasando).
- [ ] **Módulo Formatter** (`src/modules/formatter.ts`):
  - Generación de Markdown estructurado y copiado con `clipboardy`.

## Fase 3: CLI, Orquestador Principal y Resiliencia
- [ ] Implementar CLI (`src/cli/args.ts` y `src/cli/ui.ts`).
- [ ] Conectar pipeline en `src/index.ts` y punto de entrada `bin/index.js`.
- [ ] Implementar fallback al portapapeles si no se detecta código en pantalla.

## Fase 4: Verificación Integral y Release v0.1.0
- [ ] Ejecución completa de tests (`npm run test`).
- [ ] Build de TypeScript (`npm run build`).
- [ ] Verificación en consola: `node dist/index.js --dry-run`.
- [ ] Publicación del release v0.1.0 en GitHub vía MCP.
