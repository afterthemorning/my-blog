---
title: Introduction to Microservices - 微服务架构之旅
date: {{ date }}
tags:
  - cloud
  - 微服务架构
  - microservices
  - monolithic application
categories:
  - TECH
  - Microservices
banner: /gallery/Microservices-01.png
---

#### 简介&前言

**原作者:** Chris Richardson，是世界著名的软件大师，经典技术著作《POJOS IN ACTION》一书的作者，也是 cloudfoundry.com 最初的创始人，他的研究领域包括 Spring、Scala、微服务架构设计、NoSQL 数据库、分布式数据管理、事件驱动的应用编程等。Chris Richardson 与 Martin Fowler、Sam Newman、Adrian Cockcroft 等并称为世界十大软件架构师。Chris 与家人居住在美国加州奥克兰市的海滨小镇，他定期为企业提供微服务设计培训和实战项目的架构咨询服务。


#### 微服务架构系列有7篇:

##### 1. {% post_link Introduction_to_Microservices 微服务架构简介 %} (this article)  
##### 2. 构建微服务: 使用API Gateway
##### 3. 构建微服务: 微服务构架内的进程间通信
##### 4. 微服务构架的服务发现
##### 5. 微服务事件驱动的数据管理
##### 6. 微服务的部署策略
##### 7. 重构单应用到微服务

<!-- main body -->

* Microservices e-Book: [Microservices: From Design to Deployment](https://www.nginx.com/resources/library/designing-deploying-microservices/)

### Microservices 现状:

当下微服务引起广泛关注，成为文章、博客、社交媒体讨论和大会演讲的热点; 在 Gartner 的"Hype Cycle"中也正迅速排名靠前。与此同时,在软件社区也有一些人们认为微服务并非新事物。

反对者认为微服务只是 SOA （Service Oriented Architecture）的二度包装。然而，无论是追捧还是质疑，微服务架构模式拥有显著优势, 特别是涉及到敏捷开发和交付使复杂的企业应用程序时。

** 本文是微服务架构系列的第一篇：主是介绍了微服务设计，构建以及部署。**
你将进一步了解和走近微服务构架，并且比较分析它与传统单体应用架构模式. 本系列将会讲解到微服务架构的各种构成要素。还将了解到微服务架构的优势和弊端，并且是否对你的项目有帮助，和如何使用它。

* 个人觉得既然这个技术架构，这么火爆，了解一下也不是坏事情，所以一起来看看吧。

<!--more-->

### Building Monolithic Applications - 构建单体应用

首先，想象一下假如我们要新开发一款以"Uber" & "Hailo"进行竞争为目的打车软件，我们经过一系列的筹备会议和需求收集之后，我们会创建一个新项目，或者通过Rails, Spring Boot, Play, or Maven等进行开发。此全新APP应该是一个[六边形架构](http://www.infoq.com/news/2014/10/exploring-hexagonal-architecture)。

如下图所示:

{% asset_img microservices-part1-1_monolithic-architecture.png  monolithic-architecture %}

此应用的核心区域是：业务逻辑，它是由定义服务、域对象和事件的模块来实现的。包围核心区域的是各种适配接口与外部交互。例如：数据库访问组件，消息组件，以及Web UI和对外提供的API.

尽管有着逻辑化的模块架构，整个应用还是被整体的打包和部署.
实际的格式需要依赖于整个应用的开发语言和框架，例如：一部分Java应用程序通常都是被打包成WAR包，并且部署到Tomcat或Jetty服务容器中.
另一部分Java应用程序则是被打包成能够自执行的JARs格式. 与此类推，Rails和Node.js应用则被打包成一个目录结构.

此类应用的编写风格已经是非常普遍了，主要是因为现在的IDEs工具都注重于构建单体应用。此类应用也非常便于测试。我们可以非常轻松的实现End-to-End的测试，以及通过Selenium进行UI测试。单体应用部署也非常方便，一般来说，我们只需要复制打包好的程序到服务器即可，我们也可能通过复制多份程序并行运行，进行负载均衡。如果是项目早期还是非常有效的。

### Marching Towards Monolithic Hell - 迈向单体应用的地狱


非常不幸，对于单体应用有着巨大的局限性，一个成功的应用都有着一个习惯 - 经过久而久之的成长与更新，最终都会变的非常庞大。在每一个小阶段（Sprint）中，我们的开发团队都会实现小功能，增加许多行代码。然后，经过几年以后，我们的小而简单的应用程序将会变的异常巨大。举个栗子来说：
我最近和一个编写依赖分析工具的开发者交流，他正在开发一款分析工具，来分析他们应用（包括几百万行代码）中的几千个 JARs 的依赖。我肯定花了大量的开发人员的共同努力多年来创建这样的"野兽"。

一旦我们的应用程序变成一个庞大，复杂的单体应用时，我们的开发团队将会处于一个非常痛苦的世界，尝试任何敏捷开发和交付都将陷入困境。最主要的问题在于此时的应用已经变得极其复杂。它会复杂且庞大到任何一个开发者都无法完全理解了。因而造成的结果是，修复Bugs和实现一些新功能变的非常困难和花费更多的时间。更多的是，这一趋势会逐渐变成（水准）**螺旋式下跌**。如果基础代码（Codebase)非常难以理解，也很难做出正确的改变，直至最后我们会深陷庞大的、且无法估量的泥淖之中 - [big ball of mud](http://www.laputan.org/mud/) - http://www.laputan.org/mud。


待续....


### Microservices – Tackling the Complexity - 应付单体应用复杂度
