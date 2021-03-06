---
layout: post
title: 一条很有价值的编程建议
description: 不要使用‘er’结尾的对象命名。（Don’t make objects that end with ‘er’.） 
keywords: code, 代码
category : other
tags : [code, 代码]
---

多年以前（早在1992年），我加入了这个疯狂的skunkworks项目，这个项目使用的是他们叫做Smalltalk的另类程序语言。
当时， “面向对象”作为一个“热门”项目才刚刚起步。作为“面向对象”的顾问，报酬非常可观。
很多人自以为这就是新的对象派别的全部内容。
这发生在[Alan Kay][ak]（Smalltalk语言的发明人之一，也是面向对象编程思想的创始人之一）发表他的图灵奖获奖感言

> “我发明了‘面向对象编程’这个术语，
> 但Java和C++跟我所知道的有所不同”（”I invented the term ‘Object Oriented Programming’ and this {Java and C++} is not what I had in mind.”）——5年前。 

[ak]: http://en.wikipedia.org/wiki/Alan_Kay

在加入skunkworks这个奇特的小组，使用这种奇怪的编程语言的一段时间内，我对实例变量、类变量、类实例变量之间的差别依然感到困惑。
于是我参加了来自ParcPlace的Russ Pencin的培训课程。他说了一些当时我并不能完全体味的东西。
尽管不明白金玉良言当中的要点，但我还是努力去遵守它们。
有些东西需要多年的经验才能渐渐体会其中的价值。Russ的建议是： 

**不要使用‘er’结尾的对象命名。（Don’t make objects that end with ‘er’.） **

就是这样。面向对象的编程范式（OOP）在我们此前的“面向过程编程（procedural programming ）”文化迸发出了一股新鲜活力。
现在我们已经不再过多地去谈论这两种模式之间的对比。
部分原因或许是因为面向对象语言现在已俯拾即是。
面向对象编程思想，在众多编程范式中脱颖而出。
可惜的是，我经常回想起在2000年左右听过的Adele Goldberg的演讲：“**现在我们有很多面向对象编程技术，但却没有那么多面向对象编程的程序员**”。
假如我有一个建议想转告给一群有志成为面向对象程序员的人，那应该是Russ提供的那句箴言：“**不要使用‘er’结尾的对象命名**。” 

那么对象命名中究竟有什么？为什么这句话值得大家对它感兴趣？
多年以后我发现，**面向对象编程的精髓在于将操作绑定在数据上**。
在你还没成为他们无归属组织的重要一员时，程序就还是由操作和数据构成。
在典型的结构化程序设计之中，我们将精力集中在行为（动词）上，然后弄清楚我们需要哪些数据（名词）才能执行。
换句话说，**我们将数据绑定在行为上**。
但在面向对象程序设计中，数据，名词，成为程序的中心，之后我们才去弄清楚要将哪些行为绑定在它们之上，藉此来解决因突发行为产生而可能造成的问题。 

最近我觉得有一个更好的名字来形容一位同事差不多都插手过的每一个“er”对象例子。
给例子起一个更好的名字会让设计更加具有独立性，代码的关联性更少，总之，更加面向对象。
这不是硬性规定，不过这会让很多例子得到改善。 

就拿某种“装载程序模块（Loader）”来说吧，重点在于它的工作单元。
模块有许多实例变量、参数，也许还有很多到处传输的数据。
如今，取而代之的是 LoadRecord 和LoadStream。
我有理由相信，你们最终使用的工具，更类似于面向对象编程创始人心中设想的模样。
**我们需要设计出可以描述的对象，然后将行为绑定在它上面，而不是聚焦在对象做什么，为此它们还需要哪些数据**。 

下面是这些年来我学到的应该避免使用的一些er结尾的对象命名： 

* 管理者（Manager）——每次我看到这样的一个命名时，我便感到厌烦。大家没有跟我说它的含义，却早早地告诉我它的职能。它是注册表吗？那就叫它注册表吧。是历史记录或者日志？就这样称呼好了。工厂？那就命名它。 
* 控制器（Controller）——我在过去20年内只做过一个上等的控制器对象，它是一个象征着现实世界对象的BallastVoltageController接口。事实上，每一个单独的MVC实现都有着不同的控制器角色，它们将告诉我们这个MVC构思是如何运作的。 
* 组织者（Organizer 以及许多类似的团体）——焦点在于他们的职能。这是一个用来说明让众多这种‘ers’对象转化为组织极其简单的不错例子。就把它们称为组织吧。现在我们来关注它们的内容。 
* 分析器/渲染器（Analyzer/Renderer）等等——“Worker”对象的具体例子。直接用analysis/renderering又能怎么样？ 
* 生成器/加载器/阅读器/编写器（Builder/Loader/Reader/Writer）等等——把你的关注从对象将被利用身上挪开，关注具体的职责而不是它们能做什么。 

当然，这条规则也会有很多的例外情况： 

* 许多以‘er’结尾的名词。Register（注册表）、Border（边框）、Character（字母）、Number（数字）。如果真的是一个名词的话，没有问题。 
* 有很多‘er’结尾的单词，尽管重点在于它们的行为上，也变得很常见了，所以我们最好至少在一定程度上维持这种情况，如Parser（分部程序）、Compiler（编译器）、Brower（浏览器）。 
* 建立一个以‘er’结尾的域对象模型。如果Manager是Personal下面的子集那没有问题，Manager是人事的一部分，拥有管理权限。 

你的经历可能会有所不同，我相信有很多人持反对意见。可是只有在试着去体会后，你才能真正明白。在你的项目/设计中试试这条规则，看看会发生什么。 

英文原文：[One of the Best Bits of Programming Advice I ever Got][1]

[1]: http://objology.blogspot.com/2011/09/one-of-best-bits-of-programming-advice.html