# Step 2: Create the Google service account (API)

{% hint style="info" %}
**Recap**\
****You have downloaded the Terraform template declaring the [Google service account](https://cloud.google.com/iam/docs/service-accounts) for Snyk. Now you need to provision the infrastructure.
{% endhint %}

To scan a Google Cloud project, Snyk Cloud takes the permissions of a tightly-scoped Google service account that allows Snyk to scan the configuration of your project resources.

The service account you create is granted the following read-only Identity & Access Management (IAM) roles:

* [Security Reviewer](https://cloud.google.com/iam/docs/understanding-roles#iam.securityReviewer)
* [Viewer](https://cloud.google.com/iam/docs/understanding-roles)

Snyk Cloud's service account is granted the [Service Account Token Creator](https://cloud.google.com/iam/docs/understanding-roles#iam.serviceAccountTokenCreator) IAM role to enable it to generate short-lived credentials for your service account.

Additionally, Snyk Cloud has a mechanism in place to lock a service account to the Organization that onboards it. This is a security feature to ensure that nobody can guess a service account name and onboard it into a separate Organization to see those resources.

## Apply the Terraform

{% hint style="info" %}
Before you use the [Terraform CLI](https://www.terraform.io/downloads), ensure you [configure it to use your Google Cloud credentials](https://registry.terraform.io/providers/hashicorp/google/latest/docs/guides/getting\_started).
{% endhint %}

To provision the Google service account using Terraform:

1. In your terminal, navigate to the directory containing your `.tf` file.
2. Using the Terraform CLI, initialize the Terraform project:

```
terraform init
```

3\. Review and apply the Terraform plan:

```
terraform apply
```

4\. Enter `yes` when Terraform asks if you want to perform the actions.

Terraform then creates the Google service account. When it is finished, you'll see the following output:

```
Apply complete! Resources: 22 added, 0 changed, 0 destroyed.

Outputs:

service_account_email = "snyk-cloud-mt-us-abcd1234@my-project.iam.gserviceaccount.com"
```

Copy the service account email for use in [Step 3: Create and scan a Snyk Cloud Environment for Google (API)](step-3-create-and-scan-a-snyk-cloud-environment-for-google-api.md).

## What's next?

The next step is to create and scan the Snyk Cloud Environment.
