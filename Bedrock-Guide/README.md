<div align="center">

<img src="https://img.shields.io/badge/AWS-Amazon%20Bedrock-FF9900?style=for-the-badge&logo=amazonaws&logoColor=white" />
<img src="https://img.shields.io/badge/GenAI-Enabled-4CAF50?style=for-the-badge" />
<img src="https://img.shields.io/badge/Status-Learning%20Project-brightgreen?style=for-the-badge" />
<img src="https://img.shields.io/badge/License-MIT-blue?style=for-the-badge" />

<br/><br/>

# ☁️ Amazon Bedrock Hands-on Guide

### A practical walkthrough for exploring Amazon Bedrock, enabling model access, and testing Generative AI use cases with AWS.

<br/>

[![Made with AWS](https://img.shields.io/badge/Made%20with-Amazon%20Web%20Services-232F3E?logo=amazonaws)](https://aws.amazon.com)
[![Generative AI](https://img.shields.io/badge/Generative-AI-6C63FF?logo=amazonaws&logoColor=white)](https://aws.amazon.com/bedrock/)
[![Python](https://img.shields.io/badge/Python-3776AB?logo=python&logoColor=white)](https://www.python.org/)

</div>

---

## 📌 Table of Contents

- [📖 Project Overview](#-project-overview)
- [🏗️ Architecture](#️-architecture)
- [✅ Prerequisites](#-prerequisites)
- [🪜 Step-by-Step Setup](#-step-by-step-setup)
  - [Step 1: Sign in to AWS Console](#step-1-sign-in-to-aws-console)
  - [Step 2: Open Amazon Bedrock](#step-2-open-amazon-bedrock)
  - [Step 3: Request Model Access](#step-3-request-model-access)
  - [Step 4: Create IAM Permissions](#step-4-create-iam-permissions)
  - [Step 5: Test the Model in the Console](#step-5-test-the-model-in-the-console)
  - [Step 6: Use Bedrock via Python SDK](#step-6-use-bedrock-via-python-sdk)
- [🗂️ Project Files](#️-project-files)
- [💡 Best Practices](#-best-practices)
- [🚨 Troubleshooting](#-troubleshooting)
- [📚 Useful Resources](#-useful-resources)
- [👤 Author](#-author)

---

## 📖 Project Overview

This project is a practical introduction to Amazon Bedrock, AWS’s fully managed service for building generative AI applications with foundation models from leading AI providers.

The goal is to help a developer or learner:

- understand how Amazon Bedrock works,
- enable model access in AWS,
- configure permissions safely,
- test a model from the AWS console,
- and call a model programmatically with Python.

This project is based on a hands-on learning workflow and is designed to be easy to follow for beginners exploring Generative AI on AWS.

> 💡 Amazon Bedrock gives you access to foundation models from Anthropic, Meta, Mistral, AI21, Cohere, Stability AI, and more through a single AWS-native experience.

---

## 🏗️ Architecture

```text
User / Developer
      │
      ▼
AWS Management Console / Python SDK
      │
      ▼
Amazon Bedrock
      │
  ├── Model Access (Anthropic / Titan / others)
  ├── Security & IAM Policies
  ├── Foundation Model Runtime
  └── Generative AI Application Layer
```

This setup is simple but powerful:

- AWS account is the security boundary
- Bedrock handles model hosting and runtime access
- IAM controls who can use specific models
- Developers can test models in the console or via API calls

---

## ✅ Prerequisites

Before starting, make sure you have the following:

| Requirement | Details |
|-------------|---------|
| AWS Account | Valid AWS account with billing enabled |
| IAM Access | Permission to open Bedrock and configure IAM |
| Region Support | Choose a supported region like `us-east-1` |
| Python | Python 3.9+ recommended |
| Boto3 | Install via `pip install boto3` |
| Browser | Modern browser with access to AWS Console |

> ⚠️ Some models are region-specific. If a model is unavailable, switch to a supported AWS region.

---

## 🪜 Step-by-Step Setup

> 📸 The screenshots below are embedded directly from the original LinkedIn post for the Bedrock walkthrough.

### Step 1: Sign in to AWS Console

1. Open the AWS Management Console.
2. Sign in with your AWS account.
3. If this is your first time using Bedrock, confirm that your account is active and billing configuration is ready.

![Step 1 — AWS Console Login](https://media.licdn.com/dms/image/v2/D4D22AQH1h7xiz6fFtg/feedshare-shrink_800/B4DaB9F90DJYAc-/0/1788805111336?e=2147483647&v=beta&t=-npEF-cYRJc71WqZd21bmhFQhD4SggeMitEY2mF4Jdg)

---

### Step 2: Open Amazon Bedrock

1. In the AWS Console search bar, type `Bedrock`.
2. Select **Amazon Bedrock** from the search results.
3. Confirm you are in a supported region.

![Step 2 — Amazon Bedrock Console](https://media.licdn.com/dms/image/v2/D4D22AQENRJ2dLcWkfQ/feedshare-shrink_800/B4DaB9F92eHgAc-/0/1788805111486?e=2147483647&v=beta&t=VqjNSVSSInktkoJcpepDhHj4PeK5oonZPyls8q_8DUI)

---

### Step 3: Request Model Access

Amazon Bedrock does not allow every model to be used immediately. You must request access to the models you want.

1. Go to **Amazon Bedrock** → **Model access**.
2. Review the available foundation models.
3. Select the model(s) you need, for example:
   - Anthropic Claude
   - Amazon Titan
   - Meta Llama
   - Cohere Command / Embed
4. Click **Request model access**.
5. Wait for approval or access activation.

![Step 3 — Model Access Request](https://media.licdn.com/dms/image/v2/D4D22AQFQ-u7SRZa_7g/feedshare-shrink_800/B4DaB9F92LHgAg-/0/1788805111669?e=2147483647&v=beta&t=LfqyOnZrnSxtNXCcIi-Sza0vQYwubIKMO4q8YWZ_szw)

---

### Step 4: Create IAM Permissions

Bedrock usage should be controlled with least-privilege permissions.

A basic policy may allow invocation of Bedrock models:

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "BedrockInvoke",
      "Effect": "Allow",
      "Action": [
        "bedrock:InvokeModel",
        "bedrock:InvokeModelWithResponseStream",
        "bedrock:GetFoundationModel",
        "bedrock:ListFoundationModels"
      ],
      "Resource": "*"
    }
  ]
}
```

Recommended workflow:

1. Navigate to **IAM**.
2. Create a user or role for Bedrock access.
3. Attach a policy with the permissions above.
4. Use that role/user in CLI or app development.

![Step 4 — IAM Policy Setup](https://media.licdn.com/dms/image/v2/D4D22AQFKDnzY3Y5RDw/feedshare-shrink_800/B4DaB9F9vVKwAc-/0/1788805111005?e=2147483647&v=beta&t=5zs_ZeK6Ly762EqHpRXhsI6ICL4D9rfRU71u30QiquU)

---

### Step 5: Test the Model in the Console

Once access is granted, you can test directly in the Bedrock console.

1. Open **Amazon Bedrock**.
2. Select a model from the available list.
3. Choose the **Playground** tab or the model test interface.
4. Enter a prompt such as:

```text
Write a short product description for a cloud-based monitoring startup targeting developers.
```

5. Click **Run** and review the generated response.

![Step 5 — Console Playground](https://media.licdn.com/dms/image/v2/D4D22AQFc0tm3RRbFzA/feedshare-shrink_800/B4DaB9F9zAKIAc-/0/1788805111281?e=2147483647&v=beta&t=GpwmiSPxVsjUxaRz0oOXkx1A5CXxYtcEkUbAkRfbNrg)

---

### Step 6: Use Bedrock via Python SDK

Once the model is available, you can call it using the AWS SDK for Python (Boto3).

#### Install dependencies

```bash
pip install boto3
```

#### Example: Invoke Claude through Bedrock

```python
import boto3
import json

bedrock = boto3.client(
    service_name='bedrock-runtime',
    region_name='us-east-1'
)

model_id = 'anthropic.claude-3-sonnet-20240229-v1:0'

prompt = "Explain what Amazon Bedrock is in simple terms for a beginner."

body = json.dumps({
    "anthropic_version": "bedrock-2023-05-31",
    "max_tokens": 300,
    "messages": [
        {
            "role": "user",
            "content": [
                {"type": "text", "text": prompt}
            ]
        }
    ]
})

response = bedrock.invoke_model(
    modelId=model_id,
    body=body,
    contentType='application/json',
    accept='application/json'
)

result = json.loads(response['body'].read())
print(result['content'][0]['text'])
```

This example demonstrates how to:

- initialize the Bedrock runtime client,
- select a foundation model,
- send a prompt,
- and print the generated response.

![Step 6 — Python SDK Example](https://media.licdn.com/dms/image/v2/D4D22AQFc0tm3RRbFzA/feedshare-shrink_800/B4DaB9F9zAKIAc-/0/1788805111281?e=2147483647&v=beta&t=GpwmiSPxVsjUxaRz0oOXkx1A5CXxYtcEkUbAkRfbNrg)

---

## 🗂️ Project Files

This project folder is intentionally simple and beginner-friendly:

```text
Bedrock-Guide/
├── README.md
├── screenshots/
│   ├── 01-aws-console.png
│   ├── 02-bedrock-console.png
│   ├── 03-model-access.png
│   ├── 04-iam-policy.png
│   ├── 05-bedrock-playground.png
│   └── 06-python-bedrock.png
└── notes/
    └── optional project notes
```

> Replace placeholder screenshot names with your real screenshots once the project is documented.

---

## 💡 Best Practices

- Use least-privilege IAM policies for Bedrock access.
- Prefer dedicated IAM roles for app or automation use.
- Validate model access before building production workloads.
- Keep prompts and outputs secure, especially with sensitive data.
- Test in a supported region before deployment.
- Monitor model usage and budget alerts in AWS Billing.

---

## 🚨 Troubleshooting

### Model access not available

- Ensure you are in a supported region.
- Go to **Bedrock → Model access** and request access.
- Refresh the page after activation.

### Permission denied error

- Check IAM permissions for `bedrock:InvokeModel`.
- Verify the user/role is attached to the required policy.

### Region mismatch

- Some models are available only in certain regions.
- Change the AWS region and retry.

### Python client error

- Install Boto3 and verify AWS credentials.
- Run `aws configure` if needed.

---

## 📚 Useful Resources

- [Amazon Bedrock Documentation](https://docs.aws.amazon.com/bedrock/)
- [Amazon Bedrock Pricing](https://aws.amazon.com/bedrock/pricing/)
- [AWS IAM Documentation](https://docs.aws.amazon.com/IAM/latest/UserGuide/introduction.html)
- [Boto3 Documentation](https://boto3.amazonaws.com/v1/documentation/api/latest/index.html)

---

## 👤 Author

Abhishek Kumar

Aspiring Cloud & DevOps Engineer

This project is part of a hands-on AWS and Generative AI learning journey focused on practical implementation, security, and real-world cloud workflows.

---

⭐ Built and documented for hands-on learning with Amazon Bedrock.
