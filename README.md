# terraform-cloud-function-api

> Deploy a Node.js API on Google Cloud Functions using Terraform

## Prerequisites

- `terraform`
- `node` (latest version supported by [Cloud Functions](https://cloud.google.com/functions/docs/concepts/nodejs-runtime))
- `gcloud`

## Develop

1. Write your code on `src/` and run:

```bash
# Run function locally
npm run dev
```

## Deploy

0. Create a Google Cloud account and set up Billing

1. Initialize the CLI

```bash
gcloud init
```

2. Create a new project

```bash
# Replace PROJECT_ID with your Project ID.
gcloud projects create PROJECT_ID --name="My App"
```

3. Set the project as default

```bash
gcloud config set project PROJECT_ID
```

4. Enable billing

```bash
# List billing accounts
gcloud beta billing accounts list

# Link a billing account to project
gcloud beta billing projects link PROJECT_ID --billing-account=BILLING_ACCOUNT_ID
```

5. On `terraform/`, find and replace `PROJECT_ID` with your Project ID.

6. Deploy 🤞

```bash
cd terraform/

terraform init
terraform plan
terraform apply
```

You will see the function URL at the end of the result.

## Destroy

To shut everything down, run the following commands on this order:

```bash
# Delete all infrastructure
terraform destroy

# Optional: delete the project
gcloud projects delete PROJECT_ID
```
