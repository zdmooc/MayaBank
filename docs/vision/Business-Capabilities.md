# Business Capabilities

## 1. Capacités métier simulées

- client onboarding institutionnel
- trade capture
- pricing
- workflow d'approbation
- decisioning
- reporting réglementaire
- batch de fin de journée
- audit & compliance

## 2. Capacités techniques transverses

- IAM / SSO
- API Management
- event streaming
- persistance relationnelle
- persistance documentaire
- observabilité
- gouvernance de plateforme
- FinOps et capacité

## 3. Mapping capacités → workloads

| Capacité | Workload principal |
|---|---|
| Decisioning | IBM ODM |
| Workflow | PegaSystems |
| Event streaming | Kafka |
| API exposure | Kong API Gateway |
| Client access | client-portal-web / client-portal-session |
| Transactional persistence | PostgreSQL |
| Flexible reference data | MongoDB |
| Authentication / federation | Keycloak |
| Monitoring / logging | observability stack |
| End-of-day processing | batch / CronJob |
