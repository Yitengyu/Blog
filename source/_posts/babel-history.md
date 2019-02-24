---
title: 学习Babel（一） —— 历史篇
catalog: true
date: 2019-02-01 22:51:44
subtitle: Babel的前世今生
header-img: babel_tower.png
tags: babel history
---

## 前言

使用Babel已经一年有余，一直以来对它认识仅仅停留在**“能让我方便地写ES6及ESNext的一个转换器”**。直到最近写了一个babel小插件`babel-plugin-vue-jsx-template`才对它有了一点进一步的认识。

借此契机，进一步去了解Babel，希望转变这种应该避免的`熟悉的陌生人`的状态，将心得撰文如下。
这篇主要介绍Babel的发展历史，了解它一路走来的历程，能够知道它在历史上解决了前端技术发展过程中的什么痛点，并得以展望未来。

## Babel 的前世今生

### 6to5 to Babel

Babel在版本4.0之前叫做“6to5”，由澳大利亚的[Sebastian](https://github.com/kittens)在他的2014年十一月*（那是他的高中时期，你可以估算一下他的年龄了）*提交第一行代码。有趣的是，Sebastian写这个项目的初衷仅仅是将这个作为一个练习的项目，想了解一下JS作为编程语言是怎样运作的，计算机是怎样解析并“理解”代码的。有兴趣的话可以看看[作者2015年的年终总结](https://medium.com/@sebmck/2015-in-review-51ac7035e272)

`6to5`这个名字就更明确了，就是将ES6的代码转换成ES5的代码，当时做类似事情的工具还有`esnext`和来自谷歌的`traceur`。到了15年一月，`6to5`的npm日下载量一度是`traceur`的两三倍，`6to5`与`esnext`合并了。相关见[6to5 + esnext](https://babeljs.io/blog/2015/01/12/6to5-esnext)。

转折点发生在15年二月。当时外界认为`6to5`只是ES6得到广泛支持之前的临时方案，而Sebastian并不赞同，他有更远大清晰的目标。

> 我认为6to5还能做很多事情，它不仅仅不是一个临时的解决方案，而且它将可能影响到将来标准的制定。当人们需要使用下一代JS的特性时，就会想起6to5
>
> I believe that there are things that 6to5 can expand upon to not only become future proof but to potentially influence future standards. 6to5 will always be necessary if you want next generation features.

恰好当时一众来自不同JS工具团队的大佬（Mozilla, Esprima, The jQuery Foundation, Acorn, 6to5, ESLint, and others）一起制定了一个标准——[ESTree](https://github.com/estree/estree)，约定了自ES5之后的JS抽象语法树（AST）.

6to5认为无论从代码压缩（minifiers）到代码美化（beautifiers）, 从代码规范（linters）到代码补全提示（code coverage instrumentors） , 从可编译成js的语言到语法扩展，代码高亮等等，都离不开两件事——解析（parser）和转译（transpiler），于是6to5立下大志希望肩负起转译的责任.

> We want for 6to5 to solve the transpiler story.

但`6to5`这个名字不仅无法承担起这样的愿景，并且已经造成了一些困扰。它当时除了能够将ES6转译到ES5之外，已经能够转译ES7与JSX，但这样的行为与名字并不符合，有人会说这些不是该`6to5`做的事情。

于是，**Babel**诞生了。

Babel 一词是向《银河系漫游指南》里的 [巴别鱼（BabelFish）](http://en.wikipedia.org/wiki/List_of_races_and_species_in_The_Hitchhiker%27s_Guide_to_the_Galaxy#Babel_fish)致敬，它是一个能帮助人类理解任何语言的虚构物种（巴别鱼则来自于 [巴别塔（Babel Tower）](http://en.wikipedia.org/wiki/Tower_of_Babel)的故事）。Babel的故事自此开始，它不再仅仅是一个工具，它成为了一个工具链平台——提供了转译下一代JS的各种工具，并允许开发者参与进来开发的平台。

[6to5 JavaScript Transpiler Changes Name to Babel]: https://www.infoq.com/news/2015/02/babel-new-name-for-6to5

### 版本里程碑

由`6to5`重命名为`Babel`前，`6to5`已经走过了三个版本，所以重命名后的Babel从版本4.0开始。根据文章「Not Born to Die」提到，有以下几个里程碑

* 5.0.0 引入了`stage`，创建了`plugin system`来支持自定义转译
* 6.0.0 模块化，拆分了几个核心包，引入了`opt-in functionality`(这是啥？)与`presets`和`plugin options`的概念
* 6.13.0 支持`Preset Options`

等等。

### Babel 7.x

在18年八月末，Babel发布了7.0版本。在发布时重申了自己的角色——让开发者无视用户浏览器的差异性，能够用新的JS语法及特性进行开发。

除了性能方面的提升以外，增加了对typescript的支持，对安装包使用‘@babel’的命名空间，增加了`babel.config.js`等等。



[Not Born to Die]: https://babeljs.io/blog/2015/02/15/not-born-to-die
[The State of Babel]: https://babeljs.io/blog/2016/12/07/the-state-of-babel

[6to5 JavaScript Transpiler Changes Name to Babel]: https://www.infoq.com/news/2015/02/babel-new-name-for-6to5