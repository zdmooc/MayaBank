# MayaBank

MayaBank est un **dépôt de référence d’architecture, de gouvernance, de lab semi-exécutable et de pilotage FinOps** pour une **banque d’investissement fictive** spécialisée dans les **produits dérivés financiers**.

Le dépôt est conçu pour servir **cinq usages en parallèle** :

1. **comprendre** le socle Kubernetes / OKD et raisonner comme un architecte plateforme ;
2. **structurer** un dossier d’architecture crédible pour un contexte banque / marchés ;
3. **construire** progressivement une trajectoire vers un niveau **Architecte OpenShift Senior** ;
4. **réaliser** le projet pas à pas, en gardant un ordre clair entre vision, architecture, sécurité, coûts et exécution ;
5. **reprendre** le chantier plus tard sans perdre le fil grâce à une documentation ordonnée.

---

# 1. Finalité du dépôt

MayaBank n’est pas un simple dépôt de manifests, ni une maquette sans gouvernance.

C’est un dépôt conçu pour devenir à la fois :

- un **guide de compréhension** ;
- un **guide d’architecture** ;
- un **guide de réalisation** ;
- un **guide de reprise** ;
- un **support d’entretien, de comité d’architecture et de démonstration**.

L’objectif n’est pas seulement d’écrire des documents.  
L’objectif est de produire un dépôt que l’on peut **relire du début à la fin**, comprendre, challenger, puis **mettre en œuvre progressivement**.

---

# 2. Ce que MayaBank est, et ce que MayaBank n’est pas

## 2.1 MayaBank est

- un **dépôt documentaire + architecture** ;
- un **support de gouvernance d’architecture** ;
- un **lab semi-exécutable** ;
- un **support de runbooks** ;
- un **cadre de FinOps avancé** ;
- un **support de trajectoire OKD → OpenShift enterprise** ;
- un **fil conducteur de réalisation sprint par sprint**.

## 2.2 MayaBank n’est pas

- une vraie **plateforme bancaire de production** ;
- un produit applicatif prêt à déployer tel quel ;
- un simple dépôt YAML sans vision d’ensemble ;
- un TP Kubernetes isolé des sujets de sécurité, d’exploitation et de coûts ;
- une plateforme enterprise déjà terminée.

---

# 3. Positionnement technique général

## 3.1 Base technique retenue

La base de construction et d’apprentissage est :

- **OKD / Kubernetes open source**
- **on-prem + AWS + Azure**
- un **niveau semi-exécutable** : plus concret qu’un pur dossier documentaire, mais moins ambitieux qu’une vraie plateforme enterprise prête pour la production

## 3.2 Cible conceptuelle à maîtriser

La cible de raisonnement, d’entretien et de maturité visée reste :

- **OpenShift enterprise**
- gouvernance de plateforme
- GitOps
- sécurité renforcée
- observabilité structurée
- workloads stateful
- contraintes d’audit, de résilience et de pilotage des coûts

## 3.3 Pourquoi ce choix

Ce choix permet de :

- rester **100 % open source** sur la base du dépôt ;
- comprendre le **socle réel** sous la plateforme ;
- construire une trajectoire crédible vers une lecture **OpenShift enterprise** ;
- éviter de dépendre trop tôt de composants propriétaires ou trop complexes ;
- comparer **on-prem, AWS et Azure** sans perdre un modèle d’architecture commun.

---

# 4. Domaine métier simulé

MayaBank représente une **banque d’investissement** orientée :

- pricing de produits dérivés ;
- trade booking ;
- workflows d’approbation ;
- decisioning / risk scoring ;
- reporting réglementaire ;
- batch de fin de journée ;
- exposition API ;
- portail client institutionnel ;
- analytics, data platform et montée vers data/IA.

---

# 5. Domaines d’architecture couverts

Le dépôt est structuré autour de **cinq grands domaines**.

## 5.1 Platform

- cluster baseline
- namespaces / quotas / policies
- ingress / exposition
- topologie multi-environnements
- overlays on-prem / AWS / Azure

## 5.2 Shared Services

- Keycloak
- Kong
- Kafka
- observability
- patterns secrets / identité / intégration

## 5.3 Business Workloads

- IBM ODM
- PegaSystems
- portals
- batch / CronJobs
- APIs métiers

## 5.4 Data / AI Platform

- PostgreSQL
- MongoDB
- data pipelines
- vector database patterns
- ML serving patterns
- RAG / retrieval patterns
- analytics workers
- gouvernance Data/IA et coûts associés

## 5.5 Governance / Operations / FinOps

- ADR
- HLD / LLD
- runbooks
- sécurité
- showback / chargeback
- capacity planning
- quality gates
- design authority pack
- debt / issues / assumptions

---

# 6. Workloads couverts

## 6.1 Workloads métier et plateforme

Le dépôt couvre les workloads suivants :

- **IBM ODM** pour le decisioning ;
- **PegaSystems** pour le workflow et le case management ;
- **Kafka** pour l’event backbone ;
- **Kong API Gateway** pour l’exposition et la gouvernance API ;
- **observability stack** pour métriques, logs, supervision et diagnostic ;
- **client-portal-web** en mode stateless ;
- **client-portal-session** en mode stateful ;
- **PostgreSQL** pour les données relationnelles ;
- **MongoDB** pour les données orientées document ;
- **Keycloak** pour IAM/SSO ;
- **batch / CronJob** pour les traitements périodiques.

## 6.2 Workloads Data/IA

Le domaine Data/IA inclut :

- **data-pipelines** pour ingestion, transformation et enrichissement ;
- **vector-database** pour retrieval, knowledge et similarity search ;
- **ml-serving** pour exposition d’inférence ;
- **rag-patterns** pour recherche augmentée interne ;
- **analytics-workers** pour calculs, scoring et génération de vues enrichies.

---

# 7. Pourquoi la plateforme Data/IA est dans le même dépôt

La plateforme Data/IA n’est pas gérée dans un autre dépôt à ce stade, pour trois raisons :

1. une banque d’investissement moderne n’isole pas totalement data, IA, intégration, IAM, observabilité et coûts ;
2. l’objectif de MayaBank est d’apprendre à raisonner **plateforme de bout en bout** ;
3. le domaine Data/IA modifie fortement les choix de :
   - capacité,
   - stockage,
   - observabilité,
   - sécurité,
   - FinOps.

Le domaine **Data/IA** est donc traité comme un **pilier technique à part entière** du dépôt.

---

# 8. Ce que le dépôt doit prouver à la fin

À la fin, MayaBank doit démontrer que son auteur sait :

- structurer une **plateforme cible cohérente** ;
- relier **architecture, exploitation, sécurité et coût** ;
- raisonner **stateless / stateful / data / IA** ;
- intégrer **IAM/SSO**, **observability**, **API management**, **eventing** ;
- documenter des décisions d’architecture traçables ;
- comparer **on-prem, AWS et Azure** sans casser le modèle commun ;
- traduire une base **OKD / open source** vers une cible **OpenShift enterprise** ;
- tenir une discussion crédible en **entretien**, en **comité d’architecture** ou en **design authority**.

---

# 9. Arborescence logique du dépôt

Le dépôt est structuré pour pouvoir être **lu, enrichi et rejoué progressivement**.

## 9.1 Documents principaux

- `docs/vision/` : vision métier et principes d’architecture
- `docs/hld/` : High Level Design
- `docs/lld/` : Low Level Design
- `docs/adr/` : Architecture Decision Records
- `docs/security/` : sécurité, IAM, OIDC, compliance
- `docs/finops/` : cadre FinOps
- `docs/runbooks/` : exploitation
- `docs/governance/` : revue d’architecture, quality gates, risk register
- `docs/roadmap/` : trajectoire produit, plateforme, sécurité et sprints

## 9.2 Partes lab / plateforme / exécution

- `lab/` : topologies et exemples rejouables
- `platform/` : structuration logique des services et overlays
- `infra/` : Terraform, Ansible, scripts
- `gitops/` : Argo CD, Helm, Kustomize
- `cicd/` : Jenkins, GitHub Actions, quality gates
- `finops/` : modèles, rapports, dashboards
- `evidence/` : preuves, logs, screenshots, smoke tests
- `risks/` : assumptions, debt, issues, RAID log

---

# 10. Ordre de lecture recommandé

Si le dépôt est repris après interruption, il faut **lire avant d’agir**.

L’ordre de lecture recommandé est le suivant :

1. `README.md`
2. `docs/vision/Mayabank-Vision.md`
3. `docs/vision/Business-Capabilities.md`
4. `docs/vision/Architecture-Principles.md`
5. `docs/hld/HLD-MayaBank.md`
6. `docs/hld/HLD-Platform.md`
7. `docs/hld/HLD-Data-AI-Platform.md`
8. `docs/hld/HLD-Security.md`
9. `docs/hld/HLD-Data-Stateful.md`
10. `docs/hld/HLD-Integration-Eventing.md`
11. `docs/hld/HLD-FinOps.md`
12. `docs/lld/LLD-global.md`
13. `docs/lld/onprem.md`
14. `docs/lld/aws.md`
15. `docs/lld/azure.md`
16. `docs/roadmap/Product-Roadmap.md`
17. `docs/roadmap/Sprint-Plan.md`
18. `docs/adr/`
19. `docs/security/`
20. `docs/finops/`
21. `docs/governance/`
22. `docs/runbooks/`

---

# 11. Ordre officiel de construction

L’ordre de construction officiel du dépôt est le suivant :

1. `README` / vision / HLD principal
2. `LLD global + providers`
3. `shared-services`
4. `business workloads`
5. `data & stateful`
6. `data/IA platform`
7. `sécurité / IAM / OIDC / secrets`
8. `GitOps / CI/CD / quality gates`
9. `FinOps avancé`
10. `gouvernance / design authority`
11. `lab semi-exécutable / evidence`

Cet ordre doit être respecté pour éviter de détailler trop tôt des briques dépendantes d’un socle encore instable.

---

# 12. Roadmap de maturité

## V1 — socle crédible

- dépôt structuré
- vision et HLD
- LLD global et providers
- premiers workloads
- FinOps et gouvernance fondatrice
- Data/IA cadrée architecturalement

## V2 — industrialisation initiale

- observabilité baseline
- Ansible / pipelines documentés
- runbooks enrichis
- quotas / network policies / sécurité de base
- premiers patterns data pipelines et ML serving

## V3 — plateforme avancée

- GitOps
- stateful renforcé
- DR / backup
- showback / chargeback outillés
- vector database patterns et cost controls Data/IA

## V4 — enterprise-ready

- hardening
- conformité
- IAM mature
- audit logging
- mapping complet **OKD → OpenShift enterprise**
- gouvernance d’architecture consolidée

---

# 13. Sprints du projet

Le dépôt est pensé pour être construit **sprint par sprint**.

## Sprint 0 — cadrage

- README
- vision
- HLD principal
- ADR de fondation
- roadmap
- règles de vérité du dépôt

## Sprint 1 — plateforme

- HLD plateforme
- LLD global
- LLD on-prem / AWS / Azure
- topologie
- réseau
- exposition
- stockage

## Sprint 2 — shared services

- Keycloak
- Kong
- Kafka
- observability baseline
- secrets baseline

## Sprint 3 — business workloads

- ODM
- Pega
- portals
- batch

## Sprint 4 — data & stateful

- PostgreSQL
- MongoDB
- backup / restore
- storage patterns

## Sprint 5 — sécurité & IAM

- threat model
- IAM / OIDC / SSO
- policy as code
- compliance baseline

## Sprint 6 — GitOps / CI/CD

- Argo CD
- Helm / Kustomize
- Jenkins
- quality gates

## Sprint 7 — FinOps avancé

- tagging
- budgets
- showback / chargeback
- KPIs
- rightsizing

## Sprint 8 — gouvernance

- architecture review checklist
- quality gates HLD/LLD
- risk register
- design authority pack

## Sprint 9 — Data/IA avancée

- data pipelines
- vector database
- ML serving
- RAG patterns
- observability et cost controls Data/IA

## Sprint 10 — lab semi-exécutable

- kind / notes OKD
- namespaces / quotas / policies
- scripts de bootstrap et validation
- preuves minimales

---

# 14. FinOps avancé

Le dépôt intègre une logique **FinOps avancée**.

Le but n’est pas seulement de parler de coûts, mais de relier :

- coût,
- capacité,
- criticité,
- résilience,
- observabilité,
- exploitation,
- type de workload,
- choix de plateforme.

## 14.1 Axes FinOps couverts

- centres de coûts par domaine ;
- budgets par environnement ;
- coûts par produit ;
- coûts par namespace ;
- unit economics ;
- showback / chargeback ;
- coût de l’observabilité ;
- coût des workloads stateful vs stateless ;
- impact Data/IA sur compute, storage et logs ;
- lien entre criticité, résilience et coût.

## 14.2 Références principales

- `docs/finops/FinOps-Framework.md`
- `docs/finops/Tagging-Strategy.md`
- `docs/finops/Capacity-and-Cost-Model.md`
- `docs/finops/Showback-Chargeback.md`
- `docs/finops/Unit-Economics.md`
- `docs/finops/Environment-Budgets.md`

---

# 15. Règles de vérité du dépôt

C’est une règle majeure de MayaBank.

Chaque sujet doit toujours être classé dans l’une des trois catégories suivantes :

1. **documenté**
2. **semi-exécutable**
3. **cible future**

Ne jamais présenter comme réalisé ce qui n’est qu’un objectif futur.

Cette distinction doit rester visible dans :
- les HLD ;
- les LLD ;
- les runbooks ;
- les roadmaps ;
- les sujets FinOps ;
- les parties lab.

---

# 16. Règles d’écriture du dépôt

- documentation en **français**
- noms techniques, composants et objets en **anglais**
- un fichier = un objectif lisible
- chaque document doit préciser :
  - son objectif ;
  - son périmètre ;
  - ce qui est actuel ;
  - ce qui est cible ;
  - les hypothèses ;
  - les limites ;
  - les prochaines étapes

---

# 17. Règles de gouvernance du dépôt

- toute décision structurante passe par un **ADR**
- toute évolution de cible impactant la plateforme doit mettre à jour le **HLD**
- tout nouveau détail d’implémentation doit être porté dans un **LLD**
- toute dette connue doit être visible dans `risks/Technical-Debt.md`
- tout arbitrage non tranché doit apparaître dans `risks/Open-Issues.md`
- toute reprise de chantier doit commencer par lire :
  - `README.md`
  - `docs/roadmap/Sprint-Plan.md`
  - `docs/roadmap/Product-Roadmap.md`
  - `docs/governance/Decision-Log.md`
  - `risks/Open-Issues.md`
  - `risks/Technical-Debt.md`

---

# 18. Comment reprendre le dépôt si le chantier s’arrête

Ce `README.md` est volontairement dense pour servir de **document maître**.

Si le chantier s’interrompt, la reprise doit repartir de :

1. `README.md`
2. `docs/roadmap/Sprint-Plan.md`
3. `docs/roadmap/Product-Roadmap.md`
4. `docs/governance/Decision-Log.md`
5. `risks/Open-Issues.md`
6. `risks/Technical-Debt.md`

Puis :

- si la vision n’est plus claire : repartir de `docs/vision/`
- si la cible technique n’est plus claire : repartir de `docs/hld/`
- si la structure détaillée n’est plus claire : repartir de `docs/lld/`
- si une décision est floue : repartir de `docs/adr/`
- si le coût et la capacité dérivent : repartir de `docs/finops/`

---

# 19. Démarrage recommandé du chantier

Si le dépôt doit être repris ou densifié, suivre **cet ordre** :

1. challenger `docs/vision/Mayabank-Vision.md`
2. valider `docs/hld/HLD-MayaBank.md`
3. détailler `docs/hld/HLD-Platform.md`
4. verrouiller `docs/lld/LLD-global.md`
5. détailler `docs/lld/onprem.md`, `docs/lld/aws.md`, `docs/lld/azure.md`
6. traiter `docs/lld/workloads/keycloak.md`, `kong.md`, `kafka.md`
7. traiter `docs/lld/workloads/odm-decisioning.md` et `pega-workflow.md`
8. traiter `docs/lld/workloads/postgresql.md` et `mongodb.md`
9. traiter `docs/lld/workloads/data-ai/`
10. consolider `docs/security/*`
11. consolider `docs/finops/*`
12. compléter `docs/governance/*`
13. seulement après : renforcer `lab/`, `infra/`, `gitops/` et `cicd/`

---

# 20. Ce qu’il ne faut pas faire

- ne pas construire trop tôt un faux niveau enterprise sans socle ;
- ne pas détailler le multi-cloud avant d’avoir un modèle commun ;
- ne pas traiter les workloads stateful comme de simples workloads stateless ;
- ne pas séparer architecture et coût ;
- ne pas ajouter Data/IA comme simple annexe non intégrée ;
- ne pas documenter vaguement : chaque choix important doit être traçable.

---

# 21. Statut actuel du dépôt

**Statut : V2 fondatrice étendue**

Le dépôt contient :

- une structure complète ;
- les documents fondateurs principaux ;
- l’intégration du domaine **Data/IA** ;
- une trajectoire claire pour continuer sprint par sprint ;
- une base crédible pour compréhension, entretien, démonstration et réalisation progressive.

---

# 22. Références internes majeures

- `docs/hld/HLD-MayaBank.md`
- `docs/hld/HLD-Platform.md`
- `docs/hld/HLD-Data-AI-Platform.md`
- `docs/hld/HLD-Security.md`
- `docs/hld/HLD-FinOps.md`
- `docs/lld/LLD-global.md`
- `docs/adr/ADR-0011-okd-to-openshift-enterprise-mapping.md`
- `docs/finops/Capacity-and-Cost-Model.md`
- `docs/security/OIDC-SSO-Model.md`
- `docs/roadmap/Sprint-Plan.md`

---

# 23. Résultat attendu à terme

À terme, MayaBank doit pouvoir être utilisé de quatre façons :

- **comme dépôt de lecture** pour comprendre la plateforme ;
- **comme dépôt d’architecture** pour préparer un entretien ou un comité ;
- **comme dépôt de construction** pour réaliser progressivement un lab crédible ;
- **comme dépôt de reprise** pour continuer le chantier sans dépendre d’un contexte oral externe.