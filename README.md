# 关卡数据分析

## 简介
在本项目中，我们对3D消除游戏进行了数据分析，但本方法适用于任何多关卡为基础的移动游戏应用。

## 使用说明
建议使用Anaconda的Jupyter Notebook运行

## 埋点和字段需求
每次关卡通过后上报一次，字段包含如下

玩家基本信息
```UserID```唯一用户账号标识
```DeviceID```唯一用户设备标识
```Level```当前关卡ID
```CreateTime```创建时间
```AccCreateTime```账号注册时间
```Region```账号注册地区
```Version```版本号

关卡信息
```IsWin```标记是否成功通过关卡
```WinStreak```当前连胜次数
```LoseReason```失败原因
```Progress```结算时距离目标的进度
```Target```目标消除数量
```LevelStartTime```关卡开始时间
```LevelTime```关卡持续时间

道具信息
```BuyBolts```购买了多少次闪电道具
```BuyTimer```购买了多少次时钟道具
```Usebroom```购买了多少次扫把道具

## 参考资料
Yasin Hatiboğlu  https://www.linkedin.com/in/tyhat/ Match3 Level Analysis Workshop
Game Analytics Retention and Monetization in Free-to-Play Mobile Games - Russell Ovans
