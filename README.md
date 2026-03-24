# MayaBank

Dépôt de référence pour une **banque d'investissement fictive** spécialisée dans les **produits dérivés financiers**, conçu pour apprendre, structurer et démontrer une trajectoire vers un niveau **Architecte OpenShift Senior**.

Le dépôt combine quatre dimensions :

1. **architecture** : vision, HLD, LLD, ADR, trajectoire OKD vers OpenShift enterprise ;
2. **gouvernance** : revues d'architecture, qualité documentaire, risk register, design authority pack ;
3. **lab semi-exécutable** : exemples locaux et overlays on-prem / AWS / Azure ;
4. **FinOps avancé** : showback, chargeback, budgets, KPIs, capacité vs coût.

## 1. Pourquoi ce dépôt existe

MayaBank n'est ni un simple TP Kubernetes, ni une plateforme de production réelle.

C'est un **dépôt d'apprentissage et de démonstration** qui doit permettre de :

- comprendre le **socle Kubernetes / OKD** sous-jacent ;
- raisonner comme un **architecte plateforme** ;
- comparer **on-prem, AWS et Azure** sans perdre un modèle d'architecture commun ;
- documenter la différence entre une base **open source** et une cible **OpenShift enterprise** ;
- structurer des **workloads critiques** d'un contexte banque / marchés ;
- intégrer les dimensions **stateful**, **IAM/SSO**, **observabilité**, **API Management**, **event streaming**, **batch** et **FinOps**.

## 2. Périmètre fonctionnel MayaBank

### 2.1 Domaine métier simulé

MayaBank est une banque d'investissement fictive orientée :

- pricing de produits dérivés ;
- trade booking ;
- workflows d'approbation ;
- risk scoring / decisioning ;
- reporting réglementaire ;
- batch de fin de journée ;
- portail client institutionnel.

### 2.2 Workloads couverts

Le dépôt couvre les workloads suivants :

- **IBM ODM** pour le decisioning ;
- **PegaSystems** pour les workflows et case management ;
- **Kafka** pour l'event backbone ;
- **Kong API Gateway** comme point d'entrée d'API ;
- **ELK / observability stack** pour logs, métriques et diagnostic ;
- **client-portal-web** en mode stateless ;
- **client-portal-session** en mode stateful ;
- **PostgreSQL** pour la persistance relationnelle ;
- **MongoDB** pour les données flexibles / référentiels / vues orientées document ;
- **IAM/SSO** via Keycloak ;
- **batch / CronJob** pour les traitements périodiques.

## 3. Cible technique retenue

### 3.1 Base open source

La base d'apprentissage et de construction est :

- **OKD / Kubernetes open source**
- **on-prem + AWS + Azure**
- **niveau semi-exécutable** : suffisamment concret pour un lab crédible, sans viser la production réelle

### 3.2 Mapping cible entreprise

La cible conceptuelle à maîtriser à terme reste :

- **OpenShift enterprise**
- gouvernance plateforme
- GitOps
- sécurité renforcée
- stateful enterprise
- conformité et auditabilité

Le mapping est détaillé dans :
- `docs/adr/ADR-0011-okd-to-openshift-enterprise-mapping.md`
- `docs/hld/HLD-Platform.md`
- `docs/roadmap/Platform-Roadmap.md`

## 4. Ce que ce dépôt doit prouver

À la fin, le dépôt doit démontrer que son auteur sait :

- produire un **HLD crédible** ;
- décliner ce HLD en **LLD cohérents** ;
- expliquer les différences **stateless vs stateful** ;
- raisonner **shared services vs business workloads** ;
- intégrer **IAM/SSO**, **API Gateway**, **eventing**, **data**, **observabilité** ;
- articuler **coût, capacité, criticité, gouvernance** ;
- traduire une base **OKD** vers une cible **OpenShift enterprise** ;
- tenir une discussion d'architecte en **entretien** ou en **comité d'architecture**.

## 5. Structure du dépôt

```text
MayaBank/
├── docs/            # vision, HLD, LLD, ADR, runbooks, sécurité, FinOps, gouvernance, roadmap
├── lab/             # exemples locaux, on-prem, AWS, Azure
├── platform/        # base, shared services, business workloads, overlays
├── infra/           # terraform, ansible, scripts
├── gitops/          # argocd, helm, kustomize
├── cicd/            # jenkins, github actions, quality gates
├── finops/          # modèles, rapports, tableaux de bord
├── risks/           # RAID, dette, hypothèses, points ouverts
└── evidence/        # preuves d'exécution et revues
```

## 6. Référentiel de lecture recommandé

L'ordre recommandé n'est pas aléatoire. Il permet de comprendre avant d'agir.

### Étape 1 — Vision et cadre
1. `docs/vision/Mayabank-Vision.md`
2. `docs/vision/Business-Capabilities.md`
3. `docs/vision/Architecture-Principles.md`

### Étape 2 — Architecture de haut niveau
4. `docs/hld/HLD-MayaBank.md`
5. `docs/hld/HLD-Platform.md`
6. `docs/hld/HLD-Security.md`
7. `docs/hld/HLD-Data-Stateful.md`
8. `docs/hld/HLD-Integration-Eventing.md`
9. `docs/hld/HLD-FinOps.md`

### Étape 3 — Architecture détaillée
10. `docs/lld/LLD-global.md`
11. `docs/lld/onprem.md`
12. `docs/lld/aws.md`
13. `docs/lld/azure.md`

Puis :
- `docs/lld/platform/*`
- `docs/lld/workloads/*`

### Étape 4 — Décisions structurantes
14. `docs/adr/*`

### Étape 5 — Exploitation et sécurité
15. `docs/runbooks/*`
16. `docs/security/*`

### Étape 6 — Coût, capacité, gouvernance
17. `docs/finops/*`
18. `docs/governance/*`
19. `docs/roadmap/*`

## 7. Méthode de construction incrémentale

Le dépôt est pensé pour être construit **par sprints**.

### Sprint 0 — cadrage
- vision
- README
- HLD principal
- ADR de fondation
- roadmap

### Sprint 1 — plateforme
- HLD plateforme
- LLD global
- LLD on-prem / AWS / Azure
- topologie, réseau, exposition, stockage

### Sprint 2 — shared services
- Keycloak
- Kong
- Kafka
- observability baseline
- secrets baseline

### Sprint 3 — business workloads
- ODM
- Pega
- portails
- batch

### Sprint 4 — data & stateful
- PostgreSQL
- MongoDB
- backup / restore
- storage patterns

### Sprint 5 — sécurité & IAM
- threat model
- IAM / OIDC / SSO
- policy as code
- compliance baseline

### Sprint 6 — GitOps / CI/CD
- Argo CD
- Helm / Kustomize
- Jenkins
- quality gates

### Sprint 7 — FinOps avancé
- tagging
- budgets
- showback / chargeback
- KPIs
- rightsizing

### Sprint 8 — gouvernance
- architecture review checklist
- quality gates HLD/LLD
- risk register
- design authority pack

### Sprint 9 — lab semi-exécutable
- kind / notes OKD
- namespaces / quotas / policies
- scripts de bootstrap et validation
- preuves minimales

## 8. Roadmap V1 → V4

### V1 — socle crédible
- structure complète du dépôt
- README complet
- vision
- HLD principal
- LLD global + providers
- premières ADR
- premiers runbooks
- socle FinOps
- placeholders propres pour la suite

### V2 — industrialisation initiale
- ansible
- CI/CD basique
- Prometheus / Grafana
- policies initiales
- runbooks consolidés
- budgets par environnement

### V3 — plateforme avancée
- GitOps
- patterns CSI / stateful renforcés
- HA control plane
- backup / restore et DR
- showback / chargeback améliorés

### V4 — posture enterprise-ready
- hardening
- compliance baseline
- IAM/OIDC mature
- audit logging
- design authority pack finalisé
- matrice d'écart OKD vers OpenShift enterprise

## 9. FinOps avancé — lecture rapide

Le dépôt intègre un angle **FinOps avancé** :

- centres de coûts par domaine ;
- budgets par environnement ;
- coûts par produit ;
- coûts par namespace ;
- unit economics ;
- showback / chargeback ;
- coût de l'observabilité ;
- coût des workloads stateful vs stateless ;
- relation entre criticité, résilience et coût.

Références de lecture :
- `docs/finops/FinOps-Framework.md`
- `docs/finops/Tagging-Strategy.md`
- `docs/finops/Capacity-and-Cost-Model.md`
- `docs/finops/Showback-Chargeback.md`
- `docs/finops/Unit-Economics.md`
- `docs/finops/Environment-Budgets.md`

## 10. Comment reprendre le dépôt si le chantier s'arrête

Ce README est volontairement **complet** pour que le travail puisse reprendre plus tard sans perte de contexte.

### 10.1 Vérifier l'état du dépôt
- lire `README.md`
- lire `docs/roadmap/Sprint-Plan.md`
- lire `risks/Open-Issues.md`
- lire `risks/Technical-Debt.md`
- lire `docs/governance/Decision-Log.md`

### 10.2 Reprendre au bon niveau
- si la vision n'est plus claire : repartir de `docs/vision/`
- si la cible technique n'est plus claire : repartir de `docs/hld/`
- si la structure des workloads n'est plus claire : repartir de `docs/lld/`
- si la décision d'architecture est floue : repartir de `docs/adr/`
- si le coût et la capacité dérivent : repartir de `docs/finops/`

### 10.3 Règle de poursuite
Toujours poursuivre selon ce triptyque :

1. **documenté**
2. **semi-exécutable**
3. **cible future**

Ne jamais présenter comme déjà implémenté ce qui n'est qu'une cible future.

## 11. Règles d'écriture du dépôt

- documentation en **français**
- noms techniques, composants et objets en **anglais**
- un fichier = un objectif lisible
- chaque document doit préciser :
  - son objectif ;
  - son périmètre ;
  - ce qui est **actuel** ;
  - ce qui est **cible** ;
  - les hypothèses ;
  - les limites ;
  - les prochaines étapes

## 12. Règles de gouvernance du dépôt

- toute décision structurante passe par un **ADR**
- toute évolution de cible impactant la plateforme doit mettre à jour le **HLD**
- tout nouveau détail d'implémentation doit être porté dans un **LLD**
- toute dette connue doit être visible dans `risks/Technical-Debt.md`
- tout arbitrage non tranché doit apparaître dans `risks/Open-Issues.md`

## 13. Démarrage recommandé du chantier

Si tu veux reprendre la construction dans l'ordre, suis exactement ce plan :

1. compléter ou challenger `docs/vision/Mayabank-Vision.md`
2. valider `docs/hld/HLD-MayaBank.md`
3. détailler `docs/hld/HLD-Platform.md`
4. verrouiller `docs/lld/LLD-global.md`
5. détailler `docs/lld/onprem.md`, `docs/lld/aws.md`, `docs/lld/azure.md`
6. traiter `docs/lld/workloads/keycloak.md`, `kong.md`, `kafka.md`
7. traiter `odm-decisioning.md` et `pega-workflow.md`
8. traiter `postgresql.md` et `mongodb.md`
9. consolider `docs/security/*`
10. consolider `docs/finops/*`
11. compléter `docs/governance/*`
12. seulement après : renforcer `lab/`, `infra/`, `gitops/` et `cicd/`

## 14. Ce qu'il ne faut pas faire

- ne pas construire trop tôt un faux niveau enterprise sans socle ;
- ne pas détailler le multi-cloud avant d'avoir un modèle d'architecture commun ;
- ne pas traiter les workloads stateful comme de simples déploiements stateless ;
- ne pas séparer architecture et coût ;
- ne pas documenter vaguement : chaque choix important doit être traçable.

## 15. Statut actuel du dépôt

**Statut : V1 fondatrice**

Le dépôt contient :
- une structure complète ;
- les documents fondateurs principaux ;
- des placeholders organisés pour la suite ;
- une trajectoire claire pour continuer incrémentalement.

La suite du chantier consiste à densifier chaque domaine sans casser la cohérence globale.
