# Project Brief

## Project Context

The AI/ML team has prepared an image-classification model and needs to package its inference environment into reproducible Docker images.

The project uses a pretrained model from `torchvision.models` together with the following artifacts:

- `model/model.pt` — model artifact
- `app/inference.py` — inference application
- `requirements.txt` — Python dependencies
- `Dockerfile.fat` — baseline Docker image definition
- `Dockerfile.slim` — optimized Docker image definition
- `.dockerignore` — build-context exclusions
- `README.md` — build and run instructions
- `report.md` — comparison of the two images

## Business / Delivery Goal

The goal is to make the ML inference component reproducible and easy to validate across environments. Docker images are treated as delivery artifacts because they package the runtime, dependencies and application in a form that can be built, tested and promoted to another environment.

## Two Image Variants

The team will provide two variants:

- `ml-infer-fat:1.0` — a simple baseline image based on `python:3.13`, intended for the first validation.
- `ml-infer-slim:1.0` — an optimized image based on `python:3.13-slim`, using a multi-stage build.

The slim variant is expected to reduce image footprint while preserving the same inference behavior as the fat image.

## Success Conditions

Optimization must not change the inference result. Both images must be buildable and runnable, accept the same test input, and produce the same top-3 prediction result.

The solution should be suitable for verification locally and, after the required evidence is collected, in CI/CD or staging.

## AI PM Responsibility

The AI Project Manager is not expected to write the Bash script, Dockerfiles or inference code. The PM responsibility is to:

1. define the expected delivery;
2. make requirements and acceptance criteria explicit;
3. review delivery artifacts;
4. request evidence for technical claims;
5. identify delivery risks;
6. assess readiness for the next environment.

## Current Evidence Status

Technical measurements such as image size, build time, startup time, security findings and layer count are not provided in the project brief. These values must be supplied by the technical team or measured using the commands defined in the review documents.
