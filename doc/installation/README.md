# Installing GitLab using Helm

This document provides all steps in installing a complete GitLab environment via
[helm](../helm/README.md).

## Dependencies

Before you can install GitLab in an Kubernetes cluster, make sure you have
all required tools. See [dependencies][] document for more information.

## Configure

### Resources

You will need to create a few resources to use this chart, such as a static IP and DNS entry. See [resources document][resources] for more information.

### Secrets

For a functional deployment, various secrets are necessary. See [secrets document][secrets] for more information.

### Configuration file

Next, populate your configuration which will be used to deploy. See
[generating configuration document][configuration] for more information.

## Deploy

Now that we have the environment setup and configuration generated,
we can proceed to [deployment][].

[dependencies]: dependencies.md
[helm]: helm/README.md
[resources]: resources.md
[secrets]: secrets.md
[configuration]: configuration.md
[deployment]: deployment.md