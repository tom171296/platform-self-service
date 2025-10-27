# Application Templates

## Web Application Template

To deploy a web application:

1. Request a namespace first (via PR in namespaces/ directory)
2. Copy `web-app-template.yaml`
3. Replace the following placeholders:
   - `TEAM_NAME`: Your team name
   - `APP_NAME`: Your application name
   - `ENVIRONMENT`: Target environment (dev/staging/prod)
4. Save as `applications/TEAM_NAME-APP_NAME.yaml`
5. Submit a Pull Request to this repository

## Requirements

- Your application repository must have a `k8s/` directory with Kubernetes manifests
- The target namespace must already exist (request via namespaces/ directory first)
- Your application must follow the resource limits defined in the namespace quota
- Your application repository must be accessible to ArgoCD

## Example

If the "mobile" team wants to deploy their "api" application to the dev environment:

1. First ensure `devops-mobile-dev` namespace exists
2. Copy the template and create `applications/mobile-api-dev.yaml`
3. Replace placeholders:
   - `TEAM_NAME`: mobile
   - `APP_NAME`: api
   - `ENVIRONMENT`: dev
4. Create a PR with the file
5. After merge, ArgoCD will deploy your application!
