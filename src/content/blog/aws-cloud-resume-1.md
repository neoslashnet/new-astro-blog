---
title: "AWS Cloud Resume Challenge Part 1"
pubDate: 2023-09-01
intro: Part 1 of the AWS Cloud Resume Challenge. Building a Static S3 Website and Implementing CloudFront.
author: dg
tag: AWS, Cloud
image: ../../assets/cloudresume.jpg
---

# Introduction 

The Cloud Resume Challenge is a series of hands-on projects designed to help you build real-world cloud skills and demonstrate your expertise on your resume. This is one way to show and prove you have the skills necessary to deploy cloud services. I decided to take on the challenge for fun so I could go through the process and blog about it.

In this first part of the challenge, I go through how to build a static S3 website and implement CloudFront for faster delivery.

# **Step 1: Setting up an S3 Bucket**

The first step in building a static S3 website is to create an S3 bucket. S3 is Amazon Web Services' object storage service that provides industry-leading scalability, data availability, security, and performance. To create an S3 bucket:

1. Open the Amazon S3 console
    
2. Click the “Create Bucket” button
    
3. Give your bucket a unique name (Needs to be globally unique), select a region, and choose the default settings for all other options
    
4. Click the “Create” button to create your S3 bucket
    

![](https://res.cloudinary.com/dcu6gtw2y/image/upload/v1707174824/Blog%20Pictures/cloud_res_1_r2xk7z.png)

# **Step 2: Uploading Your Website Files to S3**

Once you have created your S3 bucket, it's time to upload your website files. You can either drag and drop your files into the S3 console or use the AWS CLI to upload the files.

I was able to snag [this template](https://www.free-css.com/free-css-templates/page288/global) and adjust index.html and update the images, etc. to suit my needs. After I made my changes, I uploaded the files.

![](https://res.cloudinary.com/dcu6gtw2y/image/upload/v1707174823/Blog%20Pictures/cloud_res_2_vtcwh7.png)

NOTE: If you look into the properties of the bucket, you may notice that the Static website hosting is DISABLED. This is fine as I am going to configure the CloudFront Origin access control settings so this does not need to be enabled.

# **Step 3: Implementing CloudFront**

Now that your website is hosted on S3, it's time to implement CloudFront for faster delivery. CloudFront is a content delivery network (CDN) service that speeds up the delivery of your static website by caching content at locations around the world (Edge locations). To implement CloudFront:

* Open the AWS Management Console
    
* Go to the CloudFront dashboard
    
* Click the “Create Distribution” button
    
* Choose your S3 bucket as the origin
    
* Configure the Origin access control settings and select "create control setting"
    
    ![](https://res.cloudinary.com/dcu6gtw2y/image/upload/v1707174819/Blog%20Pictures/3_md8lea.png)
    
    Give the control setting a name and configure it with the settings below and "create".
    
    ![](https://res.cloudinary.com/dcu6gtw2y/image/upload/v1707174819/Blog%20Pictures/4_co5dgi.png)
    
    Back on the distribution page, leave the default settings and then proceed to “Create distribution”.
    

![](https://res.cloudinary.com/dcu6gtw2y/image/upload/v1707174819/Blog%20Pictures/5_tgpbe7.png)

![](https://res.cloudinary.com/dcu6gtw2y/image/upload/v1707174820/Blog%20Pictures/6_vscodu.png)

After the “Distribution” is created, a bucket policy will be created and you will see a banner message indicating you need to update the bucket policy. Make sure to copy and update the bucket policy in the S3 bucket. Then Save Changes.

This is a sample of what the bucket policy should look like:

```json
{
    "Version": "2012-10-17",
    "Statement": {
        "Sid": "AllowCloudFrontServicePrincipalReadOnly",
        "Effect": "Allow",
        "Principal": {
            "Service": "cloudfront.amazonaws.com"
        },
        "Action": "s3:GetObject",
        "Resource": "arn:aws:s3:::<S3 bucket name>/*",
        "Condition": {
            "StringEquals": {
                "AWS:SourceArn": "arn:aws:cloudfront::<AWS account ID>:distribution/<CloudFront distribution ID>"
            }
        }
    }
}
```

The bucket policy setting is located under the "permissions" tab on the bucket. You need to select "edit" and paste it in.

![](https://res.cloudinary.com/dcu6gtw2y/image/upload/v1707174820/Blog%20Pictures/7_lzyuaj.png)

Save your changes to apply the bucket policy.

One thing I had to do for the website to work was go back to the CloudFront Distribution I created and update the Default root object to index.html.

![](https://res.cloudinary.com/dcu6gtw2y/image/upload/v1707174821/Blog%20Pictures/8_cexahj.png)

![](https://res.cloudinary.com/dcu6gtw2y/image/upload/v1707174822/Blog%20Pictures/9_xooklh.png)

After doing more reseach on this, I discovered that adding “index.html” as the default root object in the CloudFront distribution is essential for ensuring that visitors to the site can access the desired content without specifying the exact file name in the URL. By setting “index.html” as the default root object, CloudFront knows to look for this file and automatically serves it to the user. This eliminates the need for users to explicitly include “index.html” in the URL.

At this point, you can go to your Distribution and select Distribution domain name and copy it. Mine is [https://d3k83rr5rihesr.cloudfront.net](https://d3k83rr5rihesr.cloudfront.net)

That's it! The website works.

![](https://res.cloudinary.com/dcu6gtw2y/image/upload/v1707174822/Blog%20Pictures/10_kxdq1k.png)

NOTE: I am not mapping a custom domain to this project. If you want to do that, you can use AWS Route 53 to purchase a domain name and then create the necessary records for the Cloudfront Distribution.