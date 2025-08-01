---
title: SFR3 - Deployment/Usage Telemetry
description: Module Specification for the Azure Verified Modules (AVM) program
url: /spec/SFR3
type: default
tags: [
  Class-Resource, # MULTIPLE VALUES: this can be "Class-Resource" AND/OR "Class-Pattern" AND/OR "Class-Utility"
  Class-Pattern, # MULTIPLE VALUES: this can be "Class-Resource" AND/OR "Class-Pattern" AND/OR "Class-Utility"
  Type-Functional, # SINGLE VALUE: this can be "Type-Functional" OR "Type-NonFunctional"
  Category-Telemetry, # SINGLE VALUE: this can be "Category-Testing" OR "Category-Telemetry" OR "Category-Contribution/Support" OR "Category-Documentation" OR "Category-CodeStyle" OR "Category-Naming/Composition" OR "Category-Inputs/Outputs" OR "Category-Release/Publishing"
  Language-Bicep, # MULTIPLE VALUES: this can be "Language-Bicep" AND/OR "Language-Terraform"
  Language-Terraform, # MULTIPLE VALUES: this can be "Language-Bicep" AND/OR "Language-Terraform"
  Severity-MUST, # SINGLE VALUE: this can be "Severity-MUST" OR "Severity-SHOULD" OR "Severity-MAY"
  Persona-Owner, # MULTIPLE VALUES: this can be "Persona-Owner" AND/OR "Persona-Contributor"
  Lifecycle-Initial, # SINGLE VALUE: this can be "Lifecycle-Initial" OR "Lifecycle-BAU" OR "Lifecycle-EOL"
  Validation-TBD # SINGLE VALUE (PER LANGUAGE): for Bicep, this can be "Validation-BCP/Manual" OR "Validation-BCP/CI/Informational" OR "Validation-BCP/CI/Enforced" and for Terraform, this can be "Validation-TF/Manual" OR "Validation-TF/CI/Informational" OR "Validation-TF/CI/Enforced"
]
priority: 30
---

## ID: SFR3 - Category: Telemetry - Deployment/Usage Telemetry

{{% notice style="important" %}}

We will maintain a set of CSV files in the [AVM Central Repo (`Azure/Azure-Verified-Modules`)](https://github.com/zojovano/azure-verified-modules-copy/tree/main/docs/static/module-indexes) with the required TelemetryId prefixes to enable checks to utilize this list to ensure the correct IDs are used. To see the formatted content of these CSV files with additional information, please visit the [AVM Module Indexes]({{% siteparam base %}}/indexes) page.

These will also be provided as a comment on the module proposal, once accepted, from the AVM core team.

{{% /notice %}}

Modules **MUST** provide the capability to collect deployment/usage telemetry as detailed in [Telemetry]({{% siteparam base %}}/help-support/telemetry/) further.

To highlight that AVM modules use telemetry, an information notice **MUST** be included in the footer of each module's `README.md` file with the below content. (See more details on this requirement, [here](https://docs.opensource.microsoft.com/releasing/general-guidance/telemetry/).)

### Telemetry Information Notice

{{% notice style="note" %}}

The following information notice is automatically added at the bottom of the `README.md` file of the module when

- **Bicep:** Using the [`utilities/tools/Set-AVMModule.ps1`](https://github.com/Azure/bicep-registry-modules/blob/main/utilities/tools/Set-AVMModule.ps1) utility
- **Terraform:** Executing the `make docs` command with the note and header `## Data Collection` being placed in the module's `_footer.md` beforehand

{{% /notice %}}

{{< highlight lineNos="false" type="markdown" wrap="true" title="" >}}

### Data Collection

{{% include file="/static/includes/telemetry-information-notice.md" %}}
{{< /highlight >}}

### Bicep

{{% notice style="important" %}}
The value you need to use for your module is defined in the related module index. You can look it up on the index pages for [Resource Modules]({{% siteparam base %}}/indexes/terraform/tf-resource-modules/#module-name-telemetry-id-prefix-github-teams-for-owners--contributors), [Pattern Modules]({{% siteparam base %}}/indexes/terraform/tf-pattern-modules/#module-name-telemetry-id-prefix-github-teams-for-owners--contributors) and [Utility Modules]({{% siteparam base %}}/indexes/terraform/tf-utility-modules/#module-name-telemetry-id-prefix-github-teams-for-owners--contributors).
{{% /notice %}}

The ARM deployment name used for the telemetry **MUST** follow the pattern and **MUST** be no longer than 64 characters in length: `46d3xbcp.<res/ptn>.<(short) module name>.<version>.<uniqueness>`

- `<res/ptn>` == AVM Resource or Pattern Module
- `<(short) module name>` == The AVM Module's, possibly shortened, name including the resource provider and the resource type, **without**;
  - The prefixes: `avm-res-`
  - The prefixes: `avm-ptn-`
- `<version>` == The AVM Module's MAJOR.MINOR version (only) with `.` (periods) replaced with `-` (hyphens), to allow simpler splitting of the ARM deployment name
- `<uniqueness>` == This section of the ARM deployment name is to be used to ensure uniqueness of the deployment name.
  - This is to cater for the following scenarios:
    - The module is deployed multiple times to the same:
      - Location/Region
      - Scope (Tenant, Management Group,Subscription, Resource Group)

{{% notice style="note" %}}

Due to the 64-character length limit of Azure deployment names, the `<(short) module name>` segment has a length limit of 36 characters, so if the module name is longer than that, it **MUST** be truncated to 36 characters. If any of the semantic version's segments are longer than 1 character, it further restricts the number of characters that can be used for naming the module.

{{% /notice %}}

An example deployment name for the AVM Virtual Machine Resource Module would be: `46d3xbcp.res.compute-virtualmachine.1-2-3.eum3`

An example deployment name for a shortened module name would be: `46d3xbcp.res.desktopvirtualization-appgroup.1-2-3.eum3`

{{% notice style="tip" %}}

**Terraform**: Terraform uses a telemetry provider, the configuration of which is the same for every module and is included in the template repo.

**General**: See the language specific contribution guides for detailed guidance and sample code to use in AVM modules to achieve this requirement.

- [Bicep]({{% siteparam base %}}/contributing/bicep/)
- [Terraform]({{% siteparam base %}}/contributing/terraform/)

{{% /notice %}}

### Terraform

To enable telemetry data collection for Terraform modules, the [modtm](https://registry.terraform.io/providers/Azure/modtm/latest) telemetry provider **MUST** be used. This lightweight telemetry provider sends telemetry data to Azure Application Insights via a HTTP POST front end service.

The `modtm` telemetry provider is included in all Terraform modules and is enabled by default through the [main.telemetry.tf](https://github.com/Azure/terraform-azurerm-avm-template/blob/main/main.telemetry.tf) file being automatically distributed from the template repo.

The `modtm` provider **MUST** be listed under the `required_providers` section in the module's `terraform.tf` file using the following entry. This is also validated by the linter.

```terraform
terraform {
  required_providers {
    # .. other required providers as needed
    modtm = {
      source = "Azure/modtm"
      version = "~> 0.3"
    }
  }
}
```
