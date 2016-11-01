title: Erlang in Gameserver
speaker: mingchaoyan
url: https://github.com/ksky521/nodePPT
transition: cards
files: /js/demo.js,/css/demo.css

[slide]

# Erlang in Gameserver
## 分享者：mingchaoyan

[slide]

# 大纲 
-----
* OTP
    * OTP 概念
    * OTP 设计原则
* Erlang 遇到游戏开发
    * 国内 Erlang 游戏开发历史
    * 核心组件
    * 支持组件

[slide]

# OTP 概念
-----
* Open Telecom Platform: A branding attempt before Ericsson released Erlang/OTP as open source
* ![hullo](/hullo.png) —— from 《Learn You Some Erlang》

[slide]

# OTP 概念（续）
* OTP is a collection of useful middleware, libraries, and tools written in Erlang programming language


[slide]

# OTP 设计原则
-----
* 监控树，worker, supervisor {:&.moveIn}
* ![tree](/sup-tree.png) —— from 《Learn You Some Erlang》

[slide]

# OTP 设计原则（续）
------
* 行为（Behaviours） {:&.moveIn}
* Behaviours are formalizations of these common patterns.
* 让最优秀的程序员写最抽象的部分

[slide]

# OTP 设计原则（续）
----
* gen_server {:&.moveIn}
* gen_statem（gen_fsm）
* gen_event
* supervisor

[slide]

# OTP 设计原则（续）
------
* Application
    * Kernel - Functionnality necessary to run Erlang
    * STDLIB - Erlang standard libraries
[slide]
# OTP 设计原则（续）
------
* Release
    * A release is a complete system made out from a subset of Erlang/OTP applications and a set of user-specific applications
[slide]
# OTP 设计原则（续）
------
* ![reltool-levels](/reltool-levels.png)

[slide]
# OTP 设计原则（续）
-----
* 错误处理 {:&.moveIn} 
* Let some other process do the error recovery. 
* If you can’t do what you want to do, die.
* Let it crash.
* Do not program defensively.

[slide]

# OTP 设计原则（续）
----
```erlang 
f(load) -> 1;
f(store) -> 2.
```

```erlang
f(load) -> 1;
f(stroe) -> 2;
f(X) -> ????
```

* 防御式代码破坏了代码的纯洁性 {:&.moveIn}
* 防御式代码的诊断信息未必比编译器自动提供的诊断信息好

[slide]

# Erlang 应用于游戏开发的历史
----
* 始于广州页游
* 现在 广州游戏圈（4399，Forgame等）
* 巨人，莉莉丝等

[slide]

# 核心组件
---
* 网络 {:&.moveIn}
    * rabbitmq
* 缓存 
    * 基于ETS的Cache/Buffer系统
    * Redis
* 数据库 
    * MySQL, 以emysql做驱动
    * Mongo

[slide]

# 核心组件（续）
------
* 日志 {:&.moveIn}
    * lager
* Web
    * Cowboy (star 3534)
    * MochiWeb (star 1418)

[slide]

# 支持组件
---
* 第三方包源 {:&.moveIn}
    * GitHub
    * Hex
* 构建 {:&.moveIn}
    * rebar3 (star 507)／rebar (star 897) 规范了Erlang开发
    * erlang.mk (star 403)
[slide]
# 支持组件（续）
-----
* 监控 {:&.moveIn}
    * etop／entop
    * observer:start
* 测试 
    * eunit
    * common test
    * Meck

[slide]


# 大纲（小结）
-----
* Introducing Erlang {:&.moveIn}
    * 语言层面 
* Erlang in GameServer
    * OTP
    * Erlang 遇到游戏开发

[slide]

# Q／A

[slide]

# 谢谢!

