[参考地址](http://www.jianshu.com/p/872f8fb425ce)

1. html5有哪些新特性、移除了那些元素？如何处理HTML5新标签的浏览器兼容问题？如何区分 ?

```
***新增了以下的几大类元素***
内容元素，article、footer、header、nav、section。
表单控件，calendar、date、time、email、url、search。
控件元素，webworker, websockt, Geolocation。
***移出的元素有下列这些****
显现层元素：basefont，big，center，font, s，strike，tt，u。
性能较差元素：frame，frameset，noframes。
HTML5已形成了最终的标准，概括来讲，它主要是关于图像，位置，存储，多任务等功能的增加。
新增的元素有绘画 canvas ，用于媒介回放的 video 和 audio 元素，本地离线存储 localStorage 长期存储数据，浏览器关闭后数据不丢失，而sessionStorage的数据在浏览器关闭后自动删除，此外，还新增了以下的几大类元素。
内容元素，article、footer、header、nav、section。
表单控件，calendar、date、time、email、url、search。
控件元素，webworker, websockt, Geolocation。
***新的技术***
canvas,svg,webworker, websocket, Geolocation.....
```

2.简述一下你对HTML语义化的理解。

```
（1）HTML语义化让页面的内容结构化，结构更清晰，便于对浏览器、搜索引擎解析；
（2）即使在没有样式CSS的情况下也能以一种文档格式显示，并且是容易阅读的；
（3）搜索引擎的爬虫也依赖于HTML标记来确定上下文和各个关键字的权重，有利于SEO；
（4）使阅读源代码的人更容易将网站分块，便于阅读、维护和理解。
```

3.HTML5的离线存储怎么使用？能否解释一下工作原理？

    在用户没有连接英特网时，可以正常访问站点和应用；在用户连接英特网时，更新用户机器上的缓存文件。
    `原理`：HTML5的离线存储是基于一个新建的 `.appcache` 文件的缓存机制（并非存储技术），通过这个文件上的解析清单离线存储资源，这些资源就会像cookie一样被存储下来。之后当网络处于离线状态下时，浏览器会通过被离线存储的数据进行页面展示。HTML5的离线存储怎么使用？能否解释一下工作原理？



