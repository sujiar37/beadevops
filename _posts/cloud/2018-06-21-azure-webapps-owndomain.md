---
title: Azure Web Apps - With Own domain name & SSL
category: cloud
layout: post
---

**Prerequisites knowledge** : [Azure Web Apps - An Overview](https://beadevops.com/cloud/2018/06/20/azure-webapps/) , [Create free SSL certificates and save some bucks](https://letsencrypt.org/getting-started/)

By default, azure webapp endpoint URL looks like *https://yourappname.azurewebsites.net* once it has been deployed from App services. However, we can bind our own domain name with SSL termination through a tricky DNS and opensource way. Following are those steps,

1) Go to App service in Azure portal -> Select the web app service we built -> Choose **Custom domains / SSL settings** to play with domain / SSL related settings

   {% include figure.html image="https://drive.google.com/uc?export=view&id=14sUVRiiwchWr_Mz-Rn9M4lCll7zok4ky" caption="webapps - Custom domain name" width="567" height="297" %}

   {% include figure.html image="https://drive.google.com/uc?export=view&id=1nOZGlY1ed6KM-s7fdz04BR6EYVwF2TEF" caption="webapps - SSL Settings" width="567" height="297" %}  
<center><h1>&darr;</h1></center>
2) We can go ahead either *buy domain* option if you aren't owned with any domains / select *Add hostname* and put our domain details over it . It is necessary to update these details, so that azure will start accepting any request related with that domain name.
<center><h1>&darr;</h1></center>
3) Final thing is DNS update, and it needs to be done from the registrar end for that particular domain name you have been added in azure. Go to registrar -> edit the DNS -> add CNAME record for that domain like below ( relace *appname* with the respecive app service you built )

```text
www     CNAME       appname.azurewebsites.net
```
4) Finally call the webapp via your domain name, ie; **www.your_domain_name.com**