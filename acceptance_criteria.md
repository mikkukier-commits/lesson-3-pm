# Acceptance Criteria

## Acceptance Criteria

| ID | Criterion | Verification |
|---|---|---|
| AC-01 | Fat image uses `python:3.13`. | Inspect `Dockerfile.fat` and build output. |
| AC-02 | Slim image uses `python:3.13-slim`. | Inspect `Dockerfile.slim` and build output. |
| AC-03 | Slim image uses a multi-stage build. | Inspect `Dockerfile.slim` for multiple `FROM` stages. |
| AC-04 | Both images build successfully. | Run the documented Docker build commands. |
| AC-05 | Both images run successfully with `docker run`. | Execute the documented run commands. |
| AC-06 | Both variants use the same test input. | Compare the exact test input and command arguments. |
| AC-07 | Inference returns a top-3 prediction. | Execute inference and inspect output. |
| AC-08 | Fat and slim produce matching inference results. | Compare top-3 output for the same input. |
| AC-09 | README contains reproducible build commands. | Review `README.md`. |
| AC-10 | README contains reproducible run commands. | Review `README.md`. |
| AC-11 | `report.md` contains a fat vs. slim comparison. | Review `report.md`. |
| AC-12 | Slim image does not contain unnecessary files. | Inspect image contents/build stages. |
| AC-13 | `.dockerignore` exists and excludes unnecessary build context. | Review `.dockerignore`. |
| AC-14 | Dependency versions are fixed. | Review `requirements.txt`. |
| AC-15 | Model artifact and inference/preprocessing are identical between variants. | Review Dockerfiles and application inputs. |

## Definition of Done

The task is considered done when any team member can clone the repository, follow the commands in `README.md`, build both the fat and slim images, run inference against the same input, and observe matching prediction results.

In addition, the repository must contain the required PM-review evidence and the comparison report.

## Blocking Conditions

The task should not be considered ready for staging if:

- either image cannot be built or run;
- the inference result differs between fat and slim without an approved explanation;
- the model artifact is not identifiable/versioned;
- dependencies are not reproducibly defined;
- required build/run instructions are missing;
- production secrets or production infrastructure are exposed through local configuration.
