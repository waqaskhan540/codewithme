---
layout: post
title:  "Using Custom Domain for AWS API Gateway"
date:   2019-07-25 15:26:16 +0500
categories: api-gateway
---

In this blog post I will explain that how can we use a *custom domain* with our API running on *AWS API Gateway*

## Foreword

*AWS API Gateway* is a seamless *AWS* service which provides an intuitive interface to get your APIs up-and-running with very little configuration. With *API Gateway* we can easily forward our requests to either *lambda functions* or to a *web server* running on **EC2** instance using *HTTP Proxy*.

*API Gateway* creates an arbitrary URL which you can use to access your API resources, for example, after deploying your API through *API Gateway* you might be presented with a URL that looks similar to `https://b123abcde4.execute-api.us-west-2.amazonaws.com/{stage-name}`,
 but it is not very friendly and in most cases we want to use more friendly URL that is easy to remember and is also self-explainatory.

Well, the solution to the above problem is using *Custom Domains*, lets see how can we do that.

## Using Custom Domains with API Gateway

Before going through the required steps, I would make following few assumptions:

- You have a running/deployed API on *AWS API Gateway*
- You have a registered *Domain* and have necessary permissions to configure it.
- You already have an SSL Certificate for the *Domain* you want to use as a custom domain for your API.

### Steps to follow

1. Login to your *AWS Console* .

2. Goto *API Gateway* or search for *API Gateway* using the search bar.

3. On the *left panel* choose **Custom Domains**.

4. Now click *Create Custom Domain Name*, this will open up a form.

5. For **Procol** choose *HTTP*.

6. Enter the name of the *Domain* i.e. `www.example.com` (note that the domain should be exactly same which you have the SSL certificate for).

7. Choose any of the **TLS Security Policy**.

8. For *endpoint configuration* choose **Regional**.

9. Choose your *ACM Certificate* for the Domain.

10. Click **Save** , this will create a custom domain and will show the details of it, now click **Edit**.

11. Provide Base path mappings i.e. if you provide `/api` as a base path then your `API` will be available at `www.yourdomain.com/api` which means that you will have to append the base path with your base URL. If you leave it empty then the `API` will be served on the base URL i.e. `www.yourdomain.com`.
Based on your needs give a **path** and choose name of your *API Gateway* that you want to use and then choose the relevant *stage* as well and click **Save**.

12. Now copy **Target Domain Name** from the dialog box shown.

13. Goto **Route53** (In case you are using Route53 as your domain registrar, else make upcoming changes in your respective DNS provider) and then goto **Hosted Zones**, choose your **Domain**.

14. Click **Create Record Set** and on the right hand side provide the domain name that you want to use (must be same as the one used to create a custom domain).

15. Choose **Yes** for **ALIAS**.

16. Paste the value in the text box below and click **Save Record**, thats it. Your API should now be accessible through your **Custom Domain**.