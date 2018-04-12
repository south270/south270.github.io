---
layout: post
title: 初识SpringBoot
date: 2018-4-12 13:27:10+00:00
categories: 学习报告
tags: 博客
---
## 一、简介

**Spring Boot**是有Pivotal团队提供的全新框架，其设计目的是用来简化Spring应用的初始搭建以及开发过程。该框架使用了特定的方式来进行配置，从而使开发人员不再需要定义样板化的配置，我们也可以称它为SpringMVC框架的精简版。它最大的优点就是摆脱了Spring框架中各种复杂的配置，同时继承了大量常用的第三方库配置，开发人员在使用的时候只需要少量的配置代码，可以进行快速、敏捷地开发。
* 独立运行的Spring 项目，可以以jar包的形式独立运行
* 内嵌Servlet 容器
* 提供starter简化Maven 配置
* 自动配置Spring
* 准生产的应用监控
* 无代码生成和xml配置

## 二、入门实例

### 1.配置
* jdk

![](https://github.com/south270/south270.github.io/blob/master/image/report1/1.png?raw=true)
* maven: 一个项目管理工具。

> 它包含了一个项目对象模型 (POM：Project Object Model)，一组标准集合，一个项目生命周期(Project Lifecycle)，一个依赖管理系统(Dependency Management System)，和用来运行定义在生命周期阶段(phase)中插件(plugin)目标(goal)的逻辑。

![](https://github.com/south270/south270.github.io/blob/master/image/report1/2.png?raw=true)
* IDEA: 按照安装步骤就行安装成功后，配置好jdk

### 2.Hello World

* File->New->Project->Spring Initializr

![](https://github.com/south270/south270.github.io/blob/master/image/report1/3.png?raw=true)
* 填写项目信息

![](https://github.com/south270/south270.github.io/blob/master/image/report1/4.png?raw=true)
* 选择项目使用技术

![](https://github.com/south270/south270.github.io/blob/master/image/report1/5.png?raw=true)
* 填写项目名称

![](https://github.com/south270/south270.github.io/blob/master/image/report1/6.png?raw=true)
* 项目结构

![](https://github.com/south270/south270.github.io/blob/master/image/report1/7.png?raw=true)
* 添加控制器，直接修改项目启动类HelloworldApplication即可

![](https://github.com/south270/south270.github.io/blob/master/image/report1/8.png?raw=true)

@SpringBootApplication是Spring Boot 项目的核心注解，主要目的是开启自动配置。main方法是一个标准的Java应用的main方法，主要作用是作为项目启动的入口。


这样我们就简单的创建了一个基于SpringBoot的java web项目。

