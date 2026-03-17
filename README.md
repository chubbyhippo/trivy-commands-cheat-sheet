# Trivy Commands Cheat Sheet

## Install / Verify

`trivy --version`

## Scan Filesystem

`trivy fs .`

`trivy fs /path/to/project`

`trivy fs --severity HIGH,CRITICAL .`

`trivy fs --ignore-unfixed .`

`trivy fs --format json --output trivy-report.json .`

## Scan Container Images

`trivy image nginx:latest`

`trivy image my-app:latest`

`trivy image --severity HIGH,CRITICAL my-app:latest`

`trivy image --ignore-unfixed my-app:latest`

`trivy image --format table my-app:latest`

`trivy image --format json --output trivy-image-report.json my-app:latest`

`trivy image --exit-code 1 --severity CRITICAL my-app:latest`

## Scan Git Repositories

`trivy repo https://github.com/example/project`

`trivy repo --branch main https://github.com/example/project`

## Scan Kubernetes / Manifests

`trivy k8s cluster`

`trivy config deployment.yaml`

`trivy config ./k8s`

## Scan IaC / Config

`trivy config .`

`trivy config --severity HIGH,CRITICAL .`

## Scan for Secrets

`trivy fs --scanners secret .`

`trivy image --scanners secret my-app:latest`

`trivy fs --scanners vuln,secret,misconfig .`

## Generate SBOM

`trivy fs --format cyclonedx --output sbom-cyclonedx.json .`

`trivy image --format cyclonedx --output image-sbom.json my-app:latest`

`trivy fs --format spdx-json --output sbom-spdx.json .`

## Vulnerability DB

`trivy image --download-db-only`

`trivy image --skip-db-update my-app:latest`

## Common Filters

`trivy image --pkg-types os my-app:latest`

`trivy image --pkg-types library my-app:latest`

`trivy image --severity LOW,MEDIUM,HIGH,CRITICAL my-app:latest`

## Output Formats

`trivy image --format table my-app:latest`

`trivy image --format json my-app:latest`

`trivy image --format template --template "@contrib/html.tpl" --output report.html my-app:latest`

`trivy fs --format sarif --output trivy.sarif .`

## CI/CD Friendly

`trivy fs --exit-code 1 --severity HIGH,CRITICAL .`

`trivy fs --exit-code 0 --severity HIGH,CRITICAL .`

`trivy fs --quiet .`

`trivy fs --no-progress .`

## Ignore File

`trivy fs --ignorefile .trivyignore .`

### Example `.trivyignore`

`CVE-2024-0001`

`CVE-2024-0002`

## Useful Examples

`trivy fs --scanners vuln,secret,misconfig .`

`trivy image --severity CRITICAL --exit-code 1 my-app:latest`

`trivy config --format json --output k8s-report.json ./k8s`

`trivy image --format template --template "@contrib/html.tpl" --output trivy-report.html my-app:latest`

## Quick Reference

`trivy fs .`

`trivy image my-app:latest`

`trivy config .`

`trivy repo https://github.com/example/project`

`trivy k8s cluster`

`trivy fs --severity HIGH,CRITICAL .`

`trivy image --ignore-unfixed my-app:latest`

`trivy fs --format json --output report.json .`

`trivy fs --exit-code 1 --severity HIGH,CRITICAL .`
