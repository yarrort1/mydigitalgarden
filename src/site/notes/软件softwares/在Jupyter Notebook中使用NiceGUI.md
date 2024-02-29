---
{"dg-publish":true,"permalink":"/软件softwares/在Jupyter Notebook中使用NiceGUI/"}
---

# 在Jupyter Notebook中使用NiceGUI

原创 IT磨刀石 IT磨刀石 _2023-09-06 21:41_ _发表于江苏_

收录于合集


在NiceGUI的官网上，Features部分里，有这么一句话"Jupyter notebook compatibility"，表明NiceGUI应该是可以在Jupyter notebook中运行使用的，此外就没有第二句有关的内容介绍或说明了。

![图片](https://mmbiz.qpic.cn/sz_mmbiz_png/8lNyS5yTWfZNUQmYECCntalHISP37LFAr9oTzyMd3nrW9exZalTibM1MVicsiafQASCkLUQ9Ie9roKCwib2jEK1qSA/640?wx_fmt=png&wxfrom=13)

而本人极少使用Jupyter notebook来编辑和运行python代码，因此缺少对上述NiceGUI的特性的关注。既然官网没有过多的介绍，按理应该是没有多大的问题，按照正常的写法不就可以在Jupyter notebook中跑起来了吗？直到有朋友留言问：如何在Jupyter notebook中使用NiceGUI?我才意识到，我是想当然了。于是我便开始了在Jupyter notebook中使用NiceGUI的体验之旅！

先按照正常的用法写，果不其然报错了！【RuntimeError: asyncio.run() cannot be called from a running event loop】

![图片](https://mmbiz.qpic.cn/sz_mmbiz_png/8lNyS5yTWfZNUQmYECCntalHISP37LFAzjttMNJuAj1yBLESX0UXWmvicWhmmlwI46hqmSqmtW291IUNCBvuAcQ/640?wx_fmt=png&wxfrom=5&wx_lazy=1&wx_co=1)

从报错的内容来看，显然NiceGUI是用到了asyncio模块。什么是asyncio？简单地说，它是python里用于实现异步IO，处理事件并发的包。其核心概念有事件循环和协程。asyncio以事件循环（event loop）为中心，定义协程函数。当事件触发时，执行协程函数。想要了解asyncio更多更详细的内容，可以自行查阅一些资料，这里列出部分参考文章的地址。  

> https://www.liaoxuefeng.com/wiki/1016959663602400/1017970488768640

> https://www.cnblogs.com/Red-Sun/p/16934843.html

> https://zhuanlan.zhihu.com/p/59671241

那为什么会在Jupyter notebook中报这个错呢？这说明Jupyter notebook已经创建了一个事件循环，而NiceGUI内部再调用asyncio.run()方法，这意味着会在现有运行中的事件循环里再创建一个新的事件循环，并且要在新的事件循环中运行协程函数，这就造成了事件循环的冲突！

那么如何解决这个问题呢？我先查看了NiceGUI的源码，在globals.py文件里看到loop字段，是Optional[asyncio.AbstractEventLoop]类型，默认值为None。似乎我们可以在这里做文章，我的思路是将Jupyter notebook的事件循环传递给NiceGUI，这样NiceGUI在内部会拿globals.loop进行判断。让我们来试一下！

```
from nicegui import ui,globals
```

![图片](https://mmbiz.qpic.cn/sz_mmbiz_png/8lNyS5yTWfZNUQmYECCntalHISP37LFAbm3tKIaS6b9rmsNIJZX0CdlNYQfCk5n3CQtUv1ibNUoBcnic2Rhib1BEQ/640?wx_fmt=png&wxfrom=5&wx_lazy=1&wx_co=1)

代码顺利地运行了，而且会打开新的浏览器标签页显示输出的内容！我建议在Jupyter notebook里使用@ui.page来绘制界面，至于为什么，等大家试一下不这么写看会是什么样的效果！由于在Jupyter notebook里无法自动地加载新的变化，因此需要先interrupt the kernel，然后再执行cell里的代码！