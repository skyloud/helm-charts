# AWS Security Group Binding

This chart create a `SecurityGroupBinding` custom resource definition (CRD) that allows to bind an AWS security group to a Kubernetes namespace.

To have more information about the `SecurityGroupBinding` CRD, please refer to the [official documentation](https://docs.aws.amazon.com/eks/latest/userguide/security-groups-for-pods.html)

## How to use

```hcl
resource "helm_release" "aws_security_group_binding" {
  name       = "aws-security-group-binding"
  namespace  = "your-namespace"
  repository = "https://skyloud.github.io/helm-charts"
  chart      = "aws-security-group-binding"
  version    = "0.1.0"
  values = [
    yamlencode({
      "namespace" = "default"
      podSelector = {
        matchLabels = {
            app = "my-app"
        }
      }
      securityGroups = {
        groupIds = ["sg-1234567890abcdef0"]
      }
    })
  ]
}
```
