---
layout: post
title:  Arthas(阿尔萨斯)能为你做什么？
author: GEJT
image: assets/images/avatar.jpg
category: Arthas
tags: [Arthas,jvm调优]
dateTime: "2021年4月23日"
excerpt: Arthas是Alibaba开源的Java诊断工具，深受开发者喜爱。Arthas支持JDK 6+，支持Linux/Mac/Windows，采用命令行交互模式，同时提供丰富的Tab自动补全功能，进一步方便进行问题的定位和诊断。
permalink: /arthas/10
typora-root-url: ..\..\
typora-copy-images-to: ..\..\img
---

![_images/arthas.png](/img/arthas.png)

当你遇到以下类似问题而束手无策时，`Arthas`可以帮助你解决：

1. 这个类从哪个 jar 包加载的？为什么会报各种类相关的 Exception？
2. 我改的代码为什么没有执行到？难道是我没 commit？分支搞错了？
3. 遇到问题无法在线上 debug，难道只能通过加日志再重新发布吗？
4. 线上遇到某个用户的数据处理有问题，但线上同样无法 debug，线下无法重现！
5. 是否有一个全局视角来查看系统的运行状况？
6. 有什么办法可以监控到JVM的实时运行状态？
7. 怎么快速定位应用的热点，生成火焰图？

## 快速安装

### 使用`arthas-boot`（推荐）

下载`arthas-boot.jar`，然后用`java -jar`的方式启动：
###  通过跳板机登录到开发环境
kubectl exec -it -n dev svc-user-order-query-xxxxxxx  /bin/bash
#### 下载 arthas-boot
```
curl -O https://arthas.aliyun.com/arthas-boot.jar
java -jar arthas-boot.jar
```
或者
```
wget https://arthas.aliyun.com/arthas-boot.jar 
java -jar arthas-boot.jar
```
#### 启动 arthas-boot

##### 1、默认启动并绑定到java线程

```
java -jar arthas-boot.jar
6
```



##### 2、ps/jps  Java线程号，启动时指定java线程

```
ps -ef |grep java
1 root      0:10 /sbin/tini -- sh -c java -XX:+UseContainerSupport -XX:MaxRAMPercentage=75.0 -Djava.security.egd=file:/dev/./urandom -Djava.net.preferIPv4Stack=true -Dcsp.sentinel.api.port=8719 -Dcsp.sentinel.dashboard.server=${SENTINEL_DASHBOARD_URL} -Dproject.name=${SENTINEL_NAME} -Dapollo.meta=${APOLLO_META} ${JVM_OPTS} -jar /app.jar ${PARAMS} 
6 root     11:52 java -XX:+UseContainerSupport -XX:MaxRAMPercentage=75.0 -Djava.security.egd=file:/dev/./urandom -Djava.net.preferIPv4Stack=true -Dcsp.sentinel.api.port=8719 -Dcsp.sentinel.dashboard.server=sentinel-da-dev.dev.svc.cluster.local:8080 -Dproject.name=user-order-query -Dapollo.meta=http://10.8.202.175:30003 -jar /app.jar

```

```
java -jar arthas-boot.jar 6
[INFO] arthas-boot version: 3.5.0
[INFO] arthas home: /root/.arthas/lib/3.5.0/arthas
[INFO] Try to attach process 6
[INFO] Attach process 6 success.
[INFO] arthas-client connect 127.0.0.1 3658
  ,---.  ,------. ,--------.,--.  ,--.  ,---.   ,---.                           
 /  O  \ |  .--. ''--.  .--'|  '--'  | /  O  \ '   .-'                          
|  .-.  ||  '--'.'   |  |   |  .--.  ||  .-.  |`.  `-.                          
|  | |  ||  |\  \    |  |   |  |  |  ||  | |  |.-'    |                         
`--' `--'`--' '--'   `--'   `--'  `--'`--' `--'`-----'                          
                                                                                

wiki       https://arthas.aliyun.com/doc                                        
tutorials  https://arthas.aliyun.com/doc/arthas-tutorials.html                  
version    3.5.0                                                                
main_class                                                                      
pid        6                                                                    
time       2021-04-21 10:09:51                                                  

[arthas@6]$ 
```

## 常用命令介绍

### dashboard 查看系统运行环境

```
[arthas@6]$ dashboard
```

![image-20210421101245582](/img/image-20210421101245582.png)

Ctrl+c 结束dashboard

### watch 监控Java类方法

```
watch com.xxx.order.UserOrderServiceImpl queryOrderById returnObj
```

```
method=com.xxx.order.UserOrderServiceImpl$$EnhancerBySpringCGLIB$$b6a5a1da.queryOrderById location=AtExit
ts=2021-04-21 10:39:59; [cost=486.283929ms] result=@OrderDTO[
    serialVersionUID=@Long[5159522777304597038],
    orderId=@Long[9943795447],
    orderNo=null,
    unionId=@Integer[0],
    userId=@Integer[21340806],
    userName=null,
    userMobile=@String[13253466668],
    appState=@Integer[6],
    orderState=@Integer[12],
    bizType=@Short[0],
    pbizType=@Integer[0],
    payNo=@String[P36202509943795447],
    payWay=@String[1012],
    createTime=@Date[2018-09-16 19:30:42,000],
    payTime=@Date[2018-09-16 19:38:37,000],
    refundTime=null,
    couponId=@String[66182593],
    totalFee=@BigDecimal[6400.00],
    discountFee=@BigDecimal[250.00],
    expressFee=@BigDecimal[0.00],
    payFee=@BigDecimal[6000.00],
    source=@Integer[20],
    cancelTime=null,
    lastTime=@Date[2018-09-16 19:38:38,000],
    activityId=@Integer[0],
    parentOrder=@Long[0],
    bizId=@Long[0],
    merchantId=@Long[0],
    merchantName=null,
    merchantMobile=@String[],
    deliveryType=@Integer[0],
    refundState=@Integer[0],
    perpayFee=@BigDecimal[0.00],
    deviceToken=@String[00000000-0000-0000-0000-000000000000],
    ip=@String[1.199.72.155],
    tradeRate=@BigDecimal[0.00],
    couponMoney=@String[200.00],
    userDel=@Integer[1],
    merchantDel=@Integer[0],
    refundMerchant=@Long[0],
    goodsId=@Long[0],
    unionOrderId=null,
    redbagMoney=@BigDecimal[50.00],
    redbagIds=@String[97452408],
    reduceMoney=@BigDecimal[0.00],
    balanceMoney=@BigDecimal[0.00],
    expressType=@Integer[0],
    postageType=@Integer[2],
    refundDeductMoney=null,
    snsStatus=@Byte[0],
    tradeMoney=@BigDecimal[0.00],
    completeTime=null,
    goodsIds=@String[,2267829,2519634,2514482,],
    mergeOrderId=@Long[0],
    isMerge=@Integer[1],
    num=@String[1,1,1],
    cashMoney=@BigDecimal[0.00],
    goodsPrices=@String[1000.00,1800.00,3600.00],
    cashAmount=@BigDecimal[6000.00],
    attachGoodsId=@String[0,0,0],
    channel=null,
    commisionId=@Long[0],
    useComiTradeMoney=@BigDecimal[0.00],
    subtractMoney=@Long[0],
    refundableDeposit=null,
    damageFee=null,
    leaseTime=null,
    newPayNo=null,
    newPayWay=null,
    firstPriceMoney=null,
    score=@Long[0],
    dealState=@Integer[0],
    operatorId=null,
    operatorName=null,
    orderType=@Boolean[false],
    asRentFee=@BigDecimal[0.00],
    redBagReturn=@BigDecimal[0.00],
    leasePay=null,
    asRentDeductFee=@BigDecimal[0.00],
    pointScorePrice=@BigDecimal[10.00],
    pointScore=@Integer[1000],
    waitRetPointScore=@Integer[0],
    newUserRebatePrice=@BigDecimal[140.00],
    orderProcessStatus=@Byte[0],
    isAuthorise=null,
    showInfo=null,
    cancelState=@Byte[0],
    orderSafetyId=@Long[667014256774553617],
    fixCommisionId=null,
    memberType=null,
    memberDiscount=null,
    memberPrice=null,
    saleSceneId=null,
    costPrice=null,
    blockedOrderStatus=@Byte[0],
    blockedOrderTime=@Date[2020-10-28 18:28:23,000],
    orderCode=@String[],
]

```

```
[arthas@6]$ watch com.xxx.order.UserOrderServiceImpl queryOrderById "{params,returnObj}" -x 2
Press Q or Ctrl+C to abort.
Affect(class count: 2 , method count: 2) cost in 177 ms, listenerId: 3
method=com.xxx.order.UserOrderServiceImpl.queryOrderById location=AtExit
ts=2021-04-21 10:48:18; [cost=95.077837ms] result=@ArrayList[
    @Object[][
        @Long[9943795447],
    ],
    @OrderDTO[
        serialVersionUID=@Long[5159522777304597038],
        orderId=@Long[9943795447],
        orderNo=null,
        unionId=@Integer[0],
        userId=@Integer[21340806],
        userName=null,
        userMobile=@String[13253466668],
        appState=@Integer[6],
        orderState=@Integer[12],
        bizType=@Short[0],
        pbizType=@Integer[0],
        payNo=@String[P36202509943795447],
        payWay=@String[1012],
        createTime=@Date[2018-09-16 19:30:42,000],
        payTime=@Date[2018-09-16 19:38:37,000],
        refundTime=null,
        couponId=@String[66182593],
        totalFee=@BigDecimal[6400.00],
        discountFee=@BigDecimal[250.00],
        expressFee=@BigDecimal[0.00],
        payFee=@BigDecimal[6000.00],
        source=@Integer[20],
        cancelTime=null,
        lastTime=@Date[2018-09-16 19:38:38,000],
        activityId=@Integer[0],
        parentOrder=@Long[0],
        bizId=@Long[0],
        merchantId=@Long[0],
        merchantName=null,
        merchantMobile=@String[],
        deliveryType=@Integer[0],
        refundState=@Integer[0],
        perpayFee=@BigDecimal[0.00],
        deviceToken=@String[00000000-0000-0000-0000-000000000000],
        ip=@String[1.199.72.155],
        tradeRate=@BigDecimal[0.00],
        couponMoney=@String[200.00],
        userDel=@Integer[1],
        merchantDel=@Integer[0],
        refundMerchant=@Long[0],
        goodsId=@Long[0],
        unionOrderId=null,
        redbagMoney=@BigDecimal[50.00],
        redbagIds=@String[97452408],
        reduceMoney=@BigDecimal[0.00],
        balanceMoney=@BigDecimal[0.00],
        expressType=@Integer[0],
        postageType=@Integer[2],
        refundDeductMoney=null,
        snsStatus=@Byte[0],
        tradeMoney=@BigDecimal[0.00],
        completeTime=null,
        goodsIds=@String[,2267829,2519634,2514482,],
        mergeOrderId=@Long[0],
        isMerge=@Integer[1],
        num=@String[1,1,1],
        cashMoney=@BigDecimal[0.00],
        goodsPrices=@String[1000.00,1800.00,3600.00],
        cashAmount=@BigDecimal[6000.00],
        attachGoodsId=@String[0,0,0],
        channel=null,
        commisionId=@Long[0],
        useComiTradeMoney=@BigDecimal[0.00],
        subtractMoney=@Long[0],
        refundableDeposit=null,
        damageFee=null,
        leaseTime=null,
        newPayNo=null,
        newPayWay=null,
        firstPriceMoney=null,
        score=@Long[0],
        dealState=@Integer[0],
        operatorId=null,
        operatorName=null,
        orderType=@Boolean[false],
        asRentFee=@BigDecimal[0.00],
        redBagReturn=@BigDecimal[0.00],
        leasePay=null,
        asRentDeductFee=@BigDecimal[0.00],
        pointScorePrice=@BigDecimal[10.00],
        pointScore=@Integer[1000],
        waitRetPointScore=@Integer[0],
        newUserRebatePrice=@BigDecimal[140.00],
        orderProcessStatus=@Byte[0],
        isAuthorise=null,
        showInfo=null,
        cancelState=@Byte[0],
        orderSafetyId=@Long[667014256774553617],
        fixCommisionId=null,
        memberType=null,
        memberDiscount=null,
        memberPrice=null,
        saleSceneId=null,
        costPrice=null,
        blockedOrderStatus=@Byte[0],
        blockedOrderTime=@Date[2020-10-28 18:28:23,000],
        orderCode=@String[],
    ],
]
```

## 更多命令请参考官方网站

https://arthas.aliyun.com/doc/