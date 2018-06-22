---
title: Azure Web Apps - With Own Domain & SSL
category: cloud
layout: post
---

**Prerequisites knowledge** : [Azure Web Apps - An Overview](https://www.beadevops.com/cloud/2018/06/20/azure-webapps/) , [Create free SSL certificates and save some bucks](https://letsencrypt.org/getting-started/)

By default, azure webapp endpoint URL looks like *https://yourappname.azurewebsites.net* once it has been deployed from App services. However, we can bind our own domain name with SSL termination through a tricky DNS and opensource way. Following are those steps,

1) Go to App service in Azure portal -> Select the web app service we built -> Choose **Custom domains / SSL settings** to play with domain / SSL related settings

   {% include figure.html image="https://drive.google.com/uc?export=view&id=14sUVRiiwchWr_Mz-Rn9M4lCll7zok4ky" caption="webapps - Custom domain name" width="567" height="297" %}

   {% include figure.html image="https://drive.google.com/uc?export=view&id=1nOZGlY1ed6KM-s7fdz04BR6EYVwF2TEF" caption="webapps - SSL Settings" width="567" height="297" %}  


- ### Custom Domain
    - We can go ahead either *buy domain* option if you aren't owned with any domains / select *Add hostname* and put our domain details over it . It is necessary to update these details, so that azure will start accepting any request related with that domain name.
        <center><h1>&darr;</h1></center>    
    - Final thing is DNS update, and it needs to be done from the registrar end for that particular domain name you have been added in azure. Go to registrar -> edit the DNS -> add CNAME record for that domain like below ( relace *appname* with the respecive app service you built )

        ```text
        www        CNAME       appname.azurewebsites.net
        ```
        <center><h1>&darr;</h1></center>
    - Finally call the webapp via your domain name, ie; **www.your_domain_name.com**

- ### SSL Certificate
    - Make sure we are in the right app service plan. Currently custom SSL binding support for Basic, Standard, or Premium tier plans. Check more about this via [app-service tiers](https://azure.microsoft.com/en-us/pricing/details/app-service/windows/).

    - SSL basics for a domain name were *Generate CSR with private keys -> contact SSL vendor with that CSR -> Get CRT & CA certificates -> Configure the CRT & CA using private keys in web applications such as apache/ nginx/ tomcat etc*.
        <center><h1>&darr;</h1></center>
    - CSR and private keys can be generate via openssl to request CRT & CA from SSL vendors. Here is the bash command for that and fill out the necessary details such as country/state/locality/organization/organizational unit & common name (*should be your domain name with or without www*)
        ```bash
        openssl req -new -newkey rsa:2048 -nodes -keyout your_domain_name.key -out your_domain_name.csr
        ```
        <center><h1>&darr;</h1></center>
    - Assume that we have CRT either through [Let's encrypt](https://letsencrypt.org/getting-started/) / other SSL vendor ways. Since we don't maintain infrastructure for azure webapps, we will go and upload these certificates in PFX format which contains bundle of *CRT, CA and the Private keys*. Here is the bash command for doing that
        ```bash
        openssl pkcs12 -export -out your_domain_name.pfx -inkey your_domain_name.key -in your_domain_name.crt -certfile CA_your_domain_name.crt
        ```
        <center><h1>&darr;</h1></center>
    - Now we have *PFX* formatted file - your_domain_name.pfx, let's upload it in azure webapps area

        {% include figure.html image="https://drive.google.com/uc?export=view&id=1qoWbHou8TgINnnz8I4Aq-3aIG_15mID8" caption="webapps - Custom domain name" width="567" height="297" %}

    
