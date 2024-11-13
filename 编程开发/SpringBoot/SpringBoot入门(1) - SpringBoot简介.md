# ▶SpringBoot入门(1) - SpringBoot简介

> 为什么有了SpringFramework还会诞生SpringBoot？简单而言，因为虽然Spring的组件代码是轻量级的，但它的配置却是重量级的；所以SpringBoot的设计策略是通过**开箱即用**和**约定大于配置** 来解决配置重的问题的。@pdai

- ▶SpringBoot入门 - SpringBoot简介
  - SpringFramework解决了什么问题，没有解决什么问题？
    - [SpringFramework解决了什么问题？#springframework解决了什么问题](https://help.aliyun.com/zh/yunxiao/user-guide/quickly-create-and-deploy-spring-boot-experience-applications?scm=20140722.S_help@@%E6%96%87%E6%A1%A3@@2797582.S_RQW@ag0+BB2@ag0+BB1@ag0.ID_2797582-RL_Springboot-LOC_search~UND~helpdoc~UND~item-OR_ser-V_4-P0_27&source=5176.29345612&userCode=ywqc0ubl)
    - [SpringFramework没有解决了什么问题？](https://help.aliyun.com/zh/yunxiao/user-guide/quickly-create-and-deploy-spring-boot-experience-applications?scm=20140722.S_help@@%E6%96%87%E6%A1%A3@@2797582.S_RQW@ag0+BB2@ag0+BB1@ag0.ID_2797582-RL_Springboot-LOC_search~UND~helpdoc~UND~item-OR_ser-V_4-P0_27&source=5176.29345612&userCode=ywqc0ubl)
  - SringBoot的概述
    - [SpringBoot解决上述Spring的缺点](https://help.aliyun.com/zh/yunxiao/user-guide/quickly-create-and-deploy-spring-boot-experience-applications?scm=20140722.S_help@@%E6%96%87%E6%A1%A3@@2797582.S_RQW@ag0+BB2@ag0+BB1@ag0.ID_2797582-RL_Springboot-LOC_search~UND~helpdoc~UND~item-OR_ser-V_4-P0_27&source=5176.29345612&userCode=ywqc0ubl)
    - [SpringBoot的特点](https://help.aliyun.com/zh/yunxiao/user-guide/quickly-create-and-deploy-spring-boot-experience-applications?scm=20140722.S_help@@%E6%96%87%E6%A1%A3@@2797582.S_RQW@ag0+BB2@ag0+BB1@ag0.ID_2797582-RL_Springboot-LOC_search~UND~helpdoc~UND~item-OR_ser-V_4-P0_27&source=5176.29345612&userCode=ywqc0ubl)
    - [SpringBoot的核心功能](https://help.aliyun.com/zh/yunxiao/user-guide/quickly-create-and-deploy-spring-boot-experience-applications?scm=20140722.S_help@@%E6%96%87%E6%A1%A3@@2797582.S_RQW@ag0+BB2@ag0+BB1@ag0.ID_2797582-RL_Springboot-LOC_search~UND~helpdoc~UND~item-OR_ser-V_4-P0_27&source=5176.29345612&userCode=ywqc0ubl)
  - [参考文章](https://help.aliyun.com/zh/yunxiao/user-guide/quickly-create-and-deploy-spring-boot-experience-applications?scm=20140722.S_help@@%E6%96%87%E6%A1%A3@@2797582.S_RQW@ag0+BB2@ag0+BB1@ag0.ID_2797582-RL_Springboot-LOC_search~UND~helpdoc~UND~item-OR_ser-V_4-P0_27&source=5176.29345612&userCode=ywqc0ubl)

## [#](#springframework解决了什么问题-没有解决什么问题) SpringFramework解决了什么问题，没有解决什么问题？

> 需要概括性的理解 SpringFramework解决了什么问题，没有解决什么问题？

### [#](#springframework解决了什么问题) SpringFramework解决了什么问题？

Spring是Java企业版（Java Enterprise Edition，JEE，也称J2EE）的轻量级代替品。无需开发重量级的EnterpriseJavaBean（EJB），Spring为企业级Java开发提供了一种相对简单的方法，通过依赖注入和面向切面编程，用简单的Java对象（Plain Old Java Object，POJO）实现了EJB的功能。

1.使用Spring的IOC容器,将对象之间的依赖关系交给Spring,降低组件之间的耦合性,让我们更专注于应用逻辑 2.可以提供众多服务,事务管理,WS等。 3.AOP的很好支持,方便面向切面编程。 4.对主流的框架提供了很好的集成支持,如Hibernate,Struts2,JPA等 5.Spring DI机制降低了业务对象替换的复杂性。 6.Spring属于低侵入,代码污染极低。 7.Spring的高度可开放性,并不强制依赖于Spring,开发者可以自由选择Spring部分或全部

### [#](#springframework没有解决了什么问题) SpringFramework没有解决了什么问题？

虽然Spring的组件代码是轻量级的，但它的配置却是重量级的。一开始，Spring用XML配置，而且是很多XML配置。Spring 2.5引入了基于注解的组件扫描，这消除了大量针对应用程序自身组件的显式XML配置。Spring 3.0引入了基于Java的配置，这是一种类型安全的可重构配置方式，可以代替XML。

所有这些配置都代表了开发时的损耗。因为在思考Spring特性配置和解决业务问题之间需要进行思维切换，所以编写配置挤占了编写应用程序逻辑的时间。和所有框架一样，Spring实用，但与此同时它要求的回报也不少。

除此之外，项目的依赖管理也是一件耗时耗力的事情。在环境搭建时，需要分析要导入哪些库的坐标，而且还需要分析导入与之有依赖关系的其他库的坐标，一旦选错了依赖的版本，随之而来的不兼容问题就会严重阻碍项目的开发进度。

1.jsp中要写很多代码、控制器过于灵活,缺少一个公用控制器 2.Spring不支持分布式,这也是EJB仍然在用的原因之一。

## [#](#sringboot的概述) SringBoot的概述

### [#](#springboot解决上述spring的缺点) SpringBoot解决上述Spring的缺点

SpringBoot对上述Spring的缺点进行的改善和优化，基于约定优于配置的思想，可以让开发人员不必在配置与逻辑业务之间进行思维的切换，全身心的投入到逻辑业务的代码编写中，从而大大提高了开发的效率，一定程度上缩短了项目周期。

### [#](#springboot的特点) SpringBoot的特点

1. 为基于Spring的开发提供更快的入门体验
2. 开箱即用，没有代码生成，也无需XML配置。同时也可以修改默认值来满足特定的需求
3. 提供了一些大型项目中常见的非功能性特性，如嵌入式服务器、安全、指标，健康检测、外部配置等

SpringBoot不是对Spring功能上的增强，而是提供了一种快速使用Spring的方式

### [#](#springboot的核心功能) SpringBoot的核心功能

- **起步依赖** 起步依赖本质上是一个Maven项目对象模型（Project Object Model，POM），定义了对其他库的传递依赖，这些东西加在一起即支持某项功能。

简单的说，起步依赖就是将具备某种功能的坐标打包到一起，并提供一些默认的功能。

- **自动配置**

Spring Boot的自动配置是一个运行时（更准确地说，是应用程序启动时）的过程，考虑了众多因素，才决定Spring配置应该用哪个，不该用哪个。该过程是Spring自动完成的。



作为一名多年开发经验的老鸟，平时抽空收集了各种优质的技术教程，涉及前后端和移动端。包含各种编程语言，有兴趣的可以抽空学习起来：[全栈工程师必读技术教程](https://nav.vpssw.com/favorites/technical-information)   毕竟在这个竞争激烈的时代，多学一点，多一份技能傍身总是有好处的。

## [#](#参考文章) 参考文章

https://spring.io/projects/spring-boot

https://baike.baidu.com/item/Spring%20Boot/20249767?fr=aladdin

https://www.jianshu.com/p/24add3c5fedb

https://www.cnblogs.com/luzhanshi/p/10592209.html

 [快速创建并部署spring-boot体验应用](https://help.aliyun.com/zh/yunxiao/user-guide/quickly-create-and-deploy-spring-boot-experience-applications?scm=20140722.S_help@@%E6%96%87%E6%A1%A3@@2797582.S_RQW@ag0+BB2@ag0+BB1@ag0.ID_2797582-RL_Springboot-LOC_search~UND~helpdoc~UND~item-OR_ser-V_4-P0_27&source=5176.29345612&userCode=ywqc0ubl)

------

