# CloudGate — versions publiées

Builds publics de CloudGate (migration et gouvernance Microsoft 365). Le code source est privé.

## Installer ou mettre à jour

Dans PowerShell :

```powershell
irm https://github.com/LiamJ74/CloudGate-releases/releases/latest/download/install.ps1 | iex
```

Le script télécharge le dernier MSI, vérifie son empreinte SHA-256 puis l'installe pour la machine
(Windows demande les droits administrateur). L'application se met ensuite à jour seule depuis ces versions.

Installation silencieuse (déploiement) : télécharger `CloudGate-x.y.z.msi` depuis
[Releases](https://github.com/LiamJ74/CloudGate-releases/releases) puis
`msiexec /i CloudGate-x.y.z.msi /qn UPDATESOURCE=https://github.com/LiamJ74/CloudGate-releases/releases/latest/download`.