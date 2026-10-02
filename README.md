# Azure Functions Connectors Samples

Quickstart and end-to-end samples for using Connector Namespace with Azure Functions. Receive events from external services through connector triggers and call connector operations from your code.

## Getting-started samples (per language)

| Language | Repository |
| -------- | ---------- |
| C# (.NET isolated worker) | [functions-connectors-net](https://github.com/Azure-Samples/functions-connectors-net) |
| Python | [functions-connectors-python](https://github.com/Azure-Samples/functions-connectors-python) |
| TypeScript (Node.js) | [functions-connectors-typescript](https://github.com/Azure-Samples/functions-connectors-typescript) |

Each repository has its own prerequisites, deployment instructions, and `azd` templates. Choose a language, open a sample folder, and follow its README.

> [!NOTE]
> Connectors in Azure Functions are in public preview. See the [overview](https://learn.microsoft.com/azure/azure-functions/functions-connectors-overview) for supported runtimes and hosting plans.

## End-to-end scenario samples

| Scenario | Repository |
| -------- | ---------- |
| New email, sender lookup, and a Teams adaptive card (.NET) | [functions-connectors-net-e2e-email-users-teams](https://github.com/Azure-Samples/functions-connectors-net-e2e-email-users-teams) |
| SharePoint document intake, Foundry Content Understanding extraction, and a Teams summary (.NET) | [functions-connectors-net-rfp-intake-sharepoint-teams](https://github.com/Azure-Samples/functions-connectors-net-rfp-intake-sharepoint-teams) |

## Authentication samples

[Built-in authentication with managed identity (.NET)](https://github.com/Azure-Samples/functions-connectors-net-builtinauth) demonstrates Connector Namespace callbacks using App Service built-in authentication and Entra ID.

## Related documentation

- [Use connectors in Azure Functions](https://learn.microsoft.com/azure/azure-functions/functions-connectors-overview)
- [Azure connectors overview](https://learn.microsoft.com/azure/connectors/overview)
- [Connector Namespace](https://learn.microsoft.com/azure/connectors/connector-namespace)
- [Azure Functions Hosted Skills](https://learn.microsoft.com/azure/azure-functions/functions-hosted-skills)

## Related repositories

- [Azure Functions Connector Extension](https://github.com/Azure/azure-functions-connector-extension)
- [Operations to Azure Functions signature mapping](https://github.com/Azure/azure-functions-connector-extension/blob/main/docs/operations-functions-match.md)
- [Connectors .NET SDK](https://github.com/Azure/Connectors-NET-SDK)
- [Connectors Python SDK](https://github.com/Azure/Connectors-python-sdk)
- [Connectors Node.js SDK](https://github.com/Azure/Connectors-nodejs-sdk)

## Contributing

This repository is an index; samples live in their own repositories. To propose a sample, open an issue or PR here with its repository link and a one-line description.

## Trademarks

This project may contain trademarks or logos for projects, products, or services. Authorized use of Microsoft trademarks or logos is subject to and must follow [Microsoft's Trademark & Brand Guidelines](https://www.microsoft.com/legal/intellectualproperty/trademarks/usage/general). Use of Microsoft trademarks or logos in modified versions of this project must not cause confusion or imply Microsoft sponsorship. Any use of third-party trademarks or logos is subject to those third parties' policies.
