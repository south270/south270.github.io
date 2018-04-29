---
layout: post
title: 系统分析与设计第四次作业
date: 2018-4-28 13:27:10+00:00
categories: 系分作业
tags: 博客
---

## 一、领域建模
### a.阅读 Asg_RH 文档，按用例构建领域模型。
- 按 Task2 要求，请使用工具 UMLet，截图格式务必是 png 并控制尺寸
- 说明：请不要受 PCMEF 层次结构影响。你需要识别实体（E）和 中介实体（M，也称状态实体）
  - 在单页面应用（如 vue）中，E 一般与数据库构建有关， M 一般与 store 模式 有关
  - 在 java web 应用中，E 一般与数据库构建有关， M 一般与 session 有关
  
**答：**

<img src="https://github.com/south270/south270.github.io/blob/master/image/h4/%E9%A2%86%E5%9F%9F%E6%A8%A1%E5%9E%8B.png?raw=true">

### b.数据库建模(E-R 模型)
- 按 Task 3 要求，给出系统的 E-R 模型（数据逻辑模型）
- 建模工具 PowerDesigner（简称PD） 或开源工具 OpenSystemArchitect
- 不负责的链接 http://www.cnblogs.com/mcgrady/archive/2013/05/25/3098588.html
- 导出 Mysql 物理数据库的脚本
- 简单叙说 数据库逻辑模型 与 领域模型 的异同

**答：**
- 系统的 E-R 模型（数据逻辑模型）:

<img src="https://github.com/south270/south270.github.io/blob/master/image/h4/%E9%80%BB%E8%BE%91%E6%A8%A1%E5%9E%8B.png?raw=true">


- 导出 Mysql 物理数据库的脚本 :

```sql

/*==============================================================*/
/* Table: Customer                                              */
/*==============================================================*/
create table Customer 
(
   customer_id          int                            not null,
   customer_name        varchar(64)                    null,
   email_address        varchar(64)                    null,
   constraint PK_CUSTOMER primary key clustered (customer_id)
);

/*==============================================================*/
/* Table: Hotel                                                 */
/*==============================================================*/
create table Hotel 
(
   hotel_id             int                            not null,
   hotel_name           varchar(64)                    null,
   hotel_star           int                            null,
   hotel_hot            int                            null,
   hotel_address        varchar(64)                    null,
   location_code        int                            null,
   constraint PK_HOTEL primary key clustered (hotel_id)
);

/*==============================================================*/
/* Table: Location                                              */
/*==============================================================*/
create table Location 
(
   location_code        int                            not null,
   location_name        varchar(64)                    null,
   location_hot         int                            null,
   location_region      varchar(64)                    null,
   location_city        varchar(64)                    null,
   location_town        varchar(64)                    null,
   isCapital            tinyint                        null,
   constraint PK_LOCATION primary key clustered (location_code)
);

/*==============================================================*/
/* Table: Reservation                                           */
/*==============================================================*/
create table Reservation 
(
   reservation_id       int                            not null,
   check_in_date        date                           null,
   check_out_date       date                           null,
   room_id              integer                        null,
   hotel_id             int                            null,
   room_quantity        int                            null,
   at_total_price       decimal                        null,
   state                tinyint                        null,
   customer_id          int                            null,
   constraint PK_RESERVATION primary key clustered (reservation_id)
);

/*==============================================================*/
/* Table: Room                                                  */
/*==============================================================*/
create table Room 
(
   room_id              integer                        not null,
   room_des_id          int                            null,
   is_available         tinyint                        null,
   date_time            date                           null,
   room_des             int                            null,
   hotel_id             int                            null,
   constraint PK_ROOM primary key clustered (room_id)
);

/*==============================================================*/
/* Table: RoomDescription                                       */
/*==============================================================*/
create table RoomDescription 
(
   room_des_id          int                            not null,
   room_list_price      decimal                        null,
   room_type            varchar(64)                    null,
   constraint PK_ROOMDESCRIPTION primary key clustered (room_des_id)
);

alter table Hotel
   add constraint FK_HOTEL_REFERENCE_LOCATION foreign key (location_code)
      references Location (location_code)
      on update restrict
      on delete restrict;

alter table Reservation
   add constraint FK_RESERVAT_REFERENCE_ROOM foreign key (room_id)
      references Room (room_id)
      on update restrict
      on delete restrict;

alter table Reservation
   add constraint FK_RESERVAT_REFERENCE_HOTEL foreign key (hotel_id)
      references Hotel (hotel_id)
      on update restrict
      on delete restrict;

alter table Reservation
   add constraint FK_RESERVAT_REFERENCE_CUSTOMER foreign key (customer_id)
      references Customer (customer_id)
      on update restrict
      on delete restrict;

alter table Room
   add constraint FK_ROOM_REFERENCE_HOTEL foreign key (hotel_id)
      references Hotel (hotel_id)
      on update restrict
      on delete restrict;

alter table Room
   add constraint FK_ROOM_DESCRIBE_ROOMDESC foreign key (room_des_id)
      references RoomDescription (room_des_id)
      on update restrict
      on delete restrict;


```
- 数据库逻辑模型与领域模型的异同 :
  - 领域模型专注于功能业务流程，数据库专注于数据库表.
  
  - 数据库逻辑模型借助相对抽象、逻辑统一且结构稳健的结构，实现数据仓库系统所要求的数据存储目标，支持大量的分析应用，是实现业务智能的重要基础，同时也是数据管理分析的工具和交流的有效手段，我们需要明确哪些类需要在数据库中存储，明确定义类的属性即其主键外键.
  - 领域模型是对领域内的概念类或现实世界中对象的可视化表示。又称概念模型、领域对象模型、分析对象模型。它是对业务角色和业务实体之间应该如何联系和协作以执行业务的一种抽象，我们需要找到概念类并根据用例确定之间的关联.
  

