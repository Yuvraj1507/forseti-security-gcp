# Forseti Security Implementation (Personal Open-Source Project)

## Overview
Forseti Security is an open-source tool that helps secure Google Cloud Platform (GCP) environments by auditing IAM policies, scanning resources, enforcing security rules, and providing visibility into cloud security settings. This project involves implementing Forseti Security for a GCP organization, configuring policy enforcement, and integrating automated compliance checks.

## Features
- **Automated Cloud Security Auditing**: Continuously scans GCP resources for misconfigurations.
- **IAM Policy Monitoring**: Tracks access control changes and detects unauthorized modifications.
- **Policy Enforcement & Correction**: Ensures compliance with predefined security policies.
- **Logging & Alerting**: Provides visibility into policy violations and security threats.
- **Infrastructure as Code (IaC) Setup**: Uses Terraform for automated deployment.

## Technologies & Tools Used
- **Cloud Platform**: Google Cloud Platform (GCP)
- **Infrastructure as Code**: Terraform
- **Security Tools**: Forseti Security, IAM Analyzer
- **Automation & Scripting**: Bash, Python
- **Version Control**: Git, GitHub
- **Logging & Monitoring**: Stackdriver Logging, Cloud Functions

## Installation & Setup
### Prerequisites
1. Google Cloud Project with appropriate permissions.
2. Cloud Shell or a local machine with the Google Cloud SDK installed.
3. Terraform installed for infrastructure automation.
4. A GitHub repository for version control.

### Step 1: Clone Repository
```sh
git clone https://github.com/yourusername/forseti-security-project.git
cd forseti-security-project
```

### Step 2: Deploy Forseti Using Terraform
1. Initialize Terraform:
```sh
terraform init
```
2. Apply configuration:
```sh
terraform apply -auto-approve
```
3. Verify Forseti installation:
```sh
gcloud compute instances list --filter="name~forseti"
```

### Step 3: Configure IAM Policy Monitoring
1. Enable policy scanner:
```sh
gcloud projects add-iam-policy-binding forseti-security \
    --member=user:your-email@example.com \
    --role=roles/viewer
```
2. Run Forseti inventory:
```sh
forseti inventory create
```
3. Scan IAM policies:
```sh
forseti scanner run
```

### Step 4: Enable Alerts & Logging
1. Set up Stackdriver logging:
```sh
gcloud logging sinks create forseti-alerts \
    --destination=pubsub.googleapis.com/projects/YOUR_PROJECT_ID/topics/forseti-alerts
```
2. Subscribe to alerts:
```sh
gcloud pubsub subscriptions create forseti-alerts-subscription \
    --topic=forseti-alerts
```

## Use Cases
- **Monitoring Cloud IAM Policies**: Track access changes and enforce security best practices.
- **Automated Security Auditing**: Identify misconfigured resources and fix them proactively.
- **Policy Compliance Enforcement**: Enforce organization-wide security standards.
- **Real-Time Security Alerting**: Get notified of policy violations instantly.

## Enhancements & Future Improvements
- **CI/CD Integration**: Automate security scanning in a CI/CD pipeline.
- **Custom Security Rules**: Develop custom rules for specific GCP security policies.
- **Multi-Cloud Support**: Expand Forseti capabilities to support hybrid cloud environments.
- **Dashboards & Reporting**: Integrate with visualization tools like Grafana for better insights.

## Contributions
If you’d like to contribute, feel free to fork this repository, make improvements, and submit a pull request.

## License
This project is open-source and available under the [Apache 2.0 License](https://www.apache.org/licenses/LICENSE-2.0).

---
**Author:** Dalayi Yuvaraju  


