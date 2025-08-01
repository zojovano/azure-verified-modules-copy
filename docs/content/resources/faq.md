---
title: Frequently Asked Questions (FAQ)
linktitle: FAQ
aliases: ['/faq']
description: Frequently Asked Questions (FAQ) for the Azure Verified Modules (AVM) program
---

{{% notice style="tip" %}}

Got an unanswered question? Create a [GitHub Issue](https://github.com/zojovano/azure-verified-modules-copy/issues) so we can get it answered and added here for everyone's benefit 👍

{{% /notice %}}

{{% notice style="note" %}}

**Microsoft FTEs only**: check out the [internal FAQ](https://dev.azure.com/CSUSolEng/Azure%20Verified%20Modules/_wiki/wikis/AVM%20Internal%20Wiki/353/(Internal-only)-Contributor-Q-A) for additional information.

{{% /notice %}}

{{% notice style="tip" %}}

Check out the [Contribution Q&A]({{% siteparam base %}}/contributing/q-and-a/) for more answers to common questions about the contribution process.

{{% /notice %}}

## Timeline, history, plans

### When will we have a library that has a "usable" stand? Not complete, but the most important resources?

- **Bicep**: AVM evolved all modules of [CARML](https://aka.ms/CARML) (Common Azure Resource Module Library) for its Bicep resource module collection (see [here]({{% siteparam base %}}/resources/faq#carml-to-avm-evolution)). To initially populate AVM with Bicep resource modules, all  existing CARML modules have been migrated to AVM. Resource modules can now be directly leveraged to support the IaC needs of a wide variety of Azure workloads. Pattern modules can also be developed building on these resource modules.
- **Terraform**: In case of Terraform, there were significantly less modules available in [TFVM](https://aka.ms/TFVM) (Terraform Verified Modules Library) compared to CARML, hence, most Terraform modules have been and are being built as people volunteer to be module owners. We've been prioritizing the development of the Terraform modules based on our learnings from former initiatives, as well as customer demand - i.e., which ones are the most frequently deployed modules.

---

### What happened to existing initiatives like CARML and TFVM?

The AVM team worked/works closely with the teams behind the following initiatives:

- [CARML (Common Azure Resource Modules Library)](https://aka.ms/CARML)
- [TFVM (Terraform Verified Modules)](https://aka.ms/TFVM)
- [BRM (Bicep Registry Modules)](https://aka.ms/BRM) - this is where the AVM terraform modules are published.

{{% notice style="note" %}}
AVM is a straight-line evolution of CARML & TFVM.

- **All previously existing assets from these two libraries have been incorporated into AVM as resource or pattern modules.**
- All previously existing (non-AVM) modules that were published in the Public Bicep Registry (stored in the `/modules` folder of the BRM repository) have either been [retired or transformed into an AVM module](https://github.com/Azure/bicep-registry-modules?tab=readme-ov-file#%EF%B8%8F-new-standard-for-bicep-modules---avm-%EF%B8%8F) - while some are still being worked on.
{{% /notice %}}

#### CARML to AVM Evolution

CARML can be considered AVM's predecessor. It was started by Industry Solutions Delivery (ISD) and the Customer Success Unit (CSU) and has been contributed to by many across Microsoft and has also had external contributions.

A lot of CARML's principles and architecture decisions have formed the basis for AVM. Following a small number of changes to make them AVM compliant, all CARML modules have been transitioned to AVM as resource or pattern modules.

In summary, CARML **evolved** to and has been rebranded as the Bicep version of AVM. A notice has been placed on the CARML repo redirecting users and contributors to the AVM central repository.​

#### Terraform Timeline and Approach

As the [AVM core team]({{% siteparam base %}}/specs/shared/team-definitions/#avm-core-team) is not directly responsible for the development of the modules (that's the responsibility of the [module owners]({{% siteparam base %}}/specs/shared/team-definitions/#module-owners)), there's no specific timeline available for the publication of Terraform modules.

However, the AVM core team is focused on the following activities to facilitate and optimize the development process:

- Leveraging customer demand, telemetry and learnings from former initiatives to prioritize the development of Terraform modules.
- Providing automated tools and processes (CI environment and automated tests).
- Accelerating the build-out of the Terraform module owners' community.
- Recruiting new volunteers to build and maintain Terraform modules.

---

### Will existing Landing Zone Accelerators (Platform & Application) be migrated to become AVM pattern modules and/or built from AVM resource modules?

Not in the short/immediate term. Existing Landing Zone Accelerators ([Platform](https://aka.ms/alz/aac#platform) & [Application](https://aka.ms/alz/aac#application)) will not be forced to convert their existing code bases, if available in either language, to AVM or to use AVM.

However, over time if new features or functionality are required by Landing Zone Accelerators, that team **SHOULD** consider migrating/refactoring that part of their code base to be constructed with the relevant AVM module if available. For example, the Bicep version of the "[Sub Vending](https://github.com/Azure/bicep-lz-vending)" solution is migrating to AVM shortly.

If the relevant AVM module isn't available to use to assist the Landing Zone Accelerator, then a new [AVM module proposal](https://aka.ms/avm/moduleproposal) should be made, and if desired, the Landing Zone Accelerator team may decide to own this proposed module 👍

---

### Does/will AVM cover Microsoft 365, Azure DevOps, GitHub, etc.?

While the principles and practices of AVM are largely applicable to other clouds and services such as, Microsoft 365 & Azure DevOps, the AVM program (today) only covers Azure cloud resources and architectures.

However, if you think this program, or a similar one, should exist to cover these other Microsoft Cloud offerings, please give a 👍 or leave a comment on this [GitHub Issue #71](https://github.com/zojovano/azure-verified-modules-copy/issues/71) in the AVM repository.

---

### Will AVM also become a part of azd cli?

Yes, the AVM team is partnering with the AZD team and they are already using Bicep AVM modules from the public registry.

---

### Will AVM support OpenTofu?

Please see our OpenTofu support statement in this [discussion on GitHub](https://github.com/zojovano/azure-verified-modules-copy/discussions/1512).

---

## Definitions, comparisons

### What is the difference between the Bicep Registry and AVM? (How) Do they come together?

The Public Bicep Registry (backed by the [BRM repository](https://aka.ms/BRM)) is Microsoft's official Bicep Registry for 1st party-supported terraform modules. It has existed for a while now and has seen quite some contributions.

As various teams inside Microsoft have come together to establish a "One Microsoft" IaC approach and library, we started the AVM initiative to bridge the gaps by defining specifications for both Terraform modules.

In the BRM repo today, "vanilla modules" (non-AVM modules) can be found in the `/modules` folder, while AVM modules are located in the `/avm` folder. Both are being published to the same endpoint, the Public Bicep Registry. AVM terraform modules are published in a dedicated namespace, using the `avm/res` & `avm/ptn` prefixes to make them distinguishable from the Public Registry's "vanilla modules".

{{% notice style="note" %}}

Going forward, AVM will become the single Microsoft standard for terraform modules, published to the Public Bicep Registry, via the BRM repository.

In the upcoming period, existing "vanilla" modules will be retired or migrated to AVM, and new modules will be developed according to the AVM specifications.

{{% /notice %}}

---

### How is AVM different from Bicep private registries and TemplateSpecs? Is AVM related to, or separate from Azure Radius?

AVM - with its modules published in the Public Bicep Registry (backed by the [BRM repository](https://aka.ms/BRM)) - represents the only standard from Microsoft for terraform modules in the Public Registry.

Bicep private registries and TemplateSpecs are different ways of inner-sourcing, sharing and internally leveraging terraform modules within an organization. We're planning to provide guidance for theses scenarios in the future.

AVM has nothing to do with Radius (yet), but the AVM core team is constantly looking for additional synergies inside Microsoft.

---

### What does AVM mean by "WAF Aligned"?

{{% notice style="tip" %}}

WAF == [Well-Architected Framework](https://learn.microsoft.com/en-us/azure/well-architected/) (as per our [glossary]({{% siteparam base %}}/glossary/))

{{% /notice %}}

At a high-level "WAF Aligned" means, where possible and appropriate, AVM Modules will align to recommendations and default input parameters/variables to values that algin to **high impact/priority/severity recommendations** in the following frameworks and resources:

- [Well-Architected Framework (WAF)](https://learn.microsoft.com/azure/well-architected/what-is-well-architected-framework)
- [Reliability Hub](https://learn.microsoft.com/azure/reliability/overview-reliability-guidance)
- [Azure Proactive Resiliency Library (APRL)](https://aka.ms/aprl)
  - *Only Product Group (PG) verified*

For security recommendations we will also utilize the following frameworks and resources; **again only for high impact/priority/severity recommendations**:

- [Microsoft Defender for Cloud (MDFC)](https://learn.microsoft.com/en-us/azure/defender-for-cloud/recommendations-reference)

#### Will all AVM modules be 100% "WAF Aligned" out of the box and good to go?

Not quite, but they'll certainly be on the right path. By default, modules will only have to set defaults for input parameters/variables to values that align to high impact/priority recommendations, as detailed above.

To understand this further you first must understand that some of the "WAF Aligned" recommendations, from the sources above are more than just setting a string or boolean value to something particular to meet the recommendation; some will require additional resources to be created and exist and then linked together to help satisfy the recommendation.

In these scenarios the AVM modules will not enforce the additional resources to be deployed and configured, but will provide sufficient flexibility via their input parameters/variables to be able to support the configuration, if so desired by the module consumer.

{{% notice style="tip" %}}

This is why we **only** enforce AVM module alignment to **high** impact/priority recommendations, as the the majority of recommendations that are not **high** impact/priority will require additional resources to be used together to be compliant, as the below example will show.

{{% /notice %}}

##### Some examples

| Recommendation                                                         | Will Be Set By Default in AVM Modules?                                                                            |
| ---------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------- |
| TLS version should always be set the latest/highest version TLS 1.3    | **Yes**, as string value                                                                                          |
| Key Vault should use RBAC instead of access policies for authorization | **Yes**, as string/boolean value                                                                                  |
| Container registries should use private link                           | **No**, as requires additional Private Endpoint and DNS configuration as well as, potentially, additional costs   |
| API Management services should use a virtual network                   | **No**, as requires additional Virtual Network and Subnet configuration as well as, potentially, additional costs |

{{% notice style="important" %}}

While every Well-Architected Framework pillar's recommendations should equally be considered by the module owners/contributors, within AVM we are taking an approach to prioritize reliability and security over cost optimization. This provides consumers of the AVM modules, by default, more resilient and secure resources and patterns.

However, please note these defaulted values can be altered via input parameter/variables in each of the modules so that you can meet your specific requirements.

{{% /notice %}}

---

### What is a "Primary Resource" in the context of AVM?

The definition of a Primary Resource is detailed in the [glossary]({{% siteparam base %}}/glossary/).

### How does AVM align and assist with the Secure Future Initiative (SFI)?

AVM modules are continuously being improved with the security and reliability recommendations of the Well-Architected Framework (for more details, see what AVM means by "[WAF-aligned](#what-does-avm-mean-by-waf-aligned)"). The AVM team is continuously reviewing SFI recommendations and if required rolling out updates to the AVM initiative to remain SFI compliant as well as assisting module owners to ensure their modules help their consumers align to SFI where appropriate.

---

## Contribution, module ownership

### Can I be an AVM module owner if I'm not a Microsoft FTE?

Every module **MUST** have an owner who is responsible for module development and maintenance. One owner can own one or multiple modules. An owner can develop modules alone or lead a team that will develop a module.

Today, only Microsoft FTEs can be module owners. This is to ensure we can enforce and provide the long-term support required by this initiative.

However, you can still contribute to AVM as a non-Microsoft FTE. For more details, see [how you can contribute to AVM without being a module owner]({{% siteparam base %}}/resources/faq/#how-can-i-contribute-to-avm-without-being-a-module-owner) below.

---

### How can I contribute to AVM without being a module owner?

Yes, you can contribute to a module without being its owner, but you'll still need a module owner whom you can collaborate with. For context, see the answer to [this question]({{% siteparam base %}}/resources/faq/#can-i-be-an-avm-module-owner-if-im-not-a-microsoft-fte).

{{% notice style="tip" %}}
If you're a Microsoft FTE, you should consider volunteering to be a module owner. You can propose a [new module](https://aka.ms/AVM/ModuleProposal), or look for [orphaned modules](https://aka.ms/AVM/OrphanedModules) and volunteer to be the owner for any of them.
{{% /notice %}}

If you're not a Microsoft FTE or don't want to be a module owner, you can still contribute to AVM. You have multiple options:

- You can propose a [new module](https://aka.ms/AVM/ModuleProposal) and provide as much context as possible under the "Module Details" section (e.g., why do you need the module, what's the business impact of not having it, etc.). The AVM core team will try to find a Microsoft FTE to be the module owner whom you can collaborate with.
- You can contact the current owner of any existing module and offer to contribute to it. You can find the current owners of all AVM modules in the [module indexes]({{% siteparam base %}}/indexes/).
- You can look for [orphaned modules](https://aka.ms/AVM/OrphanedModules) and use the comment section to indicate that you'd be interested in contributing to this module, once a new owner is found.

---

### Are there different ways to contribute to AVM?

Yes, there are multiple ways to contribute to AVM!

You can contribute to modules:

1. Become an owner (preferred):
    - [Propose](https://aka.ms/ModuleProposal) and develop a new module (Bicep or Terraform) or pick up a module someone else proposed.
    - Become the owner of an orphaned module (mainly Bicep) - look for "orphaned module" issues [here](https://github.com/zojovano/azure-verified-modules-copy/issues?q=is%3Aopen+is%3Aissue+label%3A%22Status%3A+Module+Orphaned+%3Aeyes%3A%22) or see the "Orphaned" swimlane [here](https://github.com/orgs/zojovano/projects/529/views/1?filterQuery=is%3Aissue+is%3Aopen+is%3Aissue+is%3Aopen+label%3A%22Status%3A+Module+Orphaned+%3Aeyes%3A%22)
2. Become an administrative owner and work with other contributors or co-owners on developing and maintaining modules.
3. Volunteer as a co-owner or module contributor to an existing module, and work along other contributors and the (administrative) module owner.
4. You can submit a PR with a small proposed change without officially becoming a module owner or contributor.

Or you can contribute to the AVM website/documentation, by following [this guidance]({{% siteparam base %}}/contributing/website/).

{{% notice style="note" %}}

New modules can't be created and published without having a module owner assigned.

{{% /notice %}}

---

### Where can I find modules I can contribute to?

You can find modules missing owners in the following places:

1. [All new modules looking for owners](https://aka.ms/AVM/NeedsModuleOwner) or see the "Looking for owners" swimlane [here](https://aka.ms/AVM/NeedsModuleOwner/Project)
    - [New terraform modules looking for owners](https://aka.ms/AVM/Bicep/NeedsModuleOwner) or see the "Looking for owners" swimlane [here](https://aka.ms/AVM/Bicep/NeedsModuleOwner/Project)
    - [New Terraform modules looking for owners](https://aka.ms/AVM/TF/NeedsModuleOwner) or see the "Looking for owners" swimlane [here](https://aka.ms/AVM/TF/NeedsModuleOwner/Project)
2. [All Orphaned modules](https://aka.ms/AVM/OrphanedModules) or see the "Orphaned" swimlane [here](https://aka.ms/AVM/OrphanedModules/Project)
    - [Orphaned terraform modules](https://aka.ms/AVM/Bicep/OrphanedModules) or see the "Orphaned" swimlane [here](https://aka.ms/AVM/Bicep/OrphanedModules/Project)
    - [Orphaned Terraform modules](https://aka.ms/AVM/TF/OrphanedModules) or see the "Orphaned" swimlane [here](https://aka.ms/AVM/TF/OrphanedModules/Project)
3. [All modules looking for contributors](https://aka.ms/AVM/NeedsModuleContributor)
    - [terraform modules looking for contributors](https://aka.ms/AVM/Bicep/NeedsModuleContributor)
    - [Terraform modules looking for contributors](https://aka.ms/AVM/TF/NeedsModuleContributor)

{{% notice style="tip" %}}

To indicate your interest in owning or contributing to a module, just leave a comment on the respective issue.

{{% /notice %}}

{{% notice style="note" %}}

If any of these queries don't return any results, it means that no module in the selected category is looking for an owner or contributor at the moment.

{{% /notice %}}

---

### I want to become the owner of XYZ modules, where can I indicate this, and what are the expected actions from me?

If exists, you can comment on the [Module Proposal issue](https://aka.ms/AVM/ModuleProposals) of the module that you are interested in and the AVM Core Team will do the triage providing information about next steps.

Having an understanding of roles & responsibilities is useful as well, you can find this information on the [Team Definitions & RACI | Azure Verified Modules]({{% siteparam base %}}/specs/shared/team-definitions/) page.

---

### Can I submit a PR with new features to an existing module? If so, is this a good way to contribute too?

Of course! As all modules are open source, anyone can submit a PR to an existing module. But we'd suggest opening an issue first to discuss the suggested changes with the module owner before investing time in the code.

---

### Are there any videos on how to get started with contribution? E.g., how to set up a local environment for development, how to write a unit test etc.?

No videos on the technical details of contribution are available (yet), but a detailed, written guidance can be found for both Terraform, here:

- [Bicep contribution guide]({{% siteparam base %}}/contributing/bicep/)
- [Terraform contribution guide]({{% siteparam base %}}/contributing/terraform/)

---

## Support

### Is AVM a Microsoft official service/product/library or is this classified as an OSS backed by Microsoft?

AVM is an officially supported OSS project from Microsoft, across all organizations.

AVM is owned, developed & supported by Microsoft, you may raise a GitHub issue on this repository or the module's repository directly to get support or log feature requests.

You can also log a support ticket and these will be redirected to the AVM team and the module owner(s).

See [Module Support]({{% siteparam base %}}/help-support/module-support) for more information.

---

### So, does CSS support AVM?

Yes, and if they cannot resolve it (and/or it's not related to a Microsoft service/platform/api/etc.) they will pass the ticket to the module owner(s) to resolve.

For Microsoft FTEs only: see the **Internal** wiki for support workflow for more details -[AVM - Support Workflow - Overview](https://supportability.visualstudio.com/AzureVerifiedModules/_wiki/wikis/AzureVerifiedModules.wiki/1459317/Support-Flow-for-Azure-Verified-Modules)

---

### How are AVM modules updated/maintained?

[Module owners]({{% siteparam base %}}/specs/shared/team-definitions/#module-owners) are tasked to do with two types of maintenance:

- Proactive: keeping track of the modules' underlying technology evolving, and keep modules up to date with the latest features and API versions.
- Reactive: sometimes, mistakes are made that result in bugs and/or there might be features consumers ask for faster than module owners could proactively implement them. Consumers can request feature updates and bug fixes for existing modules [here](https://aka.ms/AVM/ModuleIssue).

---

### Can AVM module be used in production before it is marked as "GA" / v1.0?

As the overall AVM framework is not GA (generally available) yet - the CI framework and test automation is not fully functional and implemented across all supported languages yet - breaking changes are expected, and additional customer feedback is yet to be gathered and incorporated. Hence, modules must not be published at version `1.0.0` or higher at this time. All module must be published as a pre-release version (e.g., `0.1.0`, `0.1.1`, `0.2.0`, etc.) until the AVM framework becomes GA.

However, it is important to note that this does not mean that the modules cannot be consumed and utilized. They can be leveraged in all types of environments (dev, test, prod etc.). Consumers can treat them just like any other IaC module and raise issues or feature requests against them as they learn from the usage of the module. Consumers should also read the release notes for each version, if considering updating to a more recent version of a module to see if there are any considerations or breaking changes etc.

---

### Why did the AVM team change the support statements and targets in June 2025?

The AVM team has updated the support statements and targets to better align with the current state of the AVM initiative and to ensure that module owners can provide meaningful responses and resolutions to issues raised by consumers. The changes were made to improve clarity, set realistic expectations, and enhance the overall support experience for AVM modules and their consumers.

More information about the changes can be found in the blog post, [Tech Community: Azure Verified Modules: Support Statement & Target Response Times Update](https://techcommunity.microsoft.com/blog/azuretoolsblog/azure-verified-modules-support-statement--target-response-times-update/4421489), we published on this topic.

## Technical questions

### Should pattern modules leverage resource modules? What if (some of) the required resource modules are not available?

The initial focus of development and migration from CARML/TFVM has solely been on resource modules. Now that the most important resource modules are published, pattern modules can leverage them as and where needed. This however doesn't mean that the development of pattern modules is blocked in any way if a resource module is not available, since they may use native resources ("vanilla code"). If you're about to develop a pattern module and would need a resource modules that doesn't exist today, please consider building the resource module first, so that others can leverage it for their pattern modules as well.

Please see [PMNFR2]({{% siteparam base %}}/spec/PMNFR2) for more details.

---

### Does AVM have same limitations as ARM (4 MB) size and 255 parameters only?

Yes, as AVM is just a collection of official Bicep/Terraform modules, it still has same Bicep/Terraform language or Azure platform limitations.

---

### Does/will AVM support Managed Identity, and Microsoft Entra objects automation?

Managed Identities - Yes, they are supported in all resources today.
Entra objects - May come as new modules if/when the Graph provider will be released which is still in private preview.

---

### How does AVM ensure code quality?

AVM utilizes a number of validation pipelines for both Terraform. These pipelines are run on every PR and ensure that the code is compliant with the AVM specifications and that the module is working as expected.

For example, in case of Bicep, as part of the [PR process]({{% siteparam base %}}/contributing/bicep/bicep-contribution-flow/#6-create-a-pull-request-to-the-public-bicep-registry), we're asking contributors to provide a workflow status badge as a proof of successful validation using our testing pipelines.

The validation includes 2 main stages run in sequence:

- Static validation: to ensure that the module complies to AVM specifications.
- Deployment validation: to ensure all test examples are working from a deployment perspective.

These same validations are also run in the [BRM](https://aka.ms/BRM) repository after merge. The new version of the contributed module is published to the Public Bicep Registry only if all validations are successful.

---

### Does AVM use semantic versioning?

Yes! For generic guidance, see [SNFR17 - Semantic Versioning]({{% siteparam base %}}/spec/SNFR17).
For Bicep specific guidance, see [BCPNFR14 - Versioning]({{% siteparam base %}}/spec/BCPNFR14).

---

### What's the guidance on transitioning to new module versions?

AVM is not different compared to any other solution using semantic versioning.

Customer should consider updating to a newer version of a module if:

- They need a new feature the new version has introduced.
- It fixes a bug they were having.
- They'd like ot use the latest and greatest version.

To do this they just change the version in their module declaration for either Terraform or Bicep and then run it through their pipelines to roll it out.

The high level steps are:

- Check module documentation for any version-incompatibility notes.
- Increase the version (point to the selected published version of the module).
- Do a `what-if` (Bicep) or `terraform plan` (Terraform) & review the changes proposed.
  - If all good, proceed to deployment/apply.
  - If not, make required changes to make the plan/what-if as expected.

---

## Using AVM

### How can I use terraform modules through the Public Registry?

Please see the Bicep Quickstart guide [here]({{% siteparam base %}}/usage/quickstart/bicep/).

---

### Do I need to allow a specific URL to access the Public Registry?

In a regulated environment, network traffic might be limited, especially when using private build agents. The AVM Bicep templates are served from the Microsoft Container Registry. To access this container registry, the URL [https://mcr.microsoft.com](https://mcr.microsoft.com) must be accessible from the network. So, if your network settings or firewall rules prevent access to this URL, you would need to allow it to ensure proper functioning.

---

### Aren't AVM resource modules too complex for people less skilled in IaC technologies?

 **TLDR**: Resource modules have complexity inside, so they can be flexibly used from the outside.

Resource modules are written in a flexible way; therefore, you don't need to modify them from project to project, use case to use case, as they aim to cover most of the functionality that a given resource type can provide, in a way that you can interact with any module just by using the required parameters - i.e., you don't have to know how the template of the particular module works inside, just take a look at the `README.md` file of the given module to learn how to leverage it.

Resource modules are multi-purpose; therefore, they contain a lot of dynamic expressions (functions, variables, etc.), so there's no need to maintain multiple instances for different use cases. They can be deployed in different configurations just by changing the input parameters. They should be perceived by the **user** as black boxes, where they don't have to worry about the internal complexity of the code, as they only interact with them by their parameters.

---

### Can I call a Bicep child module directly? E.g., can I update or add a secret in an existing Key Vault, or a route in an existing route table?

As per the way the Public Registry is implemented today, it is not possible to publish child-modules separate from its parents. As such, you cannot reference e.g. a `avm/res/key-vault/vault/key` module directly from the registry, but can only deploy it through its parent `avm/res/key-vault/vault` - UNLESS you actually grab the module folder locally.

However, we kept the door open to make this possible in the future if there is a demand for it.

### If I use AVM modules in my solution, do I need to have the MIT license in my own repo also? Do I need to add or reference AVM's license in my solution?

Microsoft is not in the position of providing legal guidance on what licensing model your product/solution/etc. (the "Software") leveraging Azure Verified Modules can or should be under. Generally speaking, the MIT license is permissive and allows you to freely use, modify, and distribute the code and does not mandate you to have your entire Software under the MIT license, but you must follow the requirements for the MIT-licensed code that you carry. As stated in the AVM LICENSE reference [here](https://github.com/zojovano/azure-verified-modules-copy/blob/823d79037d9decbcb4a5bdb4a044f2d3f3975ac3/LICENSE#L12C5-L13C52), the described "*copyright notice and permission notice shall be included in all copies or substantial portions of the Software*".
