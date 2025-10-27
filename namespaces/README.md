# Namespace Requests

## How to Request a Namespace

1. Copy the template below
2. Replace `TEAM_NAME` with your team name
3. Replace `ENVIRONMENT` with dev/staging/prod
4. Save as `namespaces/ENVIRONMENT/TEAM_NAME-namespace.yaml`
5. Create a Pull Request with your changes

## Template

```yaml
apiVersion: v1
kind: Namespace
metadata:
  name: TEAM_NAME-ENVIRONMENT
  labels:
    team: TEAM_NAME
    environment: ENVIRONMENT
    managed-by: platform-team
  annotations:
    team.contact: "team-email@company.com"
    purpose: "Brief description of what this namespace is for"
---
apiVersion: v1
kind: ResourceQuota
metadata:
  name: TEAM_NAME-ENVIRONMENT-quota
  namespace: TEAM_NAME-ENVIRONMENT
spec:
  hard:
    requests.cpu: "2"
    requests.memory: 4Gi
    limits.cpu: "4"
    limits.memory: 8Gi
    persistentvolumeclaims: "4"
    services: "5"
    secrets: "10"
    configmaps: "10"
---
apiVersion: v1
kind: LimitRange
metadata:
  name: TEAM_NAME-ENVIRONMENT-limits
  namespace: TEAM_NAME-ENVIRONMENT
spec:
  limits:
  - default:
      cpu: 500m
      memory: 512Mi
    defaultRequest:
      cpu: 100m
      memory: 128Mi
    type: Container
