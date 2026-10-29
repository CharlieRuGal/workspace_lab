# UNA Chat

Proyecto de chat continuado desde el Laboratorio 5. Esta nota guarda solo hechos comprobados.

Created 2026-10-28. Last reinforced 2026-10-29.

## Current status

2026-10-29: publicado en GitHub. Commit `15dadce` en `main`, igual a `origin/main`. Mensaje: «Integrar Laboratorio 5 y UNA Chat con autenticacion Google». US-01 funciona en local con Auth0 y Google. El punto 3 (harness) no se hizo. No hay despliegue en Vercel comprobado.

## Previous status

2026-10-28: el código vivía en un repositorio Git independiente y US-01 todavía no estaba implementada. El punto 3 de la guía (harness) no se haría.

## Hechos comprobados

- Repositorio local: `C:\LAB6_Paradigmas\workspace_lab\REPOS\Lab5-Paradigmas`.
- Remoto: `https://github.com/CharlieRuGal/Lab5-Paradigmas.git`, rama `main`.
- `HEAD` y `origin/main` están en `15dadce540c61bae28aa3bc8a48d6ba5d414f022`.
- El workspace no versiona ese código. `.gitignore` excluye `REPOS/*` y deja versionado solo `REPOS/AGENTS.md`.
- `antes/` es el chat original del Laboratorio 5, sin Auth0. `despues/` es UNA Chat.
- Sin sesión, `GET /` entrega `welcome.html`. El botón «Continuar con Google» es un enlace a `/login`. Auth0 usa la conexión `google-oauth2`.
- Con sesión, `GET /` entrega `index.html`. `/profile` devuelve el nombre y `GET /logout` cierra la sesión.
- Socket.IO rechaza la conexión si no hay sesión. El nombre publicado es el de la sesión.
- `libs/unalib.js` clasifica cada mensaje como `text`, `image` o `youtube` y no devuelve HTML. El cliente pinta el texto con `textContent`.
- URL local: `http://localhost:3000`. Callback de Auth0: `http://localhost:3000/callback`. Cierre de sesión y origen permitidos: `http://localhost:3000`.
- Las credenciales viven en `despues/.env`, que el repositorio de UNA Chat no versiona. La plantilla sin valores es `despues/.env.example`, con las variables `PORT`, `BASE_URL`, `CLIENT_ID`, `ISSUER_BASE_URL` y `SECRET`.
- Carlos confirmó que las 42 pruebas automatizadas pasaron. El desglose de la corrida previa al commit fue 34 Mocha, 4 Jest y 4 Playwright. Las de navegador usaron el Chrome instalado. No usan credenciales reales de Google.
- El `README.md` de `despues/` todavía dice que `npm test` no cubre el login. En el mismo commit, las pruebas de integración y e2e sí cubren la bienvenida y el rechazo del socket.

## Dónde no está la información

No hay en esta nota valores de Auth0 ni una URL de Vercel. El hueco del despliegue sigue en [[Gaps]].
