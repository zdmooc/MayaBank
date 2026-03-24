# LLD Global

## 1. Objet

Ce document sert de charnière entre le HLD et les LLD détaillés.
Il fixe le vocabulaire commun, les environnements, les familles de composants et les écarts autorisés entre on-prem, AWS et Azure.

## 2. Environnements cibles

- sandbox
- build
- preprod
- prod

## 3. Zones logiques

- management
- shared-services
- business
- data

## 4. Objets transverses

- namespaces
- resource quotas
- limit ranges
- network policies
- ingress / exposure
- observability hooks
- secrets patterns

## 5. Découpage provider

- `onprem.md`
- `aws.md`
- `azure.md`

## 6. Règle de cohérence

Toute divergence provider doit rester une divergence d'implémentation, pas une divergence de modèle d'architecture.

## 7. Dette V1

- HA non détaillée
- GitOps encore au stade de trajectoire
- service mesh non retenu en V1
- hardening incomplet
