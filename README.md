# Platform Self-Service

This repository contains self-service resources for development teams.

## Structure

- `namespaces/`: Kubernetes namespace definitions
  - `dev/`: Development environment namespaces
  - `staging/`: Staging environment namespaces
  - `prod/`: Production environment namespaces
- `projects/`: ArgoCD project definitions
- `applications/`: ArgoCD application definitions

## How to Request Resources

1. Create a branch for your request
2. Add your resource definition in the appropriate directory
3. Submit a Pull Request
4. Once approved and merged, ArgoCD will automatically create the resources

## Example Workflow

### Requesting a New Namespace

1. Create a new branch:
   ```bash
   git checkout -b request-myteam-namespace

2. Add your namespace definition in the appropriate environment directory:
   # Copy a template or create a new file
   cp namespaces/dev/frontend-dev-namespace.yaml namespaces/dev/myteam-dev-namespace.yaml
   # Edit the file with your team's details

3. Commit and push your changes:
   git add namespaces/dev/myteam-dev-namespace.yaml
   git commit -m "Request namespace for myteam in dev environment"
   git push origin request-myteam-namespace

4. Create a Pull Request on GitHub

5. Once the PR is approved and merged, ArgoCD will automatically create your namespace!

