# AWS EBS Storage Classes Helm Chart

This chart create a `StorageClass` for AWS EBS volumes with the following features:
* `gp3` with default settings as the default storage class
* `io1` for high performance volumes

## How to use

```hcl
resource "helm_release" "aws_ebs_storage_classes" {
  name       = "aws-ebs-storage-classes"
  namespace  = "kube-system"
  repository = "https://skyloud.github.io/helm-charts"
  chart      = "aws-ebs-storage-classes"
  
  values = [
    yamlencode({
      storageClasses: {
        gp3: {
          default: true
        },
        io1: {
          default: false,
          parameters: {
            iopsPerGB: 10,
          }
        }
      }
    })
  ]
}
```
