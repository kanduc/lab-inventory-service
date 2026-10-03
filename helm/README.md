# Helm chart: inventory-service

This chart deploys `inventory-service` independently.

## Expected image

```text
<AWS_ACCOUNT_ID>.dkr.ecr.<REGION>.amazonaws.com/inventory-service:<GIT_SHA>
```

## Local validation

```bash
helm lint ./helm
helm template inventory-service ./helm \
  --set image.repository=example/inventory-service \
  --set image.tag=dev
```

## Notes

- RollingUpdate: `maxUnavailable=0`, `maxSurge=1`.
- Readiness/liveness probes are enabled by default.
- HPA is disabled by default.
- Adjust `values.yaml` if the application uses another port or health endpoint.
