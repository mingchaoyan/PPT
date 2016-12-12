title: Introducing Skynet
speaker: mingchaoyan
url: https://github.com/ksky521/nodePPT
transition: cards
files: /js/demo.js,/css/demo.css

[slide]

# Introducing Skynet
## 分享者：mingchaoyan@gmail.com

[slide]

# Who am I ? 
* Erlang，PHP／《明朝这些年》／SLG／播放回合制  {:&.moveIn}
* Erlang／C++，Lua，Cocos2d／《全萌猎人》／卡牌RPG／即时微操
* Erlang／C#，Lua，Unity，uLua／《勇者联盟》／3D卡牌RPG／技能插入式回合
* JavaScript（CoffeeScript），Node.js／《谁是卧底OL》／休闲
* Ruby，RoR／《聚会玩平台管理系统》／ Web 
* C#，Unity／ ** C，Lua，Skynet **／《消消果缤纷》／三消／弱联网
* ** C, lua, Skynet **／《针锋相对》／飞行类／强联网同步

[slide]

# 大纲 
* 游戏服务器概述 {:&.moveIn}
* Actor 并发模型概述
* Skynet 概述
* 一个Demo
* 推荐
* Q／A

[slide]

# 大纲 
* ** 游戏服务器概述 ** {:&.moveIn}

[slide]

# 游戏服务器概述
* 物理上，表现为一或多台主机 {:&.moveIn}
* 逻辑上，向客户端暴露一组 host:port 二元组，接受客户端连接
* 和客户端联系，客户端与服务端借助 **网络** 传递消息，消息按一定的 **协议** 序列化与反序列化，

[slide]

# 大纲 
* 游戏服务器概述 {:&.moveIn}
* **Actor 并发模型概述**

[slide]

# Actor 并发模型概述

* "The Free Lunch Is Over" - Herb Sutter, 2005 {:&.moveIn}
* 得不到更高的主频
* 获得了更多的核心
* 现成主流语言并没有准备好迎接这次革新
* 2006 年国内 Erlang 开始发声

[slide]

# Actor 并发模型概述（二）
* 一切都是 Actor {:&.moveIn}
* 不共享状态／通过消息
* 并行

[slide]

# 大纲 
* 游戏服务器概述 {:&.moveIn}
* Actor 并发模型概述
* **Skynet 概述**

[slide]

# Skynet 概述
* 2012年 云风 C + Lua {:&.moveIn}
* Actor -> Lua VM

[slide]

# Skynet 概述（二）
![](/ClassicFramework.jpg)
[slide]

# 大纲
* 游戏服务器概述 {:&.moveIn}
* Actor 并发模型概述
* Skynet 概述
* **一个Demo**

[slide]

# 一个Demo
```shell
./skynet example/config
```

[slide]

# 大纲 
* 游戏服务器概述 {:&.moveIn}
* Actor 并发模型概述
* Skynet 概述
* 一个Demo
* **推荐**
* Q／A

[slide]

# 推荐
![](/PiL4E.jpg)
![](/SevenConcurrencyModelsinSevenWeeks.jpg)

[slide]

# 大纲
* 游戏服务器概述 {:&.moveIn}
* Actor 并发模型概述
* Skynet 概述
* 一个Demo
* 推荐
* **Q／A**

[slide]

# Q／A

[slide]

# 谢谢!

