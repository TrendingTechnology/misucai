---
title: "如果您使用Hamburger Menus进行智能手机导航，请尝试使用Sausage Links"
path: "Hamburger-Menus-ausage-Links"
date: "2019-01-17"
coverImage: "https://res.cloudinary.com/diqqalzsx/image/upload/v1562058709/content/uploads/sausagelink.gif"
author: "Frank"
excerpt: '在移动网页设计中常常会使用菜单导航，很长一段时间以来一直是使用Hamburger Menus。这不一定是坏事，如今，还有一个更简单的替代方案，就是Sausage Links。'
tags: ["rob____ot", "hello friend"]
---

在移动网页设计中常常会使用菜单导航，很长一段时间以来一直是使用Hamburger Menus。这不一定是坏事，如今，还有一个更简单的替代方案，就是Sausage Links。

![](https://res.cloudinary.com/diqqalzsx/image/upload/v1562058709/content/uploads/sausagelink.gif)

在我们深入了解Sausage Links概念的细节（以及一个简单的演示）之前，让我们快速浏览一下汉堡包菜单的优缺点。

## Hamburger Menus

[Hamburger Menus](https://codepen.io/search/pens?q=hamburger%20menu&page=1&order=popularity&depth=everything)的概念无论如何都不_可怕_，事实上它确实从视觉角度解决了很多问题。不幸的是，这并不意味着它存在没有一些恼人的缺陷。

### 优点

* 最小化菜单所需的可视空间量
* 现在相当普遍的是，很多用户都了解它的功能
* 通过在移动设备上收集所有物品，使设计师的生活变得更轻松

### 缺点

* 需要额外的测试/工作以确保菜单与屏幕阅读器和仅限键盘的用户一起使用
* 可以通过儿童下拉元素，帮助文本等的存在变得过于复杂。
* 向可能需要额外的JavaScript来呈现这些菜单的项目添加膨胀（仅CSS的汉堡包菜单可以避免此问题）
* 添加用户的额外交互点（单击以打开，然后继续阅读可用选项）

如您所见，上面列出的缺点并不是_那么_糟糕。在最终用户的UX旅程中，我认为它们更像是一个小小的坑。Hamburger Menus的很大一部分工作完全正常，应该保持原样。但是，那些滥用或滥用Hamburger概念的异常值应该引入Sausage Links。

## Sausage Links

我首先应该提到这个概念远非**新的**概念。有许多网站已经以某种形式实现此菜单类型。这篇文章的重点不是要用一些从未想过的新导航设计来打击你的思想。我只是想提高对另一个可用菜单概念的认识。

足够的闲聊，让我们来看看Sausage Links的运作情况：

<iframe height="565" style="width: 100%;" scrolling="no" title="Scrolling Navigation (Sausage Links)" src="//codepen.io/bradleytaunt/embed/preview/QXjjbE/?height=265&theme-id=0&default-tab=result" frameborder="no" allowtransparency="true" allowfullscreen="true">

See the Pen <a href='[https://codepen.io/bradleytaunt/pen/QXjjbE/](https://codepen.io/bradleytaunt/pen/QXjjbE/ "https://codepen.io/bradleytaunt/pen/QXjjbE/")'>Scrolling Navigation (Sausage Links)</a> by Bradley Taunt

(<a href='[https://codepen.io/bradleytaunt](https://codepen.io/bradleytaunt "https://codepen.io/bradleytaunt")'>@bradleytaunt</a>) on <a href='[https://codepen.io](https://codepen.io "https://codepen.io")'>CodePen</a>.

</iframe>

上面的CodePen添加了大量的视觉设计绒毛，所以让我们来看看完成这个菜单所需的最低HTML和CSS：

    <nav class="sausage-links">
        <ul>
            <li><a href="">Homepage</a></li>
            <li><a href="">Categories</a></li>
            <li><a href="">Filter Properties</a></li>
            <li><a href="">Edit Optional Tags</a></li>
            <li><a href="">Research Papers</a></li>
            <li><a href="">Contact Our Team</a></li>
        </ul>
    </nav>

    /* Sausage Links Nav Container */
    .sausage-links {
        position: relative;
    }
    
    /* The left and right "faded" pseudo elements */
    .sausage-links:before, .sausage-links:after {
        content: '';
        height: calc(100% - 2em);
        pointer-events: none;
        position: absolute;
        top: 1em;
        width: 10px;
        z-index: 2;
    }
    .sausage-links:before {
        background: linear-gradient(to right, rgba(255,255,255,0) 0%, white 100%);
        right: 0;
    }
    .sausage-links:after {
        background: linear-gradient(to left, rgba(255,255,255,0) 0%, white 100%);
        left: 0;
    }
    
    /* Basic flexbox to prevent items from breaking lines */
    .sausage-links ul {
        display: flex;
        flex-wrap: nowrap;
        overflow: auto;
        -webkit-overflow-scrolling: touch;
    }
    
    .sausage-links ul li {
        white-space: nowrap;
    }
    
    .sausage-links ul li a, .sausage-links ul li a:visited {
        display: inline-block;
    }

很简单，嗯？

### 优点

* 需要极少量的CSS
* 屏幕阅读器/键盘保险箱
* 需要零JavaScript
* `radio`切换父容器等不需要hacky隐藏输入。
* 用户无需任何交互即可查看前几个可用选项

### 缺点

* 可能看起来对某些项目设计看起来最具吸引力（在某些情况下难看的滚动条）
* 与大型站点地图相比，更适合中小型菜单列表
* 如果没有适当的淡入淡出/切断视觉提示，用户可能无法理解他们可以滚动

## 那么，应该使用Hamburger Menus还是Sausage Links？

这真的取决于你的项目或整体移动设计（我知道，这是一个有用的答案）。我确信甚至有一些用例，在基于切换的汉堡包菜单中有香肠链接是有意义的。菜单的可能性可能是无止境的！

而已。我希望我能激励你在不久的将来尝试Sausage Links，或者至少让你更深入地思考移动导航设计！
