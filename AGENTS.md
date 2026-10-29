# Workspace

> **TL;DR:** Shared AI-powered team workspace — start here, then descend into the `AGENTS.md` of the subdirectory relevant to the current task.

This is a shared team workspace designed so AI agents (GitHub Copilot, Claude Code, Cursor, etc.) can navigate efficiently using **progressive disclosure** — reading only what they need, when they need it.

## Structure

- [Knowledge/](Knowledge/AGENTS.md) — Durable reference material, notes, and facts about projects, systems, and domains.
- [Skills/](Skills/AGENTS.md) — Reusable, task-specific playbooks the agent can invoke for known classes of work.
- [Repos/](Repos/AGENTS.md) — Index of cloned source code repositories. Actual repos are **not** tracked here (see `.gitignore`).
- [Machine/](Machine/AGENTS.md) — This-computer-specific items (startup scripts, local config). **Not** tracked in Git (see `.gitignore`).
- [temp/](temp/AGENTS.md) — Scratch space for transient files, working notes, and intermediate artifacts. Safe to clear at any time.

## How to navigate

Each directory contains its own `AGENTS.md` describing its purpose, conventions, and what to expect inside — read that file before doing deep work in a directory (progressive disclosure). Start here, then descend only into the directory relevant to the current task.

### TL;DR convention

Every `AGENTS.md` starts with a one-line `> **TL;DR:**` blockquote directly under its title. When navigating:

1. Read only the title + TL;DR line first — that's usually enough to decide whether the directory is relevant to the current task.
2. Only read the rest of the file if the TL;DR isn't sufficient (e.g. you need conventions, examples, or the what-belongs/doesn't-belong rules).
3. Do not skip the TL;DR itself — it's the cheapest signal for whether to go deeper.

When adding a new `AGENTS.md`, write its TL;DR last, after the rest of the content is settled, so it accurately compresses the file.

## Getting Started

1. **Clone this repo** to your machine.
2. **Create your personal Knowledge base:** `Knowledge/{YourName}-Brain/` (add it to `.gitignore` if you want it private, or leave it shared).
3. **Link your repos:** Create a junction/symlink at `Repos/` pointing to your local repositories folder, or just use `Repos/AGENTS.md` as an index.
4. **Configure MCP servers:** Edit `.vscode/mcp.json` with the tools this workspace should use.
5. **Add team knowledge:** Document your projects, conventions, and architecture in `Knowledge/`.

## MCP Servers

MCP server configuration lives in [.vscode/mcp.json](.vscode/mcp.json). Add the servers this workspace should use.

## Customization

- **copilot-instructions.md** — Global rules applied to every AI interaction. Edit `.github/copilot-instructions.md` to set team-wide conventions.
- **AGENTS.md in every directory** — Add one to any new folder so agents (and humans) know what it contains.

## Brain

> **TL;DR:** La memoria persistente está en `brain/`. Al empezar cada sesión, leer `brain/daily-log/status.md` y el diario de hoy. Nunca guardar secretos.

Fuente de estas reglas: `obsidian-brain-instructions 1.md`. El mapa es [brain/Home.md](brain/Home.md) y el índice es [brain/INDEX.md](brain/INDEX.md).

### Al empezar

1. Leer `brain/daily-log/status.md` y, si existe, el diario de hoy `brain/daily-log/YYYY-MM-DD.md` (zona `America/Costa_Rica`, UTC-6).
2. Leer `brain/INDEX.md` y abrir solo las notas que correspondan a la tarea. Seguir los `[[wikilinks]]` desde ahí.
3. Aplicar [brain/Working/How I work.md](brain/Working/How%20I%20work.md).

### Durante la sesión

- Después de cada paso real (decisión, cambio terminado, bloqueo o dato comprobado), añadir una viñeta al diario de hoy: `- HH:MM UTC-6: qué pasó y qué sigue`.
- Si el owner corrige o fija una preferencia, anotarla en ese momento en `brain/Working/How I work.md`, con la fecha.
- No reescribir ni reordenar viñetas ya escritas en el diario. Solo agregar.

### Al cerrar

1. Guardar cada hallazgo durable en su nota. Ver la tabla de abajo.
2. Reescribir `brain/daily-log/status.md` para que describa el presente: foco, pendientes y en quién se espera. Sustituir lo viejo; no acumular historial ahí.
3. Si se crea una nota, añadir su fila en `brain/INDEX.md` y su enlace en `brain/Home.md`.

### Dónde va cada cosa

| Qué pasó | Dónde se actualiza |
|---|---|
| Trabajo o aprendizaje de la sesión | Diario de hoy y `brain/daily-log/status.md` |
| Un hecho nuevo del sistema o del dominio | La nota del tema, o una nota nueva más fila en `INDEX.md` y enlace en `Home.md` |
| Estado de un proyecto | Esa nota: «Current status» fechado arriba y el anterior pasa a «Previous status» |
| Preferencia o corrección | `brain/Working/How I work.md` |
| Ruta, remoto o entorno | `brain/Working/Environments.md` |
| Algo que no se sabe | `brain/Working/Gaps.md` |
| Un hueco que ya se resolvió | Se borra su línea en `Gaps.md` |
| Un hecho que resultó falso | Se corrige en la nota. No se deja la versión vieja. |

No guardar secretos en `brain/`: contraseñas, tokens, claves ni cadenas de conexión. Decir solo dónde vive el secreto. Commit y push de estas notas solo cuando el owner lo pida. No versionar `brain/.obsidian/workspace.json`.
