---
draft: false
title: Terraform Resource Modules
linktitle: Resource Modules
weight: 1
description: Terraform Resource Module Index showing all available, orphaned and planned modules
---

## Module catalog

{{% moduleStats language="Terraform" moduleType="Resource" showLanguage=true showClassification=true %}}

{{% expand title="➕ Additional information" %}}

{{% notice style="grey" title="Legend" %}}
{{% include file="/static/includes/module-status-legend.md" %}}
{{% /notice %}}

{{% notice style="info" %}}

This page contains various views of the module index (catalog) for **Terraform Resource Modules**. To see these views, **click on the expandable sections** with the "➕" sign below.

- {{% icon icon="fa-brands fa-github" %}} To see the **full, unfiltered, unformatted module index** on GitHub, click [here](https://github.com/zojovano/azure-verified-modules-copy/blob/main/docs/static/module-indexes/TerraformResourceModules.csv).

- {{% icon icon="download" %}} To download the source CSV file, click [here]({{% siteparam base %}}/module-indexes/TerraformResourceModules.csv).

{{% /notice %}}

{{% notice style="note" %}}

Modules listed below that aren't shown with the status of **`Module Available 🟢`**, are currently in development and are not yet available for use. For proposed modules, see the [Proposed modules]({{% siteparam base %}}/indexes/terraform/tf-resource-modules/#proposed-modules---) section below.

{{% /notice %}}

{{% /expand %}}

### Published modules - 🟢 & 🟡

{{% expand title="➕ Published Modules - Module names, status and owners" expanded="true" %}}

{{% moduleNameStatusOwners header=true csv="/static/module-indexes/TerraformResourceModules.csv" language="Terraform" moduleType="resource" include="Available,Orphaned" %}}

{{% /expand %}}

### Proposed modules - ⚪

{{% expand title="➕ Proposed Modules - Module names, status and owners" expanded="false" %}}

{{% moduleNameStatusOwners header=true csv="/static/module-indexes/TerraformResourceModules.csv" language="Terraform" moduleType="resource" include="Proposed" %}}

{{% /expand %}}

### Deprecated modules - 🔴

{{% expand title="➕ Deprecated Modules - Module names, status and owners" expanded="false" %}}

{{% moduleNameStatusOwners header=true csv="/static/module-indexes/TerraformResourceModules.csv" language="Terraform" moduleType="resource" include="Deprecated" %}}

{{% /expand %}}

### All modules - 📇

{{% expand title="➕ All Modules - Module names, status and owners" expanded="false" %}}

{{% moduleNameStatusOwners header=true csv="/static/module-indexes/TerraformResourceModules.csv" language="Terraform" moduleType="resource" include="Available,Orphaned,Proposed,Deprecated" %}}

{{% /expand %}}

### Module Publication History - 📅

{{% expand title="➕ Module Publication History - Module names, status and owners" expanded="false" %}}

{{% moduleHistory header=true csv="/static/module-indexes/TerraformResourceModules.csv" language="Terraform" moduleType="resource" exclude="Proposed" monthsToShow=9999 %}}

{{% /expand %}}

## For Module Owners & Contributors

{{% notice style="note" %}}

This section is mainly intended **for module owners and contributors** as it contains information about the **GitHub Teams for Owners & Contributors**.

{{% /notice %}}

### Module name, Telemetry ID prefix, GitHub Teams for Owners & Contributors

{{% expand title="➕ All Modules - Module name, Telemetry ID prefix, GitHub Teams for Owners & Contributors" expanded="false" %}}

{{% moduleNameTelemetryGHTeams header=true csv="/static/module-indexes/TerraformResourceModules.csv" language="Terraform" moduleType="resource" %}}

{{% /expand %}}
