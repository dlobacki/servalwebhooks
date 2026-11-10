# Backout plan

Back out if any of these hold: canary health checks fail, the error rate exceeds 2 percent for three consecutive minutes, or p95 latency is more than double the pre-deploy baseline.

1. Halt the rollout and drain traffic from any instance already carrying the new release.
2. Redeploy the previous release tag from the registry. Tags are retained for thirty days.
3. Confirm the service reports the previous version and that health checks pass.
4. Record the rollback on this change and leave the change in Review for the change manager.

Backout is expected to complete within ten minutes. No data migration reversal is required for this service.
