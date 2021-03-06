---
title: 《UML精粹》读书笔记
date: 2018-09-14 
tags:
---

# 引言

## UML使用方式

> UML在软件开发中作用的实质是人们不同的使用方式。

作者在引言第一节就抛出了本书关键的一个问题：你想使用好UML吗？先问问自己你为什么要用UML，你期望用UML做什么？

UML三种使用方法：
1. 草图 UML as sketch
2. 蓝图 UML as blueprint
3. 编程语言 UML as programing language

草图的实质是选择，用于确定一个方案值不值得去做，而不关心具体怎么做。蓝图的实质是描述，并且尽可能精确细节的描述。草图是探究性的，蓝图是定义性的。

用作编程语言指的是将UML直接编译为可执行的程序代码，这自然要求比蓝图更精确的描述能力。

另一个看待UML的角度是：用UML对什么建模？
1. 软件视角：对软件建模，UML成分直接映射为软件成分
2. 概念视角：对概念建模，UML成分只是对概念的表述，至于软件怎么实现，另当别论

UML到底用作什么，UML和设计的关系为何？引起很多争议。作者随后表明自己立场，也是我赞同的立场：
**UML用作草图，可用于软件视角和概念视角。不赞同用于蓝图和编程语言。**

> 图示法的魅力在于直观，而不是形式定义。

## 什么才是合法的UML

UML具有指定性规则还是描述性规则？换句话说，UML标准是按照某个机构某个文档说的算，还是使用者说的算？这个问题乍一看有点傻，其实是因为UML标准繁杂不统一导致的。

> 如果你是一名草图绘制人员或一名蓝图绘制人员，不必更多强调有合法的UML，更为重要的是，要对你的系统有一个好的设计。

**把精力更多的用在如何设计一个好的系统，而非拘泥于标准。**

**如果有非UML图更适合，feel free to use it.**

## 何处着手使用UML

**从类图和顺序图着手了解UML，再根据需要去了解更高级的UML**

> 没有人能了解UML的全部，你应该寻求为你和你的同事们的工作的UML子集。

## 更多资料

UML模式及其应用，larman，Applying UML and Patterns
Rumbaugh，UML Reference
重构，Martin Fowler
设计模式

# 过程

作者推崇的过程：

迭代风格、阶段提交、时间框定、回归测试、重构、连续集成、响应变更、迭代回顾

	敏捷过程
		极限编程（XP）
		Scrum
		Crystal
		DSDM
	Rational统一过程（RUP）


# 类图
# 顺序图
# 对象图
# 包图
# 部署图
# 用例图
# 状态机图
# 活动图
# 通信图
# 构件图
# 协作图
