title: Erlang in Gameserver
subtitle: xxx
speaker: mingchaoyan
url: https://github.com/ksky521/nodePPT
transition: cards
files: /js/demo.js,/css/demo.css

[slide]

# Erlang in Gameserver
## 演讲者：mingchaoyan

[slide]

# 大纲 {:&.flexbox.vleft}
## 1. 语言
## 2. OTP
## 3. 一个久经考验的服务器引擎
## 4. Q/A

[slide]

# 大纲 {:&.flexbox.vleft}
## **1. 语言**
## 2. OTP
## 3. 一个久经考验的服务器引擎
## 4. Q/A

[slide]

# 进程 {:&.flexbox.vleft}
* 
```erlang
1> X = 1.
1
2> X = 2.
** exception error: no match of right hand side value 2
```
* Erlang VM级别的进程，并非OS级别进程
* Actor并发模型的基础

[slide]

# 单一赋值 {:&.flexbox.vleft}
```erlang
1> X = 1.
1
2> X = 2.
** exception error: no match of right hand side value 2
```
## 好处
* debug 方便

[slide]
## 使用.class/#id/自定义属性样式
----

```javascript
alert('nodeppt');
```

[slide]

# 大纲 {:&.flexbox.vleft}
## 1. 语言
## **2. OTP**
## 3. 一个久经考验的服务器引擎
## 4. Q/A

[slide]

# 大纲 {:&.flexbox.vleft}
## 1. 语言
## 2. OTP
## **3. 一个久经考验的服务器引擎**
## 4. Q/A

[slide]

# 核心组件(引擎) {:&.flexbox.vleft}
## 1. 网络 rabbitmq
## 2. 缓存 基于ETS的Cache/Buffer系统
## 3. 数据库 MySQL, 以emysql做驱动
## 4. 日志 lager
# 支持组件
## 5. 构建 rebar
## 6. 监控 etop
## 7. 测试 eunit

[slide]

# 大纲 {:&.flexbox.vleft}
## 1. 语言
## 2. OTP
## 3. 一个久经考验的服务器引擎
## **4. Q/A**

[slide]

# 谢谢!

