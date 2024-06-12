![image](https://github.com/hhphu/Cloud/assets/45286750/3cb0551d-3828-4b40-8854-250a191ac3e5)

# Introduction
In this post, I will go over how to distribute the website using CloudFront. AWS CloudFront not only helps us implement HTTPS protocol for our website but also speeds up the content delivery.
To learn more about CloudFront, you can read this [article](https://aws.amazon.com/blogs/networking-and-content-delivery/amazon-s3-amazon-cloudfront-a-match-made-in-the-cloud/).

# Certificates issuance
First of all, I need to issue certificates for `hhphu.click` and `www.hhphu.click`, which can be done using **AWS Certificate Manager**. Also, make sure to select region `us-east-1` so that CloudFront can see the certificates.
1. Go to **Certificate Manager** > **Request**
2. Select **Request a public certificate** > **Next**
3. Enter `hhphu.click` in the **Fully qualified domain name** field.
4. Click **Add another name to this certificate**
5. Enter `www.hhphu.click` in the **Fully qualified domain name** field.
6. Leave the rest options as default > click **Request**

![image](https://github.com/hhphu/Cloud/assets/45286750/53a97a59-f5a1-4ce1-960d-0f9d0ad9b380)

An entry should be created when going to **AWS Certificate Manager > Certificates**

![image](https://github.com/hhphu/Cloud/assets/45286750/49e2305e-9d20-469c-92d0-24ecd4dad38d)

In order for AWS to issue certificate, I need to validate my ownership of the domains. Select the entry, then click **Create records in Route 53**

![image](https://github.com/hhphu/Cloud/assets/45286750/a766f30c-c6ea-4fcf-9055-8bb3c8c0b605)

Proceed to **Create records**

![image](https://github.com/hhphu/Cloud/assets/45286750/56911b27-505f-4997-bfca-5ff8602aee96)

This will take a bit for the certificates to be issued. Once the certificates are issued, proceed to **CloudFront**.


-----
# Distributing content using CloudFront
Go to AWS CloudFront and create a new distribution with the following selections:
- Original domain: S3 bucket for `hhphu.click` (it should be available from the dropdown)

![image](https://github.com/hhphu/Cloud/assets/45286750/e788d820-551b-434b-b637-805944834ce0)

- Origin access: Origin access control settings (recommended) > **Create new OAC**
    - Origin domain: S3 bucket for `hhphu.click`
    - Description: OAC for hhphu.click
    -  **Create**
 
![image](https://github.com/hhphu/Cloud/assets/45286750/b61607be-48f2-4a09-ac41-bcf63aed3412)
  
- Copy the policy so we can use it later for the `hhphu.click` S3 bucket. `(*)`
  
- Scroll down to the Default cache behavior, in the **Viewer protocol policy**, check **HTTPS only**

![image](https://github.com/hhphu/Cloud/assets/45286750/4d014937-dc75-49a2-bd93-d8546d0be367)

- Select **Do not enable security protections** for the WAF and Use only **North America and Europe** option for the Price class in Settings.

![image](https://github.com/hhphu/Cloud/assets/45286750/bef41d06-5a73-4c1f-99ea-3504b8260b9a)

- In the **Settings** section, select the certificate for the site
- Alternate domain name: hhphu.click

  ![image](https://github.com/hhphu/Cloud/assets/45286750/9f94e8ec-bb5f-487b-99e7-8d4382025722)

### Edit hhphu.click S3 bucket
- Go to the `hhphu.click` S3 bucket and edit its permissions:
- Replace the existing policy with the one we just created from the step `(*)` above
  
Repeat the above steps for `www.hhphu.click`:
- Original domain: S3 bucket for `www.hhphu.click` (it should be available from the dropdown)
- Origin access: Public
- Alternate domain name: www.hhphu.click

The final results should look like this

![image](https://github.com/hhphu/Cloud/assets/45286750/49a76785-eec9-42fd-b253-37e0bc9d6dae)

