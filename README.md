# aws-cdk-depot-shim

This is a workaround for using AWS CDK with Depot. The `depot-cdk` script in this repo proxies the `build` command to `depot build` with `--load` specified, and everything else to `docker`.

You would want to set `CDK_DOCKER` environment variable to the path of the `depot-cdk` script when running CDK:

```bash
env CDK_DOCKER=/path/to/depot-cdk cdk ...
```
