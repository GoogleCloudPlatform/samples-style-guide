---
title: "Effective Terraform Samples"
linkTitle: "Terraform Style Guide"
type: docs
weight: 20
---

## Introduction {#introduction}

This document defines sample standards for "standalone" Terraform code samples.
It encourages recommended practices for authoring code intended to teach others.
By consistently applying these practices, the collection of Terraform samples as
a whole becomes more approachable.\
Even if not specifically mentioned in the guide, all Terraform samples should
make best-efforts to achieve the following goals wherever possible:

-   **Copy-paste-runnable** - Users should be able to copy, paste, and run the
    Terraform code into their environment with as few changes as possible.
    Samples should be as easy as possible for a user to read, understand, run,
    modify, and troubleshoot.
-   **Teach through code** - Samples should teach users both how and *why*
    specific best practices should be implemented and performed when
    interacting with our services. Samples should also help users find and use
    the Terraform resources that correspond to the "gcloud create" commands.

### Principles {#principles}

Where the guidelines below are insufficient, these principles apply in
descending order of priority:

1.  **Clarity**: The code's purpose and rationale is clear to the reader
1.  **Consistency**: The code has the same implementation from sample to sample
1.  **Simplicity**: The code accomplishes its goal in the simplest way possible
1.  **Portability**: The code should be able to run locally or in Cloud Shell
1.  **Maintainability**: The code is written such that it can be easily maintained.
1.  **Idiomaticity**: The code should be written using idiomatic,
    community-driven coding practices, *unless these practices impact clarity,
    simplicity, or maintainability*

## Structure {#structure}

### Region tags {#region-tags}

Each Terraform code sample should have at least one
[region tag][region-tag] to define which parts of the sample are displayed
from the documentation. In general, for all languages, region tags should be:

-   Globally unique
-   Consistent across the same samples in different languages
-   Begins with the product's region tag prefix
-   In snake case (`snake_case`)

Each region tag should align with the section of the how-to or tutorial guide
that the sample will be included in.

[region-tag]:(https://g3doc.corp.google.com/company/teams/cloud-devrel/dpe/samples/code_snippets_101.md?cl=head#region-tag)

### One sample per file {#one-sample-per-file}

A single file should only include one sample. This keeps the end-to-end code
relevant to the reader's current learning need, and helps reviewers validate the
sample.

### Sample description {#sample-description}

The directory name or filename of the Terraform sample should be descriptive of
what the sample does. If more explanation is needed, the code sample file can
have a top-level comment that succinctly describes what the sample does,
including any setup required to make the sample work.

### Minimal arguments {#minimal-arguments}

Resource arguments should be limited to the requirements for testing.

## Code {#code}

### Language compatibility {#language-compatibility}

Use features that work in all Google Cloud-supported versions of a language and
use language idioms that the community understands.

### Useful comments {#useful-comments}

Comments should be used as needed with the following guidelines:

-   Comments should add context not otherwise obvious from the code.
-   Comments should be readable and grammatically correct.
-   For values that the user may wish to configure, provide links to
    documentation that lists available options (and when to use them).

### Authentication {#authentication}

Samples should always authenticate using [Application Default Credentials][ADC].
Most clients do this automatically, and no special steps are required.

[ADC]:https://cloud.google.com/docs/authentication/production#automatically

### Cyclomatic complexity {#cyclomatic-complexity}

Cyclomatic complexity is the measure of possible code paths. The more code
paths, the more complex the code sample, and the harder to understand and test.
Flow control statements like conditionals (if/else), switches, and loops are
examples of code that increases cyclomatic complexity.

Code samples should have a single path demonstrating their purpose with no extra
code.

### Linting {#linting}

Our code samples should adhere to a style used by the language communities. We
prefer to enforce style using standard linters that are popular in the
community.

## Testing {#testing}

### Coverage {#coverage}

Code samples should have reasonable test coverage and all critical code paths
should have integration tests that test against the production service.

For more information about testing, see the
[Contributing Guide][contributing].

[contributing]:https://github.com/terraform-google-modules/terraform-docs-samples/blob/main/CONTRIBUTING.md

## Language-specific practices {#language-specific-practices}

### No CLIs {#no-clis}

Do not include CLI commands (such as `gcloud` or `kubectl`) inside of your sample
by using the `null_resource` resource. Previous practice shows CLIs are expensive
to maintain and detract from the purpose of the sample.

### No variables {#no-variables}

Don't include Terraform variables (`var.VARIABLE_NAME`). Instead, hard code the
resource names and attribute values.

### Local valuess {#locals}

Sometimes multiple resources have a common string that is not accessible as a
reference or there is no child/parent reference. [Local values][locals] are
allowed and encouraged for repeated text that a user might want to change.
When a name is used multiple times, it's easier to copy, paste, and edit a
local than search and replace the whole file.

[locals]:https://developer.hashicorp.com/terraform/language/values/locals

### Other-vendor resources {#other-vendor-resources}

<!-- TODO: move this section to terraform-docs-samples README -->

For maintainability, don't include other-vendor resources. Multi-cloud isn't
recommended in terraform-docs-samples. Only Google provider resources are
recommended. For example, terraform-docs-samples samples shouldn't have Azure or
AWS resources. For multi-cloud samples, create a blueprint instead.

### Other non-cloud 1P providers {#other-non-cloud-1p-providers}

Other non-cloud 1P providers are allowed, such as `random`, `crypto`, and so
on.

### Randomize resource names

To avoid naming conflicts, make sure that your configurations have a unique
and non-overlapping resource names within each project. To do this, use
namespaces for your resources. Terraform has a built-in [random 
provider][random] for this.

[random]:https://registry.terraform.io/providers/hashicorp/random/latest/docs/resources/id

### Enabling APIs {#enabling-apis}

When possible, omit the `google_project_service` resource. Users are expected to
manually enable Google Cloud billable services like Compute Engine when
required. Terraform informs the users if any such action is required.

However, if the `terraform-docs-samples` tests fail because the sample doesn't
enable a required service, then do include the `google_project_service` resource
in your sample. If your sample enables an API, add `disable_on_destroy = false` to
prevent the API from being disabled when deleting the resources.

### Resource references {#resource-references}

When possible, refer to already-defined resources.

For example:

```
# forwarding rule
resource "google_compute_global_forwarding_rule" "default" {
  name                  = "ssl-proxy-xlb-forwarding-rule"
  ip_protocol           = "TCP"
  load_balancing_scheme = "EXTERNAL"
  port_range            = "443"
  target                = google_compute_target_ssl_proxy.default.id # Reference to already defined resource in the sample
  ip_address            = google_compute_global_address.default.id # Reference to already defined resource in the sample
}
```

### Terraform Google Provider version {#terraform-google-provider-version}

When your sample contains a new resource, add the required minimum Terraform
Google Provider version corresponding to which provider version introduced a
resource. For example, google_apigee_nat_address was added in version 4.37, so
the minimum version is 4.37. To specify a minimum version in a sample, include
the provider requirements, as follows:

```
terraform {
  required_providers {
    google = {
      source = "hashicorp/google"
      version = ">= 4.37.0"
    }
  }
}
```

To determine when a resource was added, see the
[terraform-provider-google/CHANGELOG.md][change-log] or
[terraform-provider-google-beta/CHANGELOG.md][change-log-beta].

[change-log]:https://github.com/hashicorp/terraform-provider-google/blob/main/CHANGELOG.md 
[change-log-beta]:https://github.com/hashicorp/terraform-provider-google-beta/blob/main/CHANGELOG.md

### Provider argument {#provider-argument}

Add the provider argument if the resource is from provider `google-beta`.

```
resource "google_<resource_name>" "default" {
  provider = google-beta
  ...
}
```

Fields and resources that are only present in google-beta are clearly marked in
the provider documentation.
