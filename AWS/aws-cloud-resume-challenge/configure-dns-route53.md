# Configure domain name for the website

![image](https://github.com/hhphu/Cloud/assets/45286750/37211040-0efe-4002-89d2-7772cf338ff4)

In this post, I will go over how I registered a domain name for my website and have the S3 bucket point to my domain name.

## Register a domain
Go to **AWS Route 53**. On the dashboard, in the **Register domain** section, I input domain name for my website `hhphu.click` -> Click **Check** button

![image](https://github.com/hhphu/Cloud/assets/45286750/5170dd8b-4ca8-4f92-9bf4-c38f47cde464)

As shown in the image, the domain is available. I go ahead and select the domain and **Proceed to checkout**.
**Note:** If you plan to use this domain name from now on, you can keep the box **Auto-renew** checked. Otherwise, uncheck it.
Finish the checkout process.

While waiting for the process to complete (which takes a few minutes), we can proceed to [create S3 buckets](./deploy-s3.md) for the website.

<a id="dns-configuration"><h2> DNS Configuation using AWS Route 53 </h2></a>
