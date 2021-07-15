# Best of Build 2021: Durable Functions

## Prerequisites
First, make sure you have the following installed on your machine:

- [.NET Core SDK 3.1](https://dotnet.microsoft.com/download/dotnet-core/3.1) or later. You can run dotnet --list-runtimes to check what is installed.
- [Azure Functions Core Tools 3.x](https://docs.microsoft.com/en-us/azure/azure-functions/functions-run-local?tabs=windows%2Ccsharp%2Cbash) or later. You can run func --version to check what is installed.
- [The Azure CLI 2.18.0](https://docs.microsoft.com/en-us/cli/azure/install-azure-cli) or later. You can run az --version to check what is installed.
- [PowerShell 7.1](https://docs.microsoft.com/en-us/powershell/scripting/install/installing-powershell?view=powershell-7.1) or later. You can check what is installed with pwsh --version. PowerShell is easy to install or update via dotnet tool install --global PowerShell or dotnet tool install --global PowerShell, respectively.

Also, you need an Azure subscription, to allocate and deploy the required resources.

## Testing and Debugging

For testing or debugging scenarios, there is support for emulation mode that eliminates the need for using an actual Event Hubs resource.

Since communication is "simulated in memory", this makes sense only for a single node. Also, it does not guarantee reliable execution.

The emulation mode can be selected by using a "pseudo-connection-string" instead of a real Event Hubs connection string:

| String | Interpretation |
| - | - |
| Memory | simulate both the queues and the partition states in memory | 
| MemoryF | simulate the queues in memory, but store the partition states in Azure Storage |

Example:
```json
{
  "EventHubsConnection": "Memory",
}
```

## References
https://microsoft.github.io/durabletask-netherite/#/README