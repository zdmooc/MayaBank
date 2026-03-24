# MayaBank Vision

## 1. Objet

MayaBank est une banque d'investissement fictive utilisée comme support de travail pour concevoir un dépôt d'architecture, de gouvernance et de lab semi-exécutable.

Le but n'est pas de simuler toute la finance de marché, mais de représenter un **contexte crédible** dans lequel on retrouve les contraintes qui intéressent un architecte plateforme senior :

- workloads critiques ;
- exigences de sécurité et de traçabilité ;
- arbitrages stateful vs stateless ;
- exposition API ;
- intégration IAM/SSO ;
- besoins batch et flux événementiels ;
- coûts, capacité, résilience et gouvernance.

## 2. Ambition

Ce dépôt doit permettre de progresser depuis :
- une bonne compréhension du socle Kubernetes / OKD ;
- vers une posture d'architecte capable de raisonner comme sur une cible OpenShift enterprise.

## 3. Positionnement

MayaBank est :
- un dépôt de **référence pédagogique sérieuse** ;
- un support d'**entretien / comité d'architecture** ;
- un support d'**industrialisation progressive**.

MayaBank n'est pas :
- une vraie plateforme de production ;
- un produit bancaire réel ;
- un dépôt limité à du YAML technique sans cadre d'architecture.

## 4. Axes de valeur

- clarté de la trajectoire
- cohérence HLD / LLD / ADR / runbooks / FinOps
- différenciation nette entre actuel, semi-exécutable et cible future
- capacité à reprendre le chantier dans le temps
