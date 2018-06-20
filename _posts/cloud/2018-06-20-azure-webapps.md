---
title: Azure Web Apps - An Overview
category: cloud
layout: post
---

Azure Web app services are pretty direct forward to host your applications runs in any of the languages such as **.NET, Node.js, PHP, Java, Python & HTML** in a cloud ready basis. We really dont have to manage the infrastrture since it is cloud ready, secure and supports load balancing, autoscaling, and automated management. Applications run and scale with ease on Windows and Linux based environments and perform actions such as like continuous deployment from VSTS, GitHub, Docker Hub, and other sources, package management, staging environments, custom domain, and SSL certificates.

Let's deploy a Webapp and host some files on it in azure. Here are the steps we need to perform ,

1) Login to Azure portal -> Go to App services -> Choose Webapp from that list since we are going to use that
<center><h1>&darr;</h1></center>
2) Please fill out the necessary details such as App name, Subscription and which resource group it belongs to etc. You can also opt the Operating system and service plan/location for your application needs. Currently they have limited location availability when you opt OS for Linux/Docker, however windows they have muliple locations available.

   {% include figure.html image="https://docs.microsoft.com/en-us/azure/app-service/media/app-service-web-get-started-php/php-docs-hello-world-app-service-list.png" caption="web apps we deployed" width="567" height="297" %}


   {% include figure.html image="https://docs.microsoft.com/en-us/azure/app-service/media/app-service-web-get-started-php/php-docs-hello-world-app-service-detail.png" caption="webapps inner view" width="567" height="297" %}  


