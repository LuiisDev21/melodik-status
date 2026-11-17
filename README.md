# Estado de Melodik

Monitorización y página pública de estado de [Melodik](https://melodik.es), hecha con
[Upptime](https://upptime.js.org): GitHub Actions comprueba los servicios cada 5 minutos,
GitHub Issues guarda los incidentes y GitHub Pages publica la página en
**https://status.melodik.es**.

Este README lo regenera Upptime a partir de `.upptimerc.yml`; la documentación de operación
(alta de servicios, incidentes, mantenimientos y diseño) vive en el repositorio de la app:
`docs/status-page.md`.

## Servicios vigilados

| Servicio | Qué comprueba |
| --- | --- |
| Melodik (web) | Que la portada responda. |
| API | `/api/health` con `status` `ok` o `degraded`. |
| Base de datos | `/api/health/ready`, que hace una consulta real a Postgres. |
| Inicio de sesión | `/auth/v1/health` de Supabase Auth. |
| Deezer | Que el catálogo responda (audio y portadas). |

## Cómo se opera

- **Caída automática**: Upptime abre un issue, lo asigna y lo cierra solo cuando el servicio vuelve.
- **Incidente manual**: crea un issue con el título del servicio y la etiqueta `status`.
- **Mantenimiento**: issue con la etiqueta `maintenance` y la fecha en el cuerpo.
- **Progreso**: comenta en el issue; cada comentario se publica en la página.

No edites los workflows a mano: se regeneran desde `.upptimerc.yml`.
