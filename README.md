# 前端 DDD 实现

使用领域驱动模型的思想来实现一个简易的商城

## 场景

该项目分为商品主页、个人中心页、积分中心页、抽奖活动页面，分别交给 a、b、c、d 四位开发人员来完成，四位开发人员的代码风格不同，能力不同。

## 原型图

![](https://user-gold-cdn.xitu.io/2019/7/25/16c273cdb8fab0ab?imageView2/0/w/1280/h/960/format/webp/ignore-error/1)
如上原型，传统的方式四个人去开发，会出现的问题：

1. 判断逻辑重复，多个页面存在同一个判断逻辑
2. 接口调用不统一，多块业务页面用到了同一个接口，并且在各自的根目录下都有一份相同的请求代码
3. 忽略业务整体，在一个庞大、多人协作的项目，作为其中一员很可能出现对整个系统理解不够，只知道自己负责的那几个页面，逐步恶化成“面向页面编程”

后期如果加需求，或者人员变动，所有人都按自己的习惯去写 code，久而久之，会变成一个难以维护的项目

优化思路：将每一块业务划分成不同的领域，各领域下包含哪些服务，每个页面调用的并不是 API 接口，而是各自领域的服务。

## 领域驱动设计

首先提出领域的角色是需求方，每一个需求都必将会映射到某个领域，比如“搜索商品”这个动作对应着商品中心域，“用户登录”对应着用户信息&鉴权域。从产品-后端-前端对其领域的划分认知都是一致的，这是各角色对其整个项目进行合作的基础，在一起讨论问题时，都知道对方讲述的信息是处在哪个域上。

在对领域具有统一认知的情况下，需求方也会更谨慎、清晰地提出新的需求或是更改业务逻辑，各方人员对其业务的熟悉后，也能从自己负责的职能角度上表达出自己对新业务新迭代的看法或建议，而不是“机械”地根据需求文档完成自己的职责。

假设各方角色对整体业务领域不熟悉，大家对其业务的认知不统一，项目很快就会成为一个松散的结构，需求方、开发方、设计方的产出模型无法大致匹配，最后成为开发/维护代价极高的“危楼”项目。

领域驱动设计不是万能的，它只是解决了软件开发中的部分问题，也不是可适用于任何场景的，但是其核心思想是可以借鉴到软件设计与开发过程中的。