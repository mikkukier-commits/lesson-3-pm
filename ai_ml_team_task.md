# Containerize ML Inference: Fat and Slim Docker Images

## Background

The AI/ML team has an image-classification model based on a pretrained `torchvision.models` model. The goal is to package the inference application into two reproducible Docker images and verify that optimization does not change model behavior.

## Scope

The team must:

- build a baseline fat image;
- build an optimized slim image;
- use the required Python base images;
- use multi-stage build for the slim image;
- package the required model and inference artifacts;
- document build and run commands;
- validate inference using the same test input;
- compare the two images;
- provide evidence that the optimized image preserves inference behavior.

## Out of Scope

The following are explicitly outside this task:

- model retraining;
- improving model accuracy;
- production Kubernetes deployment;
- full production monitoring.

## Expected Deliverables

1. `Dockerfile.fat`
2. `Dockerfile.slim`
3. `.dockerignore`
4. `requirements.txt` with fixed dependency versions
5. `model/model.pt`
6. `app/inference.py`
7. `README.md` with build/run commands
8. `report.md` comparing fat and slim images
9. Docker images:
   - `ml-infer-fat:1.0`
   - `ml-infer-slim:1.0`

## Technical Constraints

- Fat image base: `python:3.13`
- Slim image base: `python:3.13-slim`
- Slim image must use a multi-stage build.
- Both images must use the same model artifact.
- Both images must use the same inference logic and preprocessing.
- `requirements.txt` versions must be explicitly fixed.
- `.dockerignore` must be present.
- The inference behavior must be validated with the same test input.
- Both images must expose a documented way to run inference.
- README must contain reproducible build and run instructions.

## Acceptance Criteria Summary

The task is accepted when both images build and run successfully, inference can be executed with the same test input, and the top-3 prediction results match between fat and slim.

The repository must also contain the required Dockerfiles, dependency lock information, `.dockerignore`, README and comparison report.

## Evidence Required from the Team

Please provide:

- successful build output for both images;
- successful inference output for both images;
- the exact test input used;
- image sizes;
- layer counts or image history;
- build times;
- startup/run observations;
- security scan findings, if a scanner is available;
- confirmation of model artifact version/source.
