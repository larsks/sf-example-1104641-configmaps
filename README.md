# ConfigMap demo

This demonstration repository accompanies https://serverfault.com/a/1104670/27515.

## Deploying

To deploy three examples into your current namespace, run:

```
kubectl apply -k .
```

This will create three `Deployments`:

```
$ kubectl get deployment
NAME        READY   UP-TO-DATE   AVAILABLE   AGE
example-3   1/1     1            1           110s
example-2   1/1     1            1           110s
example-1   1/1     1            1           110s
```

Which will result in three corresponding pods:

```
$ kubectl get pods
NAME                         READY   STATUS    RESTARTS   AGE
example-3-74b6fbdf7c-78wq5   1/1     Running   0          2m12s
example-2-645bc67d69-zc7dc   1/1     Running   0          2m12s
example-1-6fb8b6dcf8-pts6c   1/1     Running   0          2m12s
```

## Looking at the manifests

You can generate the manifests without deploying them by installing the [kustomize][] command and running:

```
$ kustomize build > manifests.yaml
```

[kustomize]: https://kustomize.io/

## About the examples

- [Example 1](example1) -- This shows how to expose all the keys from a `ConfigMap` in a directory inside a container.
- [Example 2](example2) -- This shows how to expose a subset of the keys from a `ConfigMap` in a directory inside a container.
- [Example 3](example3) -- This shows how to expose a single key from a `ConfigMap` at an arbitrary path inside a container.
