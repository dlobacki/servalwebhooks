# Implementation plan

1. CI builds the release artifact from the tagged commit and publishes it to the internal registry.
2. The deployment runs first against a single canary instance behind the load balancer and holds there for five minutes.
3. Health checks and synthetic transactions must pass on the canary before the rollout continues.
4. The remaining instances roll in two batches with a two minute soak between them.
5. Post-deploy verification runs the smoke suite against the public endpoint and the results are posted back to this change.

The deploying engineer named on this change owns the execution. Expected duration is under fifteen minutes end to end, with no database migration for this service.
