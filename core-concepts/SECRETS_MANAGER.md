---
title: 'Secrets Manager'
description: 'Secure storage for API keys, tokens, credentials, and other sensitive values.'
icon: 'key'
---

## Introduction

Orka's Secrets Management feature allows you to securely store sensitive information like API keys, passwords, and tokens. Instead of hardcoding these values in your workflows, you can reference them securely, ensuring they're never exposed in logs or execution history.

## What Are Secrets?

Secrets are sensitive pieces of information that need special protection:

* API keys for third-party services
* Access tokens for authentication
* Database credentials
* Webhook URLs containing sensitive information
* Private encryption keys

Orka securely encrypts all secrets and makes them available only when needed during workflow execution.

## Managing Secrets

#### Creating a Secret

1. Navigate to Settings > Secrets in the Orka dashboard
2. Click the New Secret button
3. Enter the following information:
   1. Name: Use UPPER\_SNAKE\_CASE format (e.g., API\_KEY)
   2. Description (optional): Provide context about the secret's purpose
   3. Value: The sensitive data to be stored securely
4. Click Create

#### Viewing Secrets

The Secrets page displays all your secrets with the following information:

* Name
* Description
* Creation date
* Reference syntax for use in workflows

Note that for security reasons, you cannot view the actual value of a secret after it's created.

#### Updating a Secret

1. Navigate to Settings > Secrets
2. Find the secret you want to update
3. Click the Actions menu (three dots) and select Edit
4. You can update:
   1. Description: Change or add a description
   2. Value: Provide a new value (leave empty to keep the existing value)
5. Click Save

#### Deleting a Secret

1. Navigate to Settings > Secrets
2. Find the secret you want to delete
3. Click the Actions menu (three dots) and select Delete
4. Confirm the deletion

## Using Secrets in Workflows

### Secret References

To use a secret in a workflow, use the following syntax:

```
{{secrets.SECRET_NAME}}
```

> Check [oel](../orka-expression-language/oel "mention") for more information about Orka Expression Language (OEL).

### Frequently Asked Questions

#### Can I view my secret values after creation?

No, for security reasons, secret values cannot be viewed after creation. You can only update them with new values.

#### Are secrets shared across my organization?

Secrets are scoped to your tenant, meaning they're available to all workflows within your organization but not to other organizations.

#### How do I know if my secrets are being used?

While Orka doesn't currently provide usage tracking for secrets, you can search your workflows for references to specific secret names.

#### What happens if a secret is deleted but still referenced in a workflow?

If a workflow references a deleted secret, that step will fail with an error indicating the secret could not be found.

#### Can I use secrets in custom scripts or code?

Yes, secrets can be used in any workflow node that supports variable interpolation, including custom code and script nodes.

#### How secure are my secrets?

Orka encrypts all secrets using industry-standard encryption. Secret values are only decrypted when needed during workflow execution and are never stored in logs or execution history.