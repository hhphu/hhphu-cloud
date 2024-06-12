![image](https://github.com/hhphu/Cloud/assets/45286750/3cb0551d-3828-4b40-8854-250a191ac3e5)

# Introduction
In this post, I will go over how to distribute the website using CloudFront. AWS CloudFront not only helps us implement HTTPS protocol for our website but also speeds up the content delivery.
To learn more about CloudFront, you can read this [article](https://aws.amazon.com/blogs/networking-and-content-delivery/amazon-s3-amazon-cloudfront-a-match-made-in-the-cloud/).

# Distributing content using CloudFront
Go to AWS CloudFront and create a new distribution
- Select the bucket we created above for the Original domain field
- Check **Origin access control settings (recommended)** option > click **Create new OAC**. Leave all the options as default and create a new OAC.

![image](https://github.com/hhphu/Cloud/assets/45286750/eecd4eea-bac5-4aa9-a8da-dfab9beb0da7)

- Scroll down to the Default cache behavior, in the Viewer protocol policy, check HTTPS only

![image](https://github.com/hhphu/Cloud/assets/45286750/4d014937-dc75-49a2-bd93-d8546d0be367)

- Select Do not enable security protections for the WAF and Use only **North America and Europe** option for the Price class in Settings.

![image](https://github.com/hhphu/Cloud/assets/45286750/bef41d06-5a73-4c1f-99ea-3504b8260b9a)

- Input `index.html` into the Default root object field.
- Leave everything else as default and create a new distribution.
- Once a new distribution is created, we should get yellow banner urging us to update the bucket policy

![image](https://github.com/hhphu/Cloud/assets/45286750/90736fba-97df-4a6f-a769-f3c0282a43c5)

- Go to the bucket's Permissions tab to update the policy

![image](https://github.com/hhphu/Cloud/assets/45286750/f7e96758-1645-4345-8478-2c2521c83d62)
