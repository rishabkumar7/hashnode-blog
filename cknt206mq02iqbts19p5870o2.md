# Adding custom domain and SSL certificate Azure Static Web Apps

Hello amazing people 👋

So we finally had our website running the last article. Oh not sure what I am talking about, check out the first part of the blog here 👇

%[https://blog.rishabkumar.com/how-easy-it-is-to-deploy-with-azure-static-web-apps]

Now let's setup a custom domain and make sure we have the SSL certificate for it.

## Setting up the custom domain

Let's navigate to the Static Web App that we created in the last article.

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1619104731566/QWexmG9uI.png)

And in the blade, you should see `Custom Domains` section. Let's click that

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1618930236001/52PyAFb9a.png)

Now, if we click on the `Add`, it will open a tab on the right side for you to add the custom domain name, for this demo I will be using `faced.rishab.cloud`.

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1619104948340/mMeCt5925.png)

At this point, we have to update our Domain Name provider, in my case it's [AWS-Route53](https://aws.amazon.com/route53/). So I will create a CNAME record in Route53 to point to that value provided in Azure Static Web App

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1619105115967/35d8dBMSv.png)

If you use a different domain provider, the UI for adding the CNAME record should still look pretty similar.

Now, if we click on `Validate` after adding the CNAME record, it should succeed.

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1619105217413/XE1VniJlX.png)

And after the validation has succeeded, click on add.

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1619105260249/VmR7TVzRt.png)

After few minutes of wait, you will see the domain is added:

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1619105591903/AvFgF7sAV.png)

Let's navigate to our site now!

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1619105700341/ZY587nKts.png)

Did you notice something 🤔?

Yes, it also got a SSL certificate for the site, Azure Static Web Apps provisioned a certificate. 

![SSL.gif](https://raleigh.teddslist.com/wp-content/uploads/2018/06/ssl-https-gif.gif)

That's all for this article!
Hope you found it helpful, please feel free to reach out if you have any concerns, my twitter - [@rishabk7](https://twitter.com/rishabk7)