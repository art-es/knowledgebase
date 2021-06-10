# kubectl

`kubectl` is a command-line interface that provides the controls for the Kubernetes cluster manager.

- [Official Documentation](https://kubernetes.io/docs/reference/kubectl/kubectl/)
- [Installation](https://kubectl.docs.kubernetes.io/installation/kubectl/)

## Kubectl config

The current context is the environment/cluster you are currently working with

[Official Documentation](https://kubernetes.io/docs/reference/generated/kubectl/kubectl-commands#config)

### List of contexts
```shell
kubectl config get-contexts
```
_the current context will be marked with `*` (asterisk sign)_

### Switch context

From the above command you can get `NAME` of the required context

```shell
kubectl config use-context <NAME>
```

## Kubectl apply

Command for sending changes to Kubernetes cluster

```shell
kubectl apply
```

[⬅️ Back](../README.md)
