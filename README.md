# Azure tagging
[![Changelog](https://img.shields.io/badge/changelog-release-green.svg)](CHANGELOG.md) [![Notice](https://img.shields.io/badge/notice-copyright-yellow.svg)](NOTICE) [![Apache V2 License](https://img.shields.io/badge/license-Apache%20V2-orange.svg)](LICENSE) [![TF Registry](https://img.shields.io/badge/terraform-registry-blue.svg)](https://registry.terraform.io/modules/claranet/tagging/azurerm/)


This Terraform helper allows to merge or overwrite tags on a resource.

## Requirements

  * [AzureRM Terraform provider](https://www.terraform.io/docs/providers/azurerm/) >= 1.38.0

## Terraform version compatibility

| Module version | Terraform version |
|----------------|-------------------|
| >= 2.x.x       | 0.12.x            |
| < 2.x.x        | 0.11.x            |


## Usage

You can use this module by including it this way:
```
module "myresource_tagging" {
  source  = "claranet/tagging/azurerm"
  version = "x.x.x"

  resource_id = var.myresource_id
  behavior    = "merge"   # Must be "merge" or "overwrite"
  
  tags = {
    "foo"        = "bar",
    "monitoring" = "true"
  }
}
```

## Inputs

| Name | Description | Type | Default | Required |
|------|-------------|:----:|:-----:|:-----:|
| behavior | Behavior for tags applying. Must be `merge` or `overwrite`. | string | `"merge"` | no |
| force | True to apply every time | bool | `false` | no |
| nb\_resources | Number of resources to tag | number | `1` | no |
| resource\_ids | Id of the Azure resource to tag | list(string) | n/a | yes |
| tags | Tags to apply on resource | map(string) | n/a | yes |


## Related documentation

Terraform null_resource documentation: [terraform.io/docs/provisioners/null_resource.html](https://www.terraform.io/docs/provisioners/null_resource.html)
Terraform local_exec documentation: [terraform.io/docs/provisioners/local-exec.html](https://www.terraform.io/docs/provisioners/local-exec.html)
Microsoft Azure tagging documentation: [docs.microsoft.com/fr-fr/azure/azure-resource-manager/resource-group-using-tags](https://docs.microsoft.com/fr-fr/azure/azure-resource-manager/resource-group-using-tags)