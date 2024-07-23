# Notes

## Overview to development @ACR and @Azure (23/07/2024)

### @Azure:

- Azure has many different services, such as VMs, VNets, AKS, Entra ID, Storage
  Accounts, and of course ACR. To provide Azure to users in a new region, it
  needs to be built up from multiple services built on top of each other.
- There is rough dependency graph, with Ring 3 services depending on Ring 2
  services, which depend on Ring 1 services, which depend on Ring 0 services.
- ACR is a Ring 1 service.
- Within Rings there are also dependency graphs. Curiously, ACR depends on AKS,
  which depends on ACR, a seemingly circular dependency.

### ACR Development:

- All ACR code is located in the `DevServices-ContainerRegistry-Service` repo.

### Portal Development

- Code is located in `src/ibiza/KraterExtension`
- The portal code is an extension that connects with the main Azure portal
  shell. This allows individual teams to develop their own extensions
  independently from other teams.
- The portal is written with Knockout, and is very slowly being migrated to
  React.
- The main portal team maintains shared UI components, the portal SDK, the
  portal CLI (`ap`), and other libraries.

**Acronyms:**

- ACR: Azure Container Registry
- AKS: Azure Kubernetes Service
- ACIS: Azure Customer Information Service (Geneva Actions)
- `ap`: azure portal
- SDK: Software Development Kit
- CLI: Command Line Interface
