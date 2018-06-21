---
title: Azure Web Apps - With Own domain name & SSL
category: cloud
layout: post
---

**Prerequisites knowledge : [Azure Web Apps - An Overview](https://beadevops.com/cloud/2018/06/20/azure-webapps/) , [Create free SSL certificates and save some bucks](https://letsencrypt.org/getting-started/)

By default azure webapp endpoint URL looks like https://yourappname.azurewebsites.net once it has been deployed from App services. However, we can bind our own domain name to this app service and even configure SSL with some tricky DNS & opensource way. So, let's jump on that and following are the steps,

1) Go to App service in Azure portal -> Select the web app service we build ->  Choose **Custom domains / SSL settings** to play with domain / SSL related settings

   {% include figure.html image="https://drive.google.com/uc?export=view&id=14sUVRiiwchWr_Mz-Rn9M4lCll7zok4ky" caption="webapps - Custom domain name" width="567" height="297" %}

   {% include figure.html image="https://drive.google.com/uc?export=view&id=1nOZGlY1ed6KM-s7fdz04BR6EYVwF2TEF" caption="webapps - SSL Settings" width="567" height="297" %}  