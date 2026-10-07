# Lesson 3 PM — ML Docker Delivery Review

## Purpose

This repository contains the AI Project Manager package for reviewing the containerization and delivery readiness of an ML image-classification inference solution.

The PM does not implement the Bash scripts, Dockerfiles or inference code. The purpose is to define the work, verify delivery artifacts, evaluate evidence and identify risks.

## Project Context

The technical team is preparing:

- `ml-infer-fat:1.0` based on `python:3.13`
- `ml-infer-slim:1.0` based on `python:3.13-slim`

The slim image must use a multi-stage build and must preserve the inference behavior of the fat image.

## PM Artifacts

| File | Purpose |
|---|---|
| `project_brief.md` | Defines business and technical context |
| `ai_ml_team_task.md` | Converts the context into an executable technical task |
| `acceptance_criteria.md` | Defines measurable acceptance conditions |
| `docker_image_review.md` | Provides a PM checklist for Docker and inference review |
| `optimization_report_review.md` | Defines the fat vs. slim evidence review |
| `compose_readiness_checklist.md` | Checks local integrated environment readiness |
| `risk_register.md` | Tracks delivery risks and mitigations |
| `stakeholder_summary.md` | Translates technical status into management language |
| `README.md` | Provides navigation and questions for the technical team |

## Recommended Review Order

1. `project_brief.md`
2. `ai_ml_team_task.md`
3. `acceptance_criteria.md`
4. `docker_image_review.md`
5. `optimization_report_review.md`
6. `compose_readiness_checklist.md`
7. `risk_register.md`
8. `stakeholder_summary.md`
9. `README.md`

## Questions to AI/ML Team

- What is the final model artifact being used?
- What is the model artifact version?
- What is the source of the pretrained model?
- What input format is expected?
- What output format is expected?
- Is compatibility with `python:3.13` confirmed?
- Is compatibility with `python:3.13-slim` confirmed?
- Are `torch`, `torchvision` and `pillow` compatible with the selected Python version?
- Are dependency versions fixed in `requirements.txt`?
- Is `.dockerignore` present and reviewed?
- Does slim use a multi-stage build?
- Does inference match between fat and slim?
- What exact test input was used?
- What are the top-3 prediction results for each image?
- What are the image sizes?
- How many layers does each image have?
- What are the build times?
- What are the startup/run times under the agreed test procedure?
- What security findings were identified?
- Does `report.md` contain the fat vs. slim comparison?
- Does README contain tested build/run commands?
- Is Docker Compose required for the local integrated stand?
- Does the Compose configuration contain any production secrets?
- Does the local environment connect only to non-production services?

## Known Verification Commands

Image size:

```bash
docker images | grep ml-infer
```

Image history/layers:

```bash
docker history ml-infer:fat
docker history ml-infer:slim
```

Local Compose startup:

```bash
docker compose up --build
```

The exact inference build/run commands are intentionally not invented here. They must come from the technical implementation and be documented in the project's README.

## Evidence Rule

`TBD` in the review documents means that the required evidence has not been supplied yet. It is not an approval or rejection of the technical implementation.

A staging-readiness decision should only be made after the required evidence has been collected and acceptance criteria have been verified.
