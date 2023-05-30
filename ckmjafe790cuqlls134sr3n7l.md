---
title: "How easy it is to deploy with Azure Static Web Apps"
seoTitle: "How to deploy to Azure Static Web Apps"
seoDescription: "A look at Azure Static Web Apps and how to deploy to it."
datePublished: Sun Mar 21 2021 15:01:04 GMT+0000 (Coordinated Universal Time)
cuid: ckmjafe790cuqlls134sr3n7l
slug: how-easy-it-is-to-deploy-with-azure-static-web-apps
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1685407856062/5b8a087d-36ab-4a21-aff0-43dc2891eca7.png
tags: azure, web-development, cloud-computing, 100daysofcloud

---

Hello, amazing people 👋

Hope you all are doing well. For me, this week was exhausting due to work, but I am really happy since I got my Microsoft Azure AI Fundamentals Certification 😀

%[https://twitter.com/rishabk7/status/1371513830082220036?s=20] 

Let's get started with the [Azure Static Web Apps](https://azure.microsoft.com/en-us/services/app-service/static/).

## Intro to Azure Static Web Apps

What is Azure Static Web Apps, in Microsoft's words, "A modern web app service that offers streamlined full-stack development from source code to global high availability."

Some of the great featured I love about it is Visual Studio Code extension for local development, full repository analysis, and native GitHub workflows for CI/CD.

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1616260560002/cVTunppY_.png align="left")

## Deployment

Now, let's deploy a static web app with the same.

I had a face analysis web app that is written in JavaScript and HTML. Let's login to the Azure Portal and search for Static Web Apps:

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1616260740257/zlG_ecMXY.png align="left")

Now, let's click on the "NEW" to get started with a new Static Web App:

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1616260791440/23HNTMr33.png align="left")

You will see the following screen, where you will need to pick a Subscription and add the following details:

* Resource Group
    
* Name (for the app)
    
* Region
    

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1616260939865/8S4UpvVa3.png align="left")

For deployment, we will have to authenticate with our GitHub account:

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1616261104281/-Hz2ge_p0.png align="left")

After connecting GitHub, you should be able to pick the repository and branch for deployment.

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1616261257893/GvC1ArObt.png align="left")

Now, in the Build Details sections, you can see how many different options you have for Build Presets:

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1616261328919/wTMJsv6De.png align="left")

I will be choosing custom, since its a simple HTML/JS site. Also, I will be leaving other options blank, as I don't need them for now:

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1616261396386/x9owz9BI_.png align="left")

Click on the Review+Create, and that should take a few seconds to go through validation, and now you should be able to hit 'Create'

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1616261526198/QTAScbO9o.png align="left")

If we go to our GitHub repo, there should be a new directory: `.github/workflows/`

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1616261614959/tJ0mkLlDo.png align="left")

In this directory there is a YAML file that is created by the Static Web App to handle the automatic deployments, as we make changes to the project.

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1616261737600/69TxPcJaz.png align="left")

And you should be able to see the Build jobs under the Action tab in the GitHub repo:

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1616261792405/jsp_woQuy.png align="left")

In basic terms, this mean if we make change to our website, commit and push those changes to the branch or if we merge a pull request to the branch it will be deployed and we won't have to do anything manually. The GitHub action setup by Static Web App will take care of it.

## Results

Once, the Job finishes, you should be able to navigate to the URL:

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1616262085086/HuTqIb5pV.png align="left")

And voila!

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1616262111368/hfnobkl9Y.png align="left")

In the next blog, we will see how you can configure a custom domain and also get an SSL cert for your site.

Isn't it awesome 💜

If you have any questions, feel free to reach out [@rishabk7](https://twitter.com/rishabk7)