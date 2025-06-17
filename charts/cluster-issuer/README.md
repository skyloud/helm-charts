# Ingress Chart

## TL;DR;

```console
$ helm repo add sky-charts https://skyloud.github.io/helm-charts
$ helm install my-release sky-charts/ingress
```

## Introduction

Helm charts are great! They are really configurable and let you build complicated software stacks in seconds. Tools like [Helmfile](https://github.com/roboll/helmfile) combine helm charts together to allow you to set up an environment consisting entirely of helm releases. 

Let's say, though, you want to add additional code to a third party helm chart. You could make a new chart with your K8s API resource and the third party chart as a dependency, but that requires maintenance which might not be worth it if you only needed a single additional resource created. That's where k8s-as-helm charts come in. These charts wrap a single Kubernetes resource in a helm chart with all the key parameters exposed. 

The ingress chart deploys a single Kubernetes Ingress object. 

## Installation 

```console
$ helm repo add sky-charts https://skyloud.github.io/helm-charts
$ helm install my-release sky-charts/ingress
```

## Configuration

The following table lists the configurable parameters of the ingress chart and their default values.

Parameter | Description | Default
--- | --- | ---
`nameOverride` | override name of the chart component | .Release.Name
`apiVersion` | api version of k8s object | `"v1"`
`annotations` | annotations in yaml map format to be added to the object | `null`
`labels` | labels to add to Ingress object | `null`
`ingressClassName` | IngressClass represents the class of the Ingress | `null`
`hosts` | yaml list representing the `host` list entries for the Ingress object | `null`
`hosts[].url` | URL of host list entry | `null`
`hosts[].protocol` | the protocol of the host | `http`
`hosts[].path` | the path k8s yaml object containing the contents of the `path` field for the ingress | `null`
`tls` | the list of TLS block entries for the ingress object | `null`

## Example Configuration

For some examples of values used to configure this chart, see [the ci/example values for this chart](./ci/ci-values.yaml)

Forked from https://github.com/ameijer/k8s-as-helm
