# Docker Compose Readiness Checklist

## Target Local System

The local environment is expected to include:

- `model-api`
- model service or model runtime
- Redis
- PostgreSQL
- monitoring

## Checklist

| Check | Expected | Status | Evidence / Comment |
|---|---|---|---|
| `compose.yaml` exists | Yes | TBD | Inspect repository |
| `model-api` is defined | Yes | TBD | Inspect Compose file |
| Model service/runtime is defined | Yes | TBD | Inspect Compose file |
| Redis is defined | Yes | TBD | Inspect Compose file |
| PostgreSQL is defined | Yes | TBD | Inspect Compose file |
| Monitoring is defined | Yes | TBD | Inspect Compose file |
| Services start without manual intervention | Yes | TBD | Run Compose |
| Port is correctly configured | Documented and reachable | TBD | Test endpoint |
| Health endpoint exists | Yes | TBD | Call endpoint |
| Predict endpoint exists | Yes | TBD | Call endpoint |
| Configuration is externalized | `.env` or equivalent | TBD | Inspect configuration |
| No production secrets in Compose | Confirmed | TBD | Security review |
| No production DB/Redis/queue connection | Confirmed | TBD | Inspect environment/config |
| README documents Compose command | `docker compose up --build` | TBD | Review README |
| Test prediction works after startup | Yes | TBD | Execute test |

## Readiness Test

The local stand should be considered ready when all required services start through one documented command and a test prediction can be executed without manual service startup.

Expected command:

```bash
docker compose up --build
```

The exact endpoint, port and test request must be confirmed by the technical team if they are not already documented.

## PM Gate

A local image working by itself does not prove that the complete system is ready for integration or staging. The Compose checklist verifies service integration, configuration boundaries and basic end-to-end usability.
