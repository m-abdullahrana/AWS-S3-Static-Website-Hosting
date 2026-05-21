# AWS S3 Static Website Hosting

## Overview
This lab demonstrates how to host a publicly accessible static website using an Amazon S3 bucket.

## Cloud Components
* **Cloud Provider:** Amazon Web Services (AWS)
* **Service:** Amazon S3 (Simple Storage Service)
* **AWS Region:** Asia Pacific (Sydney) `ap-southeast-2`
* **Bucket Name:** `aws-demo-site-2026`

---

## Final Output
The live static website hosted and served directly via the S3 website endpoint:

![Final Website Launch](images/website-launch.jpg)

---

## Implementation Steps

### Step 1: Upload Assets
* Created the S3 bucket and uploaded all web files (`web.html`, `style.css`, and images) into the root directory.

![S3 Objects](images/s3-objects-list.png)

### Step 2: Enable Static Website Hosting
* Enabled **Static website hosting** under the **Properties** tab and set `web.html` as the index document.

### Step 3: Disable Block Public Access
* Turned off **Block *all* public access** under the **Permissions** tab to allow the website to be viewed publicly.

### Step 4: Apply S3 Bucket Policy
* Added the following JSON bucket policy to grant public read permissions (`s3:GetObject`) to all users:

```json
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Principal": "*",
            "Action": "s3:GetObject",
            "Resource": "arn:aws:s3:::aws-demo-site-2026/*"
        }
    ]
}
