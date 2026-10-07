# Risk Register

| Risk | Probability | Impact | Mitigation | Owner |
|---|---|---|---|---|
| Image works locally but is not ready for staging | Medium | High | Define and execute staging-readiness checks before promotion | AI PM |
| Slim image produces a different prediction than fat | Medium | High | Run both images against identical input and compare top-3 output | AI/ML Engineer + QA |
| Python, torch or torchvision version incompatibility | Medium | High | Validate dependency compatibility with Python 3.13 and both base images | AI/ML Engineer |
| Unnecessary files enter the Docker build context | Medium | Medium | Review and maintain `.dockerignore`; inspect build context | AI/ML Engineer / DevOps |
| README does not contain reproducible commands | Medium | Medium | Add and test exact build/run commands before acceptance | AI PM + AI/ML Engineer |
| Fat vs. slim comparison is incomplete | Medium | Medium | Require `report.md` with agreed metrics and evidence | AI PM |
| Production secrets enter Docker Compose configuration | Low | Critical | Use non-production configuration and externalized local secrets; perform security review | DevOps |
| Local environment connects to production DB/queue/Redis | Low | Critical | Explicitly verify endpoints and credentials are local-only | DevOps |
| Model artifact is not versioned or identifiable | Medium | High | Record model version/source and artifact checksum where applicable | AI/ML Engineer |
| Image remains too large for efficient delivery | Medium | Medium | Measure image size and identify large layers; optimize only with inference regression testing | AI/ML Engineer / DevOps |
| Runtime image contains development-only dependencies | Medium | Medium | Separate build/runtime concerns and review final image dependencies | AI/ML Engineer |
| Inference test uses different preprocessing between variants | Low | High | Verify shared preprocessing and exact test input | AI/ML Engineer + QA |

## Risk Prioritization

The highest-priority risks are those that can invalidate the delivery decision:

1. Different inference between fat and slim.
2. Production infrastructure or secrets exposed through local configuration.
3. Unknown/incompatible dependency versions.
4. Unidentifiable model artifact.
5. Missing evidence for staging readiness.
