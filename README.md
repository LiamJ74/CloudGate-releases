# CloudGate — versions publiées

Builds publics de CloudGate (migration et gouvernance Microsoft 365). Le code source est privé.

## Serveur

```powershell
irm https://github.com/LiamJ74/CloudGate-releases/releases/latest/download/install-server.ps1 | iex
```

Installe le moteur en service Windows et le proxy HTTPS (Caddy), puis ouvre sur le serveur l'assistant de
configuration (`http://127.0.0.1:5181`) : connexion Microsoft 365, certificat, nom DNS et HTTPS, connexion Entra ID.

## Client (postes)

```powershell
irm https://github.com/LiamJ74/CloudGate-releases/releases/latest/download/install-client.ps1 | iex
# relié d'office à son serveur :
& ([scriptblock]::Create((irm https://github.com/LiamJ74/CloudGate-releases/releases/latest/download/install-client.ps1))) -ServerUrl https://cloudgate.contoso.com
```

L'application affiche la console du serveur appairé et garde un moteur local de secours si le serveur est injoignable.

Relier un poste : si le serveur utilise l'autorité interne de Caddy, installer d'abord sur le poste son certificat
racine (`https://<serveur>/api/proxy/root.crt`, magasin « Autorités de certification racines de confiance » de
l'ordinateur), créer un code dans la console du serveur › Paramètres › Postes appairés, puis installer le client avec
`-ServerUrl` et saisir le code au premier lancement.
Les scripts vérifient l'empreinte SHA-256 du MSI avant de l'installer (Windows demande les droits administrateur) ;
les produits se mettent ensuite à jour seuls depuis ces versions. Installation silencieuse : télécharger
`CloudGate-Server-x.y.z.msi` ou `CloudGate-Client-x.y.z.msi` depuis
[Releases](https://github.com/LiamJ74/CloudGate-releases/releases) puis `msiexec /i <paquet> /qn`.