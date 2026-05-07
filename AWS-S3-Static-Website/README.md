<div align="center">

<img src="https://img.shields.io/badge/AWS-S3-FF9900?style=for-the-badge&logo=amazons3&logoColor=white" />
<img src="https://img.shields.io/badge/Static_Hosting-Enabled-4CAF50?style=for-the-badge&logo=amazonaws&logoColor=white" />
<img src="https://img.shields.io/badge/Status-Live-brightgreen?style=for-the-badge" />
<img src="https://img.shields.io/badge/License-MIT-blue?style=for-the-badge" />

<br/><br/>

# ☁️ Hosting a Static Website on AWS S3

### A production-ready, end-to-end guide to deploying a static portfolio website using Amazon S3 — covering bucket creation, file uploads, static hosting configuration, IAM policy setup, and live deployment.

<br/>

[![Made with AWS](https://img.shields.io/badge/Made%20with-Amazon%20Web%20Services-232F3E?logo=amazonaws)](https://aws.amazon.com)
[![HTML](https://img.shields.io/badge/HTML5-E34F26?logo=html5&logoColor=white)](https://developer.mozilla.org/en-US/docs/Web/HTML)
[![CSS](https://img.shields.io/badge/CSS3-1572B6?logo=css3&logoColor=white)](https://developer.mozilla.org/en-US/docs/Web/CSS)
[![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?logo=javascript&logoColor=black)](https://developer.mozilla.org/en-US/docs/Web/JavaScript)

</div>

---

## 📌 Table of Contents

- [📖 Project Overview](#-project-overview)
- [🏗️ Architecture](#️-architecture)
- [✅ Prerequisites](#-prerequisites)
- [🪣 Step 1 — Create an S3 Bucket](#-step-1--create-an-s3-bucket)
- [📤 Step 2 — Upload Website Files](#-step-2--upload-website-files)
- [🌐 Step 3 — Enable Static Website Hosting](#-step-3--enable-static-website-hosting)
- [🔐 Step 4 — Configure Bucket Permissions](#-step-4--configure-bucket-permissions)
- [🚀 Step 5 — Access the Live Website](#-step-5--access-the-live-website)
- [🖼️ Live Preview](#️-live-preview)
- [💡 Key Takeaways](#-key-takeaways)
- [🛠️ Tech Stack](#️-tech-stack)
- [👤 Author](#-author)

---

## 📖 Project Overview

This project demonstrates the complete deployment of a **static portfolio website** on **Amazon S3** — one of AWS's most cost-effective and scalable object storage services. Unlike traditional web hosting, S3 eliminates the need for managing servers, making it ideal for static sites built with HTML, CSS, and JavaScript.

> 💡 **Why S3 for static hosting?**
> S3 offers 99.999999999% (11 nines) durability, global availability, near-zero infrastructure management, and a generous AWS Free Tier — making it perfect for portfolio sites, landing pages, and documentation sites.

**Live Endpoint Format:**
```
https://<bucket-name>.s3.amazonaws.com/<folder>/index.html
```

---

## 🏗️ Architecture

```
┌──────────────────────────────────────────────────────────────┐
│                        End User (Browser)                     │
└─────────────────────────────┬────────────────────────────────┘
                              │  HTTPS Request
                              ▼
┌──────────────────────────────────────────────────────────────┐
│              Amazon S3 — Static Website Hosting               │
│                                                              │
│   Bucket: portfolio-static-web-site-live  (us-east-1)        │
│   ┌──────────────────────────────────────────────────────┐   │
│   │  portfolio/                                          │   │
│   │  ├── index.html        (Home Page)                   │   │
│   │  ├── about.html        (About & Skills)              │   │
│   │  ├── contact.html      (Contact Form)                │   │
│   │  ├── resume.html       (Resume)                      │   │
│   │  ├── services.html     (Services)                    │   │
│   │  ├── project.html      (Projects)                    │   │
│   │  └── assets/           (CSS · JS · Images)           │   │
│   └──────────────────────────────────────────────────────┘   │
│                                                              │
│   ✅ Static Hosting: Enabled                                  │
│   ✅ Public Read Policy: s3:GetObject → Principal: *         │
│   ✅ Block Public Access: Disabled                           │
└──────────────────────────────────────────────────────────────┘
```

---

## ✅ Prerequisites

Before starting, make sure you have the following:

| Requirement | Details |
|-------------|---------|
| 🔑 AWS Account | Free Tier is sufficient |
| 🌍 AWS Region | `us-east-1` (N. Virginia) recommended |
| 📁 Static Website Files | HTML, CSS, JS, images |
| 🖥️ AWS Management Console Access | Via browser at [console.aws.amazon.com](https://console.aws.amazon.com) |

---

## 🪣 Step 1 — Create an S3 Bucket

An S3 bucket is the container that will store all of your website's files and serve them publicly.

**Steps:**

1. Sign in to the **AWS Management Console** → Navigate to **S3**
2. Click **"Create bucket"**
3. Enter a globally unique **Bucket name** — e.g., `portfolio-static-web-site-live`
4. Select your **AWS Region** (e.g., `us-east-1 — N. Virginia`)
5. Leave other settings at default → Click **"Create bucket"**

> ✅ A green confirmation banner will confirm the bucket has been successfully created.

<br/>

![Step 1 — Create S3 Bucket](screenshots/01-create-bucket.png)

---

## 📤 Step 2 — Upload Website Files

With the bucket created, the next step is to upload all your website files and folders.

**Steps:**

1. Open your newly created bucket
2. Click **"Upload"**
3. Use **"Add files"** and **"Add folder"** to select your entire project directory
4. Click **"Upload"** to begin the transfer

> ✅ All **148 files (37.2 MB)** uploaded successfully — every file shows **"Succeeded"** status.

<br/>

![Step 2 — Upload Files](screenshots/02-upload-files.png)

**Files uploaded include:**

| File | Type | Size |
|------|------|------|
| `index.html` | text/html | 4.2 KB |
| `about.html` | text/html | 12.1 KB |
| `contact.html` | text/html | 6.8 KB |
| `resume.html` | text/html | 4.2 KB |
| `services.html` | text/html | 13.4 KB |
| `project.html` | text/html | 4.7 KB |
| `assets/` | Folder | CSS, JS, Images |

---

## 🌐 Step 3 — Enable Static Website Hosting

By default, S3 buckets are not configured for web hosting. This step activates that capability.

**Steps:**

1. Go to your bucket → Click the **"Properties"** tab
2. Scroll down to **"Static website hosting"** → Click **"Edit"**
3. Select **"Enable"**
4. Set **Hosting type** to **"Host a static website"**
5. Set **Index document** to: `index.html`
6. *(Optional)* Set **Error document** to: `error.html`
7. Click **"Save changes"**

> ⚠️ **Important:** Enabling static hosting alone is not enough — content must also be made publicly readable (covered in Step 4).

<br/>

![Step 3 — Enable Static Hosting](screenshots/03-static-hosting.png)

---

## 🔐 Step 4 — Configure Bucket Permissions

By default, S3 buckets block all public access. To serve a website, we need to:
1. Disable the Block Public Access setting
2. Apply a Bucket Policy that allows public reads

### 4a. Disable Block Public Access

1. Go to your bucket → **"Permissions"** tab
2. Under **"Block public access (bucket settings)"** → Click **"Edit"**
3. **Uncheck** "Block all public access"
4. Click **"Save changes"** → Type `confirm` when prompted

### 4b. Generate & Apply the Bucket Policy

Use the **AWS Policy Generator** to build the correct IAM policy:

1. Navigate to the **Bucket Policy** editor → Click **"Policy generator"**
2. Configure the statement as follows:

| Field | Value |
|-------|-------|
| Policy Type | S3 Bucket Policy |
| Effect | Allow |
| Principal | `*` |
| AWS Service | Amazon S3 |
| Actions | `s3:GetObject` |
| ARN | `arn:aws:s3:::portfolio-static-web-site-live/*` |

> ⚠️ **Critical:** Append `/*` at the end of the ARN to apply the policy to **all objects** inside the bucket — not just the bucket itself.

<br/>

![Step 4a — Policy Generator](screenshots/04-policy-generator.png)

3. Click **"Add Statement"** → **"Generate Policy"**
4. Copy the generated JSON:

<br/>

![Step 4b — Policy JSON](screenshots/05-policy-json.png)

```json
{
  "Id": "Policy1718638803708",
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "Stmt1718638802061",
      "Action": [
        "s3:GetObject"
      ],
      "Effect": "Allow",
      "Resource": "arn:aws:s3:::portfolio-static-web-site-live/*",
      "Principal": "*"
    }
  ]
}
```

5. Paste this policy into the **Bucket Policy** editor → Click **"Save changes"**

---

## 🚀 Step 5 — Access the Live Website

With hosting enabled and permissions configured, your website is now publicly live.

**Verify your files are in place:**

![Step 5 — Bucket Objects](screenshots/06-bucket-objects.png)

**Access your website using the S3 endpoint URL:**

```
https://portfolio-static-web-site-live.s3.amazonaws.com/portfolio/index.html
```

> 💡 You can find the exact endpoint under: **Bucket → Properties → Static website hosting → Bucket website endpoint**

---

## 🖼️ Live Preview

The deployed portfolio website is fully functional and publicly accessible.

### 🏠 Home Page
> Displays the hero section with name, title, and call-to-action.

![Live Site — Home Page](screenshots/07-live-site-home.png)

### 👤 About Page — Skills Section
> Showcases the complete technology stack with icons.

![Live Site — About Page](screenshots/08-live-site-about.png)

**Pages available on the live site:**

| Page | Description |
|------|-------------|
| 🏠 Home | Hero section — Cloud Engineer introduction |
| 👤 About | Bio and skills grid |
| 📄 Resume | Work experience and education |
| 🛠️ Services | Cloud & DevOps services offered |
| 📦 Projects | Portfolio of completed projects |
| 📬 Contact | Contact form |

---

## 💡 Key Takeaways

> **1. S3 is production-ready for static websites**
> With 99.999999999% durability and built-in redundancy, S3 is more reliable than most self-managed servers for serving static content.

> **2. Three things must be configured for public access**
> Static hosting must be enabled, Block Public Access must be disabled, and a bucket policy with `s3:GetObject` must be applied — all three are required.

> **3. Always append `/*` to the bucket ARN in policies**
> Using just `arn:aws:s3:::bucket-name` applies the policy to the bucket itself. Adding `/*` applies it to every object inside — which is what web hosting requires.

> **4. Cost efficiency**
> S3 static hosting is extremely affordable — typically under $1/month for a personal portfolio with low-to-moderate traffic.

> **5. Next steps to improve this setup**
> Pair S3 with **AWS CloudFront** (CDN) for HTTPS, custom domains, and global edge caching. Add **Route 53** for a custom domain name.

---

## 🛠️ Tech Stack

| Technology | Role |
|-----------|------|
| ![AWS S3](https://img.shields.io/badge/AWS_S3-FF9900?logo=amazons3&logoColor=white) | Object storage & static website hosting |
| ![HTML5](https://img.shields.io/badge/HTML5-E34F26?logo=html5&logoColor=white) | Page structure and content |
| ![CSS3](https://img.shields.io/badge/CSS3-1572B6?logo=css3&logoColor=white) | Styling and layout |
| ![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?logo=javascript&logoColor=black) | Interactivity |
| ![AWS IAM](https://img.shields.io/badge/AWS_IAM_Policy-232F3E?logo=amazonaws&logoColor=white) | Bucket permissions and public access control |

---

## 👤 Author

<div align="center">

### Abhishek Kumar
**Cloud Engineer · AWS Solutions Architect Associate**

[![LinkedIn](https://img.shields.io/badge/LinkedIn-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white)](https://linkedin.com)
[![GitHub](https://img.shields.io/badge/GitHub-181717?style=for-the-badge&logo=github&logoColor=white)](https://github.com)
[![Twitter](https://img.shields.io/badge/Twitter-1DA1F2?style=for-the-badge&logo=twitter&logoColor=white)](https://twitter.com)
[![Instagram](https://img.shields.io/badge/Instagram-E4405F?style=for-the-badge&logo=instagram&logoColor=white)](https://instagram.com)

</div>

---

<div align="center">

**⭐ If you found this guide helpful, please consider giving this repository a star!**

*© 2024 Abhishek Kumar · All Rights Reserved*

</div>
