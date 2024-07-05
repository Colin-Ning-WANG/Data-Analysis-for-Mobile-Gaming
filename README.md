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
```Duration```关卡持续时间  
```LevelStreak```当前挑战此关卡第几次  

道具信息  
```BuyBolts```购买了多少次闪电道具  
```BuyTimer```购买了多少次时钟道具  
```Usebroom```购买了多少次扫把道具  

## 核心分析项目

### 关卡平均通过次数
通过筛选```['IsWin'] == 1```并且按照Level进行分组，计算分组后Level的平均```LevelStreak```次数（此处需要明确一个玩家只有一条成功通过关卡的记录，否则需要先按照唯一ID分组），并绘制柱状图，在样本量足够的情况下可以大致看出不同关卡整体上的难度状态

### 关卡平均通过时间
通过筛选```['IsWin'] == 1```并且按照Level进行分组，计算分组后Level的平均Duration时间。可以用来评估玩家在线行为，以及关卡难度和乐趣。

### 分析平均每个关卡的点击次数
通过筛选```['IsWin'] == 1```并且按照Level进行分组，计算分组后Level的平均ClickTime次数。可以用来评估关卡难度和乐趣。

### 分析平均每个关卡失败时候的平均进度
通过筛选```['IsWin'] == 0```并且按照Level进行分组，计算Progress/Target作为进度Ratio字段，分析失败关卡的平均Ratio进度。可以用来分析关卡失败原因，是否是由于难度太高导致玩家过早放弃或者放弃使用道具进行过关。

### 分析Sink-难度 散点图
先按照Level和唯一用户ID UserID进行分组，统计分Level分用户的平均关卡内货币消耗Sink（通过道具使用次数*道具等价货币+复活次数*复活等价货币） 和 关卡难度（每个关卡IsWin=0的人均次数） 的散点图。可以看出关卡分布的趋势，高难度高关卡消耗的关卡，和低难度低关卡消耗的关卡都是符合正常设计预期的（正常预期为简单关卡不需要消耗道具，困难关卡消耗道具通过），但高难度低消耗关卡就可以被判断为差关卡，因为这意味着关卡难度太高的同时，没有激励玩家产生消耗，说明挫折感可能会提前让玩家认为自己不可能通过从而放弃，这个维度可以综合参考 关卡失败进度 数据一起研判。

## 参考资料
Yasin Hatiboğlu  https://www.linkedin.com/in/tyhat/ Match3 Level Analysis Workshop  
Russell Ovans  Game Analytics Retention and Monetization in Free-to-Play Mobile Games
