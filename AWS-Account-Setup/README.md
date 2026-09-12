# ☁️ AWS Account Setup & Security Configuration

This project documents the complete process of creating and securing an AWS account for learning and hands-on cloud work.

It is designed for beginners who want to start their AWS journey safely, understand cloud account security, and prepare an environment for projects such as S3, EC2, IAM, and Bedrock.

---

## 👨‍💻 Project Author

**Abhishek Kumar**  
Aspiring Cloud & DevOps Engineer

---

## 📌 Project Overview

AWS account setup is the foundation of any cloud project. Before launching resources or learning services, it is important to create the account correctly, secure it with MFA, review billing, and understand the AWS Management Console.

This guide includes:

- AWS account creation steps
- Identity verification
- Billing configuration and Free Tier awareness
- Root user security
- MFA setup
- IAM basics
- Recommended security practices
- Screenshot-ready process documentation

---

## 🎯 Objectives

By completing this project, you will be able to:

- Create an AWS account safely
- Understand the AWS Console and AWS Root User
- Configure billing and security settings
- Enable MFA for stronger account protection
- Review IAM dashboard and access management basics
- Prepare your AWS environment for future hands-on projects

---

## 🧱 Prerequisites

Before starting this setup, make sure you have:

- A valid email address
- A working mobile number for verification
- A credit/debit card or acceptable billing method for identity verification
- Stable internet access
- Basic familiarity with browser-based account setup

> Note: AWS may require account verification before granting full access. This is a normal security step.

---

## 🛠️ AWS Concepts Covered

| Concept | Description |
|---|---|
| AWS Account | The root container for billing, identity, and services |
| Root User | The account owner with unrestricted access |
| IAM | Identity and Access Management for users, roles, and permissions |
| MFA | Multi-Factor Authentication for stronger login security |
| Billing Alerts | Notifications to monitor spending |
| Free Tier | AWS no-cost offers for eligible services |
| AWS Console | Browser dashboard used to manage AWS resources |

---

## 📚 Step-by-Step Guide

### Step 1: Open the AWS Sign-Up Page

Go to the AWS homepage and click on the Create an AWS Account button.

- Use a valid email address you can access
- Create a strong password
- Enter your account details carefully

#### Screenshot Placeholder

Add screenshot here:

- `./screenshots/01-create-account.png`

> Example: AWS sign-up page showing Create an AWS Account.

---

### Step 2: Fill in Account Information

Enter the required information such as:

- Account name
- Contact information
- Password
- Region preference

Double-check your email and contact info before continuing.

#### Screenshot Placeholder

- `./screenshots/02-account-details.png`

---

### Step 3: Verify Your Email Address

AWS will send a verification email to the address you entered.

Open the email and complete the verification step required by AWS.

#### Screenshot Placeholder

- `./screenshots/03-email-verification.png`

---

### Step 4: Verify Your Phone Number

AWS may request a phone verification step for additional identity confirmation.

- Enter your phone number
- Receive OTP or verification code
- Complete the verification process

#### Screenshot Placeholder

- `./screenshots/04-phone-verification.png`

---

### Step 5: Add Billing Information

AWS requires billing information to validate the account and activate services.

- Add a valid payment method
- Confirm the account is being set up securely
- Understand that AWS may perform a temporary verification check

#### Screenshot Placeholder

- `./screenshots/05-billing-information.png`

> Important: This is normal and does not mean you will be charged large amounts immediately. Always monitor your billing dashboard after setup.

---

### Step 6: Choose a Support Plan

For beginners, the Basic Support plan is typically sufficient.

- It is free
- It is adequate for learning and testing
- It keeps cost low while you explore AWS services

#### Screenshot Placeholder

- `./screenshots/06-support-plan.png`

---

### Step 7: Complete Identity Verification

AWS may ask for additional identity verification before full access is granted.

This step ensures account security and helps protect your environment from unauthorized access.

#### Screenshot Placeholder

- `./screenshots/07-identity-verification.png`

---

### Step 8: Sign In to the AWS Management Console

After the verification process is complete, sign in to the AWS Management Console.

From here you can:

- Search for AWS services
- Review billing and cost dashboards
- Manage IAM and security settings
- Start exploring resources

#### Screenshot Placeholder

- `./screenshots/08-aws-console.png`

---

### Step 9: Review Billing and Free Tier Dashboard

Open the Billing and Cost Management section from the AWS Console.

Review:

- Current billing status
- Free Tier usage
- Cost alerts
- Monthly usage summary

#### Screenshot Placeholder

- `./screenshots/09-billing-dashboard.png`

#### Recommended actions

- Set a billing alert
- Check your service usage regularly
- Be careful with services that may incur charges outside the Free Tier

---

### Step 10: Secure the Root User

The root user has complete administrative access to the account.

This account should be protected carefully because it can access everything in AWS.

#### Root user best practices

- Use a strong unique password
- Do not share the login details
- Keep account recovery email and phone number updated
- Avoid using root access for daily tasks

#### Screenshot Placeholder

- `./screenshots/10-root-user-security.png`

---

### Step 11: Enable Multi-Factor Authentication (MFA)

MFA adds an extra layer of protection to your AWS account.

How to enable MFA:

1. Go to the AWS account security settings
2. Navigate to the MFA section
3. Choose a virtual MFA app or security device
4. Scan the QR code or follow the setup instructions
5. Save the MFA configuration

#### Screenshot Placeholder

- `./screenshots/11-enable-mfa.png`

#### Why MFA matters

Even if someone learns your password, they still cannot log in without the MFA code.

---

### Step 12: Review the IAM Dashboard

IAM stands for Identity and Access Management.

This dashboard helps you manage:

- Users
- Groups
- Roles
- Policies
- Permissions

#### Screenshot Placeholder

- `./screenshots/12-iam-dashboard.png`

#### Key IAM principle

Follow the principle of least privilege: give users only the permissions they need and nothing more.

---

### Step 13: Create an IAM User for Daily Use

For normal work, use an IAM user instead of the root account.

This is safer and more organized.

Recommended flow:

1. Open IAM
2. Click Users
3. Add user
4. Set console or programmatic access
5. Attach a minimal policy
6. Save the user credentials securely

#### Screenshot Placeholder

- `./screenshots/13-create-iam-user.png`

---

## 🔐 Security Best Practices

Follow these best practices for all AWS learning projects:

- Use a strong and unique password for the root account
- Enable MFA on the root account
- Avoid using the root user for day-to-day operations
- Create a dedicated IAM user for regular activity
- Follow least-privilege access policies
- Review billing and cost alerts regularly
- Monitor Free Tier usage to avoid unexpected charges
- Keep account recovery information updated
- Never share AWS credentials in GitHub or public channels
- Never upload access keys or secrets to code repositories

---

## 🧾 Suggested AWS Setup Checklist

Use this list to verify your environment is ready:

- [ ] AWS account created
- [ ] Email verified
- [ ] Phone verified
- [ ] Billing information added
- [ ] Support plan selected
- [ ] Login to AWS Console completed
- [ ] Billing dashboard reviewed
- [ ] Root account secured
- [ ] MFA enabled
- [ ] IAM dashboard reviewed
- [ ] IAM user created for everyday use

---

## 📂 Recommended Project Folder Structure

```text
AWS-Account-Setup/
├── README.md
├── screenshots/
│   ├── 01-create-account.png
│   ├── 02-account-details.png
│   ├── 03-email-verification.png
│   ├── 04-phone-verification.png
│   ├── 05-billing-information.png
│   ├── 06-support-plan.png
│   ├── 07-identity-verification.png
│   ├── 08-aws-console.png
│   ├── 09-billing-dashboard.png
│   ├── 10-root-user-security.png
│   ├── 11-enable-mfa.png
│   ├── 12-iam-dashboard.png
│   └── 13-create-iam-user.png
└── notes/
```

---

## 📈 What I Learned

This AWS account setup project built the foundation for my cloud learning journey. It taught me that:

- Security must be planned from the beginning
- Billing awareness is essential for all AWS usage
- MFA reduces risk significantly
- IAM is the center of access control and governance
- A healthy AWS account is more than just resource creation; it is about safe and responsible usage

---

## 🎓 Key Takeaways

### Security First
Protect your AWS root account and enable MFA immediately.

### Cost Awareness
Monitor bills, usage, and budget alerts before creating any resource.

### Least Privilege
Use IAM users and minimal permissions instead of broad access.

### Build Step-by-Step
Start small, test carefully, and expand your AWS knowledge gradually.

---

## 🚀 Next Steps

After configuring the AWS account, the next projects can include:

- AWS S3 Static Website Hosting
- IAM policy practice
- EC2 instance deployment
- CloudWatch monitoring
- VPC and networking basics
- Amazon Bedrock exploration

---

## ✅ Final Notes

This project lays the groundwork for a secure and professional AWS learning environment. Once your account is configured correctly, you can confidently move into more advanced hands-on cloud projects without exposing your environment to unnecessary risk.

---

*Built and maintained for AWS learning and cloud security practice.*
