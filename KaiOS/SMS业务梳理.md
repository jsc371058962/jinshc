# SMS业务梳理

# 1.Code结构

1. js文件夹(主要的业务逻辑处理代码)
2. style文件夹(主要的SMS所使用的css文件)
3. index.html文件(SMS目前为止唯一的渲染与展示的页面，即SMS所有呈现给用户的展示均由此html文件提供)
4. manifest.webapp文件
   1. 对应用的描述和说明
   2. 需要请求的权限
   3. 处理其他应用调用其资源的activity请求
   4. etc.

5. others(提供国际化，音频与认证的信息)

# 2.SMS项目流程

![](./source/SMS业务流程图.svg)

# 3.SMS业务组织结构

![](./source/SMS组织结构图.svg)

# 4.分层简介

## 4.1 index.html

​    SMS唯一的入口index.html页面，承载SMS中new,options等相关的所有页面的呈现，是页面的主入口，可以

理解为SMS唯一的展示页面，

## 4.2 js folder(只有部分)

​    JavaScript代码均采用自执行函数编写，用`"use strict"`严格模式编写，消除代码的不合理不严谨之处，保证代码运行安全，增加运行速度，为新版本JavaScript做好铺垫

**设置选项**：

入口在settings.js文件，

