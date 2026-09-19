# Test plan

Pre-deploy, in CI, on the release commit:

- Unit and integration suites must pass.
- Dependency and secret scans must report no new high or critical findings.
- Lint must report no errors.

Post-deploy, against the target environment:

- The health endpoint returns 200 and reports the expected release version.
- An authentication smoke test completes an end to end login.
- Two synthetic business transactions succeed.
- Error rate and p95 latency are compared against the fifteen minute pre-deploy baseline.

The pipeline posts the evidence from both phases back to this change record, so the reviewer reads the actual results rather than a claim that testing happened.
