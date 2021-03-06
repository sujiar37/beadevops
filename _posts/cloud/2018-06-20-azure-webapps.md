---
title: Azure Web Apps - An Overview
date: 2018-06-20 00:00:00 +05:30
categories:
- Cloud
layout: post
comments: true
---

**Prerequisites knowledge : [Manage files via Git [clone, commit & push]](https://services.github.com/on-demand/downloads/github-git-cheat-sheet/ ),  [Access azure portal](https://azure.microsoft.com/en-in/services/app-service/), [how to use ftp for upload/download](https://wiki.filezilla-project.org/Using)** 


Azure Web app services are pretty direct forward to host your application runs in any of the languages such as **.NET, Node.js, PHP, Java, Python & HTML** in a cloud ready basis. We really dont have to manage the infrasturture since it is cloud ready, secure and supports load balancing, autoscaling & automated management. Applications run and scale with ease on Windows and Linux based environments and perform actions such as continuous deployment from VSTS/ GitHub/ Docker Hub and other sources etc. Also, it supports package management, staging environments, custom domain, and SSL certificates.

<!-- more -->

Let's deploy a Webapp and host some files on it in azure. Note that we are hosting static contents instead of Dynamic data, however it is possible when you opt *webapp+sql* package. Here are the steps we need to perform for hosting static contents ,

1) Login to Azure portal -> Go to App services -> Choose Webapp from the list it provides

   {% include figure.html image="https://drive.google.com/uc?export=view&id=10wbSJFg20uF0AtsVxopEnLvrsjKO6mJr" width="567" height="297" %}
<center><h1>&darr;</h1></center>
2) Fill out the necessary details such as App name, Subscription and the resource group which belongs to etc. We can also opt for the Operating system and service plan/location for our application needs. Currently they have limited region availability for Linux/Docker OS. However, they have muliple regions available for windows OS.

   {% include figure.html image="https://docs.microsoft.com/en-us/azure/app-service/media/app-service-web-get-started-php/php-docs-hello-world-app-service-list.png" caption="web apps we deployed" width="567" height="297" %}


   {% include figure.html image="https://docs.microsoft.com/en-us/azure/app-service/media/app-service-web-get-started-php/php-docs-hello-world-app-service-detail.png" caption="webapps inner view" width="567" height="297" %}  
<center><h1>&darr;</h1></center>
3) On the above image - *webapps inner view*, we could see all details related with our app services. **URL** represents an end point to call our application via browser, **git clone url & ftp url** can be used to access and deploy our website files.
<center><h1>&darr;</h1></center>
4) We can update our authentication details to upload/download website files via deployment tab. Finally the webfiles can access via the **URL endpoint [ https://Appname.azurewebsites.net/myfile.php ]**

{% include figure.html image="https://drive.google.com/uc?export=view&id=1Kop3xyW8hjgE2GcmtkcsqCoVbFydaGN_" caption="deployment credentials" width="567" height="297" %}


- #### Related Topics
    - [Azure Web Apps - With Own Domain & SSL](https://www.beadevops.com/cloud/2018/06/21/azure-webapps-owndomain/)

> Feature Topics : Stay tuned, How ?
<center><h1>&darr;</h1></center>
* Webapps can be Scaled and provide HA ?
* Different environments can be manageable with zero downtime using swap feature ?

