# Azure Functions connectors samples

This repository is the canonical index of samples that show how to use the new **Connector Namespace** integration with **Azure Functions**. Each sample lives in its own repo so you can clone, deploy, and explore independently.

> [!NOTE]
> Connectors in Azure Functions are in **public preview**. The Connector Namespace is currently available in **West Central US** (`westcentralus`); your function app can be deployed in any region that supports the chosen hosting plan. Supported languages: .NET 10 and .NET 8 isolated worker, Python 3.13+, and Node.js 22+. See the [overview](https://learn.microsoft.com/azure/azure-functions/functions-connectors-overview) for details.

## What are Functions connectors?

Azure Functions integrates with the managed connectors platform that backs Logic Apps and Power Platform, giving your functions:

- **Connector triggers** — A function runs when an event occurs in an external service (new email in Office 365, file added to SharePoint or OneDrive, message posted to Microsoft Teams, and many more). The runtime exposes a `connectorTrigger` binding that receives webhook callbacks from the Connector Namespace.
- **Connector SDK actions** — Function code calls connector operations through strongly-typed clients (Office 365 Outlook, Office 365 Users, Microsoft Teams, SharePoint, OneDrive, …) or through dynamic payload models for any other connector.

The connector platform handles webhook registration, OAuth flows, token refresh, and retry — you focus on the business logic.

## Getting-started samples (per language)

Start here if you're new to connectors in Azure Functions. Each repo contains a minimal trigger + SDK sample, infrastructure as code, and `azd` templates so you can go from clone to deployed in one command.

| Language | Repository | What's inside |
|---|---|---|
| **.NET** (isolated worker, .NET 8 / .NET 10) | [Azure-Samples/functions-connectors-net](https://github.com/Azure-Samples/functions-connectors-net) | `ConnectorTrigger` binding, typed `Azure.Connectors.Sdk.*` clients, DI registration patterns. |
| **Python** (3.13+) | [Azure-Samples/functions-connectors-python](https://github.com/Azure-Samples/functions-connectors-python) | `@app.connector_trigger` decorator, `azurefunctions-extensions-connectors` typed payloads. |
| **TypeScript / JavaScript** (Node.js 22+) | [Azure-Samples/functions-connectors-typescript](https://github.com/Azure-Samples/functions-connectors-typescript) | `connectors.office365.onNewEmail` typed entry points and the generic `app.connectorTrigger`. |

## End-to-end scenario samples

Larger samples that combine a connector trigger, the connector SDK, and other Azure Functions bindings to solve a complete scenario.

- [**End-to-end .NET sample: email → user lookup → Teams**](https://github.com/Azure-Samples/functions-connectors-net-e2e-email-users-teams) — A function fires on each new Office 365 email, enriches the sender through the Office 365 Users connector, and posts an adaptive card to a Microsoft Teams channel. Shows DI registration of multiple typed clients (`Office365Client`, `Office365UsersClient`, `TeamsClient`) and per-connection runtime URLs.

## Authentication samples

Secret-free topologies between the Connector Namespace and your function app.

- [**.NET sample: built-in authentication with managed identity**](https://github.com/Azure-Samples/functions-connectors-net-builtinauth) — Replaces the shared `connector_extension` system key with **App Service built-in authentication** (Easy Auth) validating an Entra ID token minted by the Connector Namespace's managed identity. Includes the full Bicep wiring for federated identity credentials, `authsettingsV2`, and `allowedPrincipals.identities`.

## When to use connectors

Use connectors in Functions when:

- You react to SaaS events and want to skip writing webhook registration, validation handshakes, and OAuth refresh.
- Your function code already calls Microsoft 365 or third-party APIs through hand-rolled HTTP clients and connection sprawl is becoming a maintenance burden.
- You're extending an event-driven Functions app and want SaaS triggers in the same project, deployment pipeline, and observability stack.
- You're building **agentic workflows** where a function receives an event, reasons with an AI model, and acts back into a SaaS system through a connector operation.
- You need code-first control over orchestration (branching, custom auth between steps, reuse of existing libraries) but want connectors to own the inbound and outbound integration.

If the workload is pure orchestration across connectors with no custom code, **Logic Apps Standard** remains the more direct choice.

## Related documentation

- [Use connectors in Azure Functions](https://learn.microsoft.com/azure/azure-functions/functions-connectors-overview) — Conceptual overview, packages, trigger model, and authentication.
- [Azure connectors overview](https://learn.microsoft.com/azure/connectors/overview) — The connector platform itself.
- [Connector Namespace](https://learn.microsoft.com/azure/connectors/connector-namespace) — The Azure resource that hosts trigger configurations and connections.
- [Serverless agents runtime in Azure Functions](https://learn.microsoft.com/azure/azure-functions/functions-serverless-agents-runtime) — How connectors plug into agentic workflows.

## Related repositories

- [Azure Functions Connector Extension](https://github.com/Azure/azure-functions-connector-extension) — The trigger binding source and per-connector operation reference.
- [Operations to Azure Functions signature mapping](https://github.com/Azure/azure-functions-connector-extension/blob/main/docs/operations-functions-match.md) — Which payload type each connector operation produces.
- [Connectors Python SDK](https://github.com/Azure/Connectors-python-sdk)
- [Connectors Node.js SDK](https://github.com/Azure/Connectors-nodejs-sdk)

## Contributing

This repo is an index only — the samples themselves live in their own repositories. To propose a new sample, open an issue or PR here with a link to the sample repo and a one-line description of what it demonstrates.

## Trademarks

This project may contain trademarks or logos for projects, products, or services. Authorized use of Microsoft trademarks or logos is subject to and must follow [Microsoft's Trademark & Brand Guidelines](https://www.microsoft.com/legal/intellectualproperty/trademarks/usage/general). Use of Microsoft trademarks or logos in modified versions of this project must not cause confusion or imply Microsoft sponsorship. Any use of third-party trademarks or logos is subject to those third parties' policies.
