# Grafana (LazyCat LPK)

Observability dashboards.

- Upstream: https://github.com/grafana/grafana
- Image: `grafana/grafana:13.2.5` (Docker Hub, mirror mode, digest-matched)
- License: AGPL-3.0 (full text in `content/licenses/LICENSE`)
- Containers: single (bundled SQLite)

## Notes

- Version resolved with the Docker Hub API (`ordering=last_updated`) — the registry
  `tags/list` endpoint caps at 1000 entries. Note 13.2.5 and 13.0.12 both appear in recent
  results, so semver sorting (not list order) picks the newest.
- Admin password comes from a deploy param via `GF_SECURITY_ADMIN_PASSWORD`; username pinned
  to `admin`. No built-in credential.
- `GF_SERVER_ROOT_URL` / `GF_SERVER_DOMAIN` must point at the app's https domain, otherwise
  assets and redirects resolve to the container's internal address behind the proxy.
- Self-signup and analytics/update checks are disabled.
- All state lives in `/lzcapp/var/grafana` (grafana.db, plugins, dashboards).
- No mail service configured.
- Not yet verified on a real device.
