# Terraform Remote State GCP
A terraform module to setup remote state backend on Cloud Storage


## Usage

```hcl
#------------------------------
# Remote State Locking
#------------------------------
module "remote_state" {
  source              = "../modules/remote-state-gcp"
  name_prefix         = "${var.project_name}-tfstate-${var.environment}"
  location            = var.region
  project_id          = var.project_id
  backend_output_path = "${path.module}/backend.tf"

  labels = local.common_labels
}

```

## Contributing

Report issues/questions/feature requests on in the issues section.

Full contributing guidelines are covered [here](CONTRIBUTING.md).

<!-- BEGINNING OF PRE-COMMIT-TERRAFORM DOCS HOOK -->
## Requirements

| Name | Version |
|------|---------|
| terraform | >= 0.12 |
| google | >= 3.29 |
| local | >= 1.2 |
| null | >= 2.1 |
| random | >= 2.1 |
| template | >= 2.1 |

## Providers

| Name | Version |
|------|---------|
| google | >= 3.29 |
| local | >= 1.2 |
| random | >= 2.1 |
| template | >= 2.1 |

## Inputs

| Name | Description | Type | Default | Required |
|------|-------------|------|---------|:--------:|
| backend\_output\_path | The default file to output backend configuration to | `string` | `"./backend.tf"` | no |
| bucket\_name | (Optional) the name of the bucket | `any` | `null` | no |
| enable\_versioning | Enable Bucket versioning | `bool` | `true` | no |
| force\_destroy | Whether to force destroy the bucket and all it's contents | `bool` | `false` | no |
| labels | A set of key/value label pairs to assign to the bucket. | `any` | `null` | no |
| location | The location of resource group | `string` | `"US-EAST1"` | no |
| name\_prefix | The prefix for all created resources | `string` | `"tfstate"` | no |
| prefix | The name of the Blob used to retrieve/store Terraform's State file inside the Storage Container. | `string` | `"global/terrform.tfstate"` | no |
| project\_id | The ID of the project in which the resource belongs. If it is not provided, the provider project is used. | `any` | `null` | no |

## Outputs

| Name | Description |
|------|-------------|
| bucket\_name | Name of created bucket |
| bucket\_url | The base URL of the bucket, in the format gs://<bucket-name> |
| prefix | GCS Prefix inside the bucket |

<!-- END OF PRE-COMMIT-TERRAFORM DOCS HOOK -->
