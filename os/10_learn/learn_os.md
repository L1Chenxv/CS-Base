# 11.1 操作系统怎么学？

操作系统真的可以说是 `Super Man`，它为了我们做了非常厉害的事情，以至于我们根本察觉不到，只有通过学习它，我们才能深刻体会到它的精妙之处，甚至会被计算机科学家设计思想所震撼，有些思想实际上也是可以应用于我们工作开发中。

操作系统比较重要的四大模块，分别是[内存管理](https://mp.weixin.qq.com/s/HJB_ATQFNqG82YBCRr97CA)、[进程管理](https://mp.weixin.qq.com/s/YXl6WZVzRKCfxzerJWyfrg)、[文件系统管理](https://mp.weixin.qq.com/s/qJdoXTv_XS_4ts9YuzMNIw)、[输入输出设备管理](https://mp.weixin.qq.com/s/04BkLtnPBmmx6CtdQPXiRA)。这是我学习操作系统的顺序，也是我推荐给大家的学习顺序，因为内存管理不仅是最重要、最难的模块，也是和其他模块关联性最大的模块，先把它搞定，后续的模块学起来我认为会相对轻松一些。  

学习的过程中，你可能会遇到很多「虚拟」的概念，比如虚拟内存、虚拟文件系统，实际上它们的本质上都是一样的，都是**向下屏蔽差异，向上提供统一的东西**，以方便我们程序员使用。

还有，你也遇到各种各样的[调度算法](https://mp.weixin.qq.com/s/JWj6_BF9Xc84kQcyx6Nf_g)，在这里你可以看到数据结构与算法的魅力，重要的是我们要理解为什么要提出那么多调度算法，你当然可以说是为了更快更有效率，但是因什么问题而因此引入新算法的这个过程，更是我们重点学习的地方。

你也会开始明白进程与线程最大的区别在于上下文切换过程中，**线程不用切换虚拟内存**，因为同一个进程内的线程都是共享虚拟内存空间的，线程就单这一点不用切换，就相比进程上下文切换的性能开销减少了很多。由于虚拟内存与物理内存的映射关系需要查询页表，页表的查询是很慢的过程，因此会把常用的地址映射关系缓存在 TLB 里的，这样便可以提高页表的查询速度，如果发生了进程切换，那 TLB 缓存的地址映射关系就会失效，缓存失效就意味着命中率降低，于是虚拟地址转为物理地址这一过程就会很慢。


你也开始不会傻傻的认为 read 或 write 之后数据就直接写到硬盘了，更不会觉得多次操作 read 或 write 方法性能会很低，因为你发现操作系统会有个「**磁盘高速缓冲区**」，它已经帮我们做了缓存的工作，它会预读数据、缓存最近访问的数据，以及使用 I/O 调度算法来合并和排队磁盘调度 I/O，这些都是为了减少操作系统对磁盘的访问频率。

……

还有太多太多了，我在这里就不赘述了，剩下的就交给你们在学习操作系统的途中去探索和发现了。


还有一点需要注意，学操作系统的时候，不要误以为它是在说 Linux 操作系统，这也是我初学的时候犯的一个错误，操作系统是集合大多数操作系统实现的思想，跟实际具体实现的 Linux 操作系统多少都会有点差别，如果要想 Linux 操作系统的具体实现方式，可以选择看 Linux 内核相关的资料，但是在这之前你先掌握了操作系统的基本知识，这样学起来才能事半功倍。




## 入门系列

对于没学过操作系统的小白，我建议学的时候，不要直接闷头看书。相信我，你不用几分钟就会打退堂鼓，然后就把厚厚的书拿去垫显示器了，从此再无后续，毕竟直接看书太特喵的枯燥了，当然不如用来垫显示器玩游戏来着香。

B 站关于操作系统课程资源很多，我在里面也看了不同老师讲的课程，觉得比较好的入门级课程是《**操作系统 - 清华大学**》，该课程由清华大学老师向勇和陈渝授课，虽然我们上不了清华大学，但是至少我们可以在网上选择听清华大学的课嘛。课程授课的顺序，就如我前面推荐的学习顺序：「内存管理 -> 进程管理 -> 文件系统管理 -> 输入输出设备管理」。

![《操作系统 - 清华大学》](https://cdn.jsdelivr.net/gh/xiaolincoder/ImageHost2/%E5%85%B6%E4%BB%96/%E6%93%8D%E4%BD%9C%E7%B3%BB%E7%BB%9F-%E6%B8%85%E5%8D%8E%E5%A4%A7%E5%AD%A6.png)

> B 站清华大学操作系统视频地址：https://www.bilibili.com/video/BV1js411b7vg?from=search&seid=2361361014547524697

该清华大学的视频教学搭配的书应该是《**现代操作系统**》，你可以视频和书籍两者结合一起学，比如看完视频的内存管理，然后就看书上对应的章节，这样相比直接啃书相对会比较好。


![《现代操作系统》](https://cdn.jsdelivr.net/gh/xiaolincoder/ImageHost2/%E5%85%B6%E4%BB%96/%E7%8E%B0%E4%BB%A3%E6%93%8D%E4%BD%9C%E7%B3%BB%E7%BB%9F.png)

清华大学的操作系统视频课讲的比较精炼，涉及到的内容没有那么细，《**操作系统 - 哈工大**》李治军老师授课的视频课程相对就会比较细节，老师会用 Linux 内核代码的角度带你进一步理解操作系统，也会用生活小例子帮助你理解。

![《操作系统 - 哈工大》](https://cdn.jsdelivr.net/gh/xiaolincoder/ImageHost2/%E5%85%B6%E4%BB%96/%E6%93%8D%E4%BD%9C%E7%B3%BB%E7%BB%9F-%E5%93%88%E5%B7%A5%E5%A4%A7.png)

> B 站哈工大操作系统视频地址：https://www.bilibili.com/video/BV1d4411v7u7?from=search&seid=2361361014547524697


## 深入学习系列

《现代操作系统》这本书我感觉缺少比较多细节，说的还是比较笼统，而且书也好无聊。

推荐一个说的更细的操作系统书 —— 《**操作系统导论**》，这本书不仅告诉你 What，还会告诉你 How，书的内容都是循序渐进，层层递进的，阅读起来还是觉得挺有意思的，这本书的内存管理和并发这两个部分说的很棒，这本书的中文版本我也没找到资源，不过微信读书可以免费看这本书。

![《操作系统导论》](https://cdn.jsdelivr.net/gh/xiaolincoder/ImageHost2/%E5%85%B6%E4%BB%96/%E6%93%8D%E4%BD%9C%E7%B3%BB%E7%BB%9F%E5%AF%BC%E8%AE%BA.png)

当然，少不了这本被称为神书的《**深入理解计算机系统**》，豆瓣评分高达 `9.8` 分，这本书严格来说不算操作系统书，它是以程序员视角理解计算机系统，不只是涉及到操作系统，还涉及到了计算机组成、C 语言、汇编语言等知识，是一本综合性比较强的书。

![《深入理解计算机系统》](https://cdn.jsdelivr.net/gh/xiaolincoder/ImageHost2/%E5%85%B6%E4%BB%96/%E6%B7%B1%E5%85%A5%E7%90%86%E8%A7%A3%E8%AE%A1%E7%AE%97%E6%9C%BA%E7%B3%BB%E7%BB%9F.jpg)

它告诉我们计算机是如何设计和工作的，操作系统有哪些重点，它们的作用又是什么，这本书的目标其实便是要讲清楚原理，但并不会把某个话题挖掘地过于深入，过于细节。看看这本书后，我们就可以对计算机系统各组件的工作方式有了理性的认识。在一定程度上，其实它是在锻炼一种思维方式 —— 计算思维。


----

## 最后

文中推荐的书，小林都已经把电子书整理好给大家了，只需要在小林的公众号后台回复「**我要学习**」，即可获取百度网盘下载链接。

![](https://cdn.jsdelivr.net/gh/xiaolincoder/ImageHost2/%E5%85%B6%E4%BB%96/%E5%85%AC%E4%BC%97%E5%8F%B7%E4%BB%8B%E7%BB%8D.png)