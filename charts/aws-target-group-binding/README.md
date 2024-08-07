# AWS Target Group Binding

This chart create a `TargetGroupBinding` custom resource definition (CRD) that allows to bind an AWS target group to a Kubernetes namespace.

To have more information about the `TargetGroupBinding` CRD, please refer to the [official documentation](https://kubernetes-sigs.github.io/aws-load-balancer-controller/v2.5/guide/targetgroupbinding/targetgroupbinding/)

## How to use

```hcl
resource "helm_release" "aws_target_group_binding" {
  name       = "aws-target-group-binding"
  namespace  = "your-namespace"
  repository = "https://skyloud.github.io/helm-charts"
  chart      = "aws-target-group-binding"
  version    = "0.1.0"
  values = [
    yamlencode({
      "namespace" = "default"
      "service" = {
        "name" = "my-service"
        "port" = 80
      }
      "aws" = {
        "targetGroupARN" = "arn:aws:elasticloadbalancing:eu-west-1:123456789012:targetgroup/my-target-group/1234567890abcdef0"
        "targetType" = "ip"
      }
    })
  ]
}
```

### Notes on the targetType

The `targetType` field can be either `ip` or `instance`. The default value is `ip`. `ip` is the recommended value for most use cases. If you need to use `instance`, please refer to the [official documentation](https://kubernetes-sigs.github.io/aws-load-balancer-controller/v2.5/guide/targetgroupbinding/targetgroupbinding/#targettype) for more information.

`ip` target the traffic to the Kubernetes Endpoints registered for the Service in Kubernetes. It can be used with any type of Service.

`instance` target the traffic to the Kubernetes Nodes where the Pods are running. It can only be used with a Service of type `NodePort`.
