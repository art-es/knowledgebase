# Deployment

## Contents:

- [Build docker image](#build-docker-image)
- [Push docker image](#push-docker-image)
- [Update manifests](#update-manifests)
- [Confirm Context](#confirm-context)
- [Running deploy process](#running-deploy-process)

## Build docker image

```shell
docker build -t <REGISTRY>/<NAME>:<VERSION> .
```

_example setup the image for Google Cloud Registry_
```shell
docker build -t gcr.io/art-es/example:1.0.1 .
```

[More about `docker build`](https://docs.docker.com/engine/reference/commandline/build/)

## Push docker image

```shell
docker push <REGISTRY>/<NAME>:<VERSION>
```

[More about `docker push`](https://docs.docker.com/engine/reference/commandline/push/)

## Update manifests

You need to update the `deployment.yaml` manifest of service which you want to update

YAML path: `spec.template.spec.containers[X].image`

Example:
```yaml
...
spec:
  template:
    spec:
      serviceAccountName: gke-workload
      containers:
        - name: example-service
          image: gcr.io/art-es/example:1.0.1
```

## Confirm Context

This is an important step!  
Please run the command [`kubectl config get-contexts`](../kubectl/README.md#list-of-contexts) and make sure about your current context is right one :)

## Running deploy process

For this step you need 2 different commands:
- [`kustomize` command to combine all manifest files into one](../kustomize/README.md#combine-all-manifest-files-into-one)
- [`kubectl` command to sending changes to Kubernetes cluster](../kubectl/README.md#kubectl-apply)

Execute it as a single command
```shell
kustomize build <MANIFESTS_DIR> | kubectl apply -f -
```


[⬅️ Back](../README.md)
