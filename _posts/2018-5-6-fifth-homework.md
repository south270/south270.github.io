---
layout: post
title: 系统分析与设计第五次作业
date: 2018-5-6 13:27:10+00:00
categories: 系分作业
tags: 博客
---

## 一、使用 UML State Model
- 建模对象： 参考 Asg_RH 文档， 对 Reservation/Order 对象建模。
- 建模要求： 参考练习不能提供足够信息帮助你对订单对象建模，请参考现在 定旅馆 的旅游网站，尽可能分析围绕订单发生的各种情况，直到订单通过销售事件（柜台销售）结束订单。

**答:**
- 状态集合 S = {新订单(未付款)，处理中(已付款)，已处理(待入住)，确认中(待取消)，退款中(待取消)，已入住}
- 常见事件 E = {选择酒店、房型，填写相关信息，创建订单，修改相关信息，支付失败，支付成功，取消订单，放弃支付，取消订单，酒店确认，客户入住}
<img src="https://github.com/south270/south270.github.io/blob/master/image/h5/%E8%AE%A2%E5%8D%95%E7%8A%B6%E6%80%81.png?raw=true">

## 二、研究淘宝退货流程活动图，对退货业务对象状态建模

**答:**
<img src="https://github.com/south270/south270.github.io/blob/master/image/h5/%E6%B7%98%E5%AE%9D%E9%80%80%E6%AC%BE.png?raw=true">
