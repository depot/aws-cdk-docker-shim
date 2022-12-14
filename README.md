# aws-cdk-docker-shim

This is a workaround for AWS CKD - CDK calls a binary named `docker` to build Docker images. The `shim/docker` script in this repo proxies the `docker build` command to `depot build`, and everything else to `docker`.

You would want to set `PATH` to find this script first when running CDK:

```bash
env PATH="$(pwd)/shim:$PATH" cdk ...
```

This assumes that you've moved the `shim` directory to the same directory as your `cdk` app.

You would also either need to have a `depot.json` file in your local directory to configure your Depot project ID, or pass it via the `buildArgs` option to `DockerImageAsset`:

```typescript
new DockerImageAsset(this, "Image", {
  directory: "docker",
  buildArgs: {
    project: "my-project-id",
  },
});
```
