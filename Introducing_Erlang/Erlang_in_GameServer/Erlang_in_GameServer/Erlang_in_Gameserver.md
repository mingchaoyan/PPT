title: Erlang in Gameserver
speaker: mingchaoyan
url: https://github.com/ksky521/nodePPT
transition: cards
files: /js/demo.js,/css/demo.css

[slide]

# Erlang in Gameserver
## 分享者：mingchaoyan

[slide]
[magic data-transition="earthquake"]

# Who am I ? 
-----
* **Erlang**，PHP／《明朝这些年》 {:&.moveIn}
* **Erlang**／C++，Lua，Cocos2d／《全萌猎人》
* **Erlang**／C#，Lua，Unity，uLua／《勇者联盟》
* JavaScript（CoffeeScript），Node.js／《谁是卧底OL》
* Ruby，RoR／《聚会玩平台管理系统》
* C#，Unity／C，Lua，Skynet／《消消果缤纷》
* [知乎](https://www.zhihu.com/people/mingchaoyan)／[乐乎](http://mingchaoyan.lofter.com/)／[微博](http://weibo.com/mingchaoyan)／[豆瓣](https://www.douban.com/people/mingchaoyan/) mingchaoyan
[/magic]

[slide]

# 大纲 
-----
* 语言层面 {:&.moveIn}
* OTP——Erlang 中一个极其重要的概念
* Erlang 游戏服务器开发的周边工具
* Q／A

[slide]

# 大纲 
-----
* **语言层面** {:&.moveIn}

[slide]

# hello, world (erlang shell)

```shell
mingchaoyan at mingchaoyan_mac in ~
$ erl
Erlang/OTP 19 [erts-8.1] [source] [64-bit] [smp:4:4] [async-threads:10] [hipe] [kernel-poll:false] [dtrace]

Eshell V8.1  (abort with ^G)
1> io:format("hello, world\n").
hello, world
ok
2> q().
ok
3> %
mingchaoyan at mingchaoyan_mac in ~
$
```

[slide] 

# hello, world (script)
* 编辑 {:&.moveIn}
```erlang 
#! /usr/bin/env escript
main(_) ->
    io:format("hello, world\n").
```
* 解释运行
```shell
$ chmod +x hello.erl
$ ./hello.erl
hello, world
```
[slide]

# hello, world (compile)
* 编辑 {:&.moveIn}
```erlang 
-module(hello).
-export([hello_world/0]).
hello_world() ->
    io:fwrite("hello, world\n").
```

* 编译产生beam文件
```shell
$ erlc hello.erl 
```
* 运行erl 载入beam文件
```shell
$ erl
> hello:hello_world().
> hello, world
```

[slide]


# 历史 
---

* 发行：1987 {:&.moveIn}
* 作者：乔·阿姆斯特朗（瑞典)，麦可·威廉（瑞典）， 罗伯·维丁（瑞典）
* 设计初衷：电信设备制造商爱立信私有软件，创造一个种可以应付大规模开发活动的程序设计语言和运行环境

[slide]

# 作者

* ![作者](/Erlang-1987.jpg)

[slide]

# 编程范型 & 语言特性
---
* 函数式 {:&.moveIn}
* 并发
* 消息通信
* 容错/热更新

[slide]

# 数据类型（动态强类型）
----

## 基本类型
* 原子(Atom): foo, bar, true, false {:&.moveIn}
* 整数(Integer):42
* 浮点数(Float):3.14
* 二进制(Bit/Binary): <<10, 20>>

[slide]

## 基本类型（续）
* 函数（Func） {:&.moveIn}
* A fun is a functional object.
``` shell
1> Fun1 = fun (X) -> X+1 end.
#Fun<erl_eval.6.39074546>
2> Fun1(2).
3
```
* 一等公民（first class）

[slide]

## 基本类型(续)

* 进程ID（Pid） {:&.moveIn}
* A process identifier, pid, identifies a process.
```
1> spawn(m, f, []).
<0.51.0>
```
* Erlang VM级别的进程，并非OS级别进程
* Actor并发模型的基础，Skynet受其启发

[slide]
## 基本类型（续）
* 端口（Port） {:&.moveIn}
* A port identifier identifies an Erlang port.
* ![](/port.gif)


[slide]
## 基本类型（续）
* 引用（Ref） {:&.moveIn}
* A reference is a term that is unique in an Erlang runtime system
```shell
> make_ref().
#Ref<0.0.4.99>
```

[slide]

## 复合类型
* List／String {:&.moveIn}
* A list is a compound data type with a variable number of terms.
```
1> L1 = [a,2,{c,4}].
[a,2,{c,4}]
2> [H|T] = L1.
[a,2,{c,4}]
3> H.
a
4> T.
[2,{c,4}]
5> L2 = [d|T].
[d,2,{c,4}]
6> length(L1).
3
7> length([]).
0
```

[slide]

## 复合类型（续）
* 元组（Tuple） {:&.moveIn}
* A tuple is a compound data type with a fixed number of terms:
```
1> P = {adam,24,{july,29}}.
{adam,24,{july,29}}
2> element(1,P).
adam
3> element(3,P).
{july,29}
4> P2 = setelement(2,P,25).
{adam,25,{july,29}}
5> tuple_size(P).
3
6> tuple_size({}).
0
```

[slide]

## 复合类型（续）
* 记录（Record） {:&.moveIn}
* A record is a data structure for storing a fixed number of elements.
* Rocord 是 Tuple 的一种语法糖
* ![record](/record.jpeg)
```
1> person:new(ernie, 44).
{person,ernie,44}
```

[slide]

## 复合类型（续）
* 映射（Maps） {:&.moveIn}
* Maps are considered to be experimental during Erlang/OTP R17
```
1> M1 = #{name=>adam,age=>24,date=>{july,29}}.
#{age => 24,date => {july,29},name => adam}
2> maps:get(name,M1).
adam
3> maps:get(date,M1).
{july,29}
4> M2 = maps:update(age,25,M1).
#{age => 25,date => {july,29},name => adam}
5> map_size(M).
3
6> map_size(#{}).
0
```

[slide]

# 单一赋值 
* Single Assignment {:&.moveIn}
```erlang  
1> X = 1.
1
2> X = 2.
** exception error: no match of right hand side value 2
```
* 没有竞态，没有锁！
* debug 方便

[slide]
# 模式匹配

```erlang
1> X.
** 1: variable 'X' is unbound **
2> X = 2.
2
3> X + 1.
3
4> {X, Y} = {1, 2}.
** exception error: no match of right hand side value {1,2}
5> {X, Y} = {2, 3}.
{2,3}
6> Y.
3
```
[slide]

# 尾递归

* 普通递归 {:&.moveIn}
```
duplicate(0, _) -> [];
duplicate(N, T)  when N > 0 -> [T | duplicate(N-1, T)].
```
* 尾递归
```
duplicate(0, _, L) -> L;
duplicate(N, X, L) -> duplicate(N-1, X, [X|L]).
```
* No Stack Overflow

[slide]

# 热更新
-----
* Erlang 设计初衷 {:&.moveIn}
* old vs current

[slide]

# 大纲 
-----
* 语言层面 {:&.moveIn}
* **OTP——Erlang 中一个极其重要的概念** 

[slide]

# OTP
-----
* Open Telecom Platform: A branding attempt before Ericsson released Erlang/OTP as open source
* OTP is a collection of useful middleware, libraries, and tools written in Erlang programming language

[slide]

# OTP 设计原则
-----
* 监控树，worker, supervisor {:&.moveIn}
* ![tree](/supervisor-tree.gif)

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
* gen_fsm
* gen_statem
* gen_event
* supervisor

[slide]

# OTP 设计原则（续）
------
* Application
    * Kernel - Functionnality necessary to run Erlang
    * STDLIB - Erlang standard libraries
* Release
    * A release is a complete system made out from a subset of Erlang/OTP applications and a set of user-specific applications

[slide]
# OTP 设计原则（续）
* 防御式编程？ {:&.moveIn}
* >让它崩溃

[slide]

# 大纲 
------
* 语言层面 {:&.moveIn}
* OTP——Erlang 中一个极其重要的概念
* **Erlang 游戏服务器开发的周边工具** 

[slide]
# Erlang 应用于游戏开发的历史
* 始于广州页游
* 现在 广州游戏圈（4399，Forgame等）
* 巨人，莉莉丝等

[slide]

# 核心组件(引擎) 
---
* 网络 {:&.moveIn}
    * rabbitmq
* 缓存 
    * 基于ETS的Cache/Buffer系统
    * Redis
* 数据库 
    * MySQL, 以emysql做驱动
    * Mongo
* 日志 
    * lager

[slide]

# 支持组件
---
* 构建 {:&.moveIn}
    * rebar3 规范了Erlang开发
* 监控 
    * etop
    * observer:start
* 测试 
    * eunit

[slide]

# 没讲到的话题
------
* 控制结构 {:&.moveIn}
* 错误处理
* 分布式
* ETS
* 并发原语／消息通信
* ...

[slide]

# 推荐
----
![](/ProgrammingErlang2.jpg)
![](/ErlangOTP.jpg)
![](/LYSEfGG.jpg)
![](/ErlangProgramming.jpg)

* 余锋（淘宝褚霸）
* 成立涛 
* 坚强2002

[slide]

# 大纲（小结）
-----
* 语言层面 {:&.moveIn}
* OTP——Erlang 中一个极其重要的概念
* Erlang 游戏服务器开发的周边工具
* **Q／A** 

[slide]

# Q／A

[slide]

# 谢谢!

