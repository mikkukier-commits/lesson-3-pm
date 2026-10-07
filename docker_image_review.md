# Docker Image Review

## 1. Dockerfile

| Check | Expected | Status | Evidence / Comment |
|---|---|---|---|
| Separate `Dockerfile.fat` | Present | TBD | Inspect repository |
| Separate `Dockerfile.slim` | Present | TBD | Inspect repository |
| Fat base image | `python:3.13` | TBD | Inspect `Dockerfile.fat` |
| Slim base image | `python:3.13-slim` | TBD | Inspect `Dockerfile.slim` |
| Slim multi-stage build | Multiple build/runtime stages | TBD | Inspect `Dockerfile.slim` |
| Logical `COPY` order | Dependencies and application copied appropriately | TBD | Review Dockerfile |
| `.dockerignore` | Present and useful | TBD | Inspect repository |

## 2. Dependencies

| Check | Expected | Status | Evidence / Comment |
|---|---|---|---|
| `requirements.txt` exists | Yes | TBD | Inspect repository |
| Versions are fixed | Explicit versions | TBD | Inspect file |
| Python 3.13 compatibility | Confirmed | TBD | Team evidence required |
| No unnecessary libraries | Runtime dependencies only where appropriate | TBD | Review dependency list |
| No development-only dependencies in runtime image | Confirmed | TBD | Review build stages |

## 3. Inference Execution

| Check | Expected | Status | Evidence / Comment |
|---|---|---|---|
| Fat image builds | Successful build | Supported by provided measurement | Build time: ~20 min |
| Slim image builds | Successful build | Supported by provided measurement | Build time: ~7 min |
| Fat image runs | Successful `docker run` | TBD | Run documented command |
| Slim image runs | Successful `docker run` | TBD | Run documented command |
| Test input can be supplied | Documented mechanism | TBD | Review README |
| Top-3 prediction returned | Yes | TBD | Capture output |
| README documents commands | Yes | TBD | Review README |

## 4. Reproducibility

| Check | Expected | Status | Evidence / Comment |
|---|---|---|---|
| Same model artifact | `model/model.pt` | TBD | Verify checksum/path |
| Same preprocessing | Identical behavior | TBD | Review inference implementation |
| Same test input | Exact same input | TBD | Record test input |
| Same inference result | Fat = Slim | TBD | Compare outputs |
| Model version/source documented | Yes | TBD | Review README/report |

## PM Decision

**Current status: Not enough evidence for staging approval.**

This is not a statement that the implementation is incorrect. The available brief does not contain execution evidence for the Docker builds, inference outputs, image metrics or security checks. These must be collected before making a staging-readiness decision.
