# 内购接入指南

::: tip 阅读本文大概需要30分钟

本文将帮助您快速了解游戏如何创建商品、接入内购、查看内购数据并调优。

::: 

什么是内购？

应用内付费简称IAP(In-App Purchase)，是一种简单、透明、公平、安全的商业化手段。使用口袋方舟编辑创作，创作者可通过以下指引接入内购，并根据数据情况优化商业化内容，丰富创作收入来源。

::: danger 派对币

派对币是游戏内的通用货币，100派对币≈1元人民币

:::

## 内购接入

### 创建商品

可在【创作者中心】-【我的游戏】-【游戏服务】-【[商品管理]([https://portal.ark.online/#/admin/good-management](https://portal.ark.online/#/admin/game-good-management))】创建商品。

- 该价格为代币价格，目前100代币≈1元，可根据游戏内定价填写合适价格
- 游戏内的每个商品都应该在游戏维度下的商品管理内创建单独的商品以方便后续管理。



### 游戏代码编写

1. **代币的数量刷新**

- 需要在客户端注册代币刷新监听接口

```JavaScript
const onArkUpdate = (amount: number) => {
    //刷新逻辑，amount为当前代币数量
}
mw.PurchaseService.onArkBalanceUpdated.add(onArkUpdate);
```

- 需要在商店打开时，在客户端调用代币刷新方法

```JavaScript
 mw.PurchaseService.getArkBalance(); // 触发代币余额刷新。接收更新的值要用mw.PurchaseService.onArkBalanceUpdated
```

2. **购买代币商品**

- 需要在客户端调用购买方法，并在回调中刷新代币数量，其中CommodityId为平台配置的商品ID

```JavaScript
const commodityId = "testId";
const count = 1;
mw.PurchaseService.placeOrder(commodityId, count, (status, msg) => {
    mw.PurchaseService.getArkBalance();//刷新代币数量
});
```

- 需要在服务端注册购买成功回调

```JavaScript
const onShipOrder = (playerId: number, orderId: string, commodityId: string, amount: number, confirmOrder: (bReceived: boolean) => void) => {
    //根据playerId和commodityId来处理购买逻辑
    confirmOrder(true);//调用这个方法表示确认收货成功
}
mw.PurchaseService.onOrderDelivered.add(onShipOrder);
```

整个购买流程是客户端调用购买方法，服务端会返回购买结果，根据购买结果来给对应的player添加道具，同时刷新当前剩余代币。

### 游戏测试上线

游戏上线前您可通过游戏测试二维码进行测试。

> 确保游戏内玩家拉起支付-支付成功-发货成功链路没问题后可提交审核，提交审核请勾选【营收方式】-【有变现】-【内购】。

![img](https://arkimg.ark.online/(null)-20240617192249400.png)

## 平台商城

平台商城即将于040版本对外发布。

## 内购数据

### 商品订单

您可在游戏主页下游戏服务-[充值订单](https://portal.ark.online/#/admin/game-order-list)查看单个游戏的订单数据；
也可通过访问财务与管理-[充值订单](https://portal.ark.online/#/admin/order-list)访问您账号下所有游戏的订单数据。

![img](https://arkimg.ark.online/(null)-20240617192249434.png)

您可在订单数据内查看每一笔订单的情况，包含购买用户、购买商品及分成后数据。

### 内购数据

内购数据看板通过多个维度和细致的数据分析，帮助开发者深入了解用户购买行为，从而优化游戏内购策略。以下是各板块功能的详细介绍：

![img](https://arkimg.ark.online/(null)-20240624143456626.png)

#### 数据概览

此板块提供游戏内购的总体数据，包括成交代币数、订单数、ARPU等关键指标。

> 该板块右上角是数据的时间。每个数据下都有日环比（对比前一天）和周同比（对比上周同一天）的增长率，每个数据右侧是对比前一天的绝对值变化，红色代表增长，绿色代表下跌。

![img](https://arkimg.ark.online/(null)-20240624141928065.png)

1. ARPU=成交代币数/日活: 日活也叫进入游戏人数
2. ARPPU=成交代币数/内购人数
3. 支付转化率（PV）=支付成功（PV）/进入游戏（PV）

#### 趋势分析

趋势分析板块展示了游戏内购关键数据的动态变化，包括订单数、购买人数、成交代币数趋势等。

![img](https://arkimg.ark.online/(null)-20240624141928035.png)

#### 转化漏斗

转化漏斗板块详细分析了用户进入游戏到成功购买的转化情况，您可仔细分析每一步的转化率，找出可能的流失点，并针对流失点，调整商品展示、定价策略手段，以提高转化率。

> 转化漏斗分UV转化和PV转化，支付转化分析常用UV转化，用于看用户整体充值意愿；整个链路转化分析常用PV转化，用于看用户行为链路的转化特点。

![img](https://arkimg.ark.online/(null)-20240624141928219.png)

#### 商品分析

此板块提供了top10商品的详细数据，包括商品的成交代币数、成交人数、首购人数、复购人数等。通过这些数据，您可以了解哪些商品最受欢迎，哪些商品需要改进。

> 看板排序字段支持手动选择，排序可选择从低到高、从高到低，可排序字段包括：成交代币数、成交人数、成交订单数、ARPU。

![img](https://arkimg.ark.online/(null)-20240624141928367.png)

1. 游戏首购人数：购买该商品且为首次在这个游戏成功产生支付行为的用户数
2. 游戏复购人数：购买该商品且非首次在这个游戏成功产生支付行为的用户数
3. 商品首购人数：首次成功购买该商品的用户数
4. 商品复购人数：非首次成功购买该商品的用户数
5. 商品复购次数：非首次成功购买该商品的次数
6. 用户复购率（UV）=商品复购人数/成交人数
7. 用户复购率（PV）=商品复购次数/成交订单数

#### 消费力分布

用户消费力分布板块展示的是用户每天消费的代币数量，展示了不同消费水平的用户比例，这些数据有助于您更精准地定位目标用户群，制定个性化的营销策略。

> 您可根据消费力分布调整商品定价，以吸引更多用户或者用户分布往更高价值偏移。

> 比如大部分消费分布集中在1~200代币，可考虑制定累计充值活动提高用户消费金额等。

![img](https://arkimg.ark.online/(null)-20240624143456519.png)
